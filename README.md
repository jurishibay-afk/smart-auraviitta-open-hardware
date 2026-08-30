





# 🌲 Älyviitta (Smart Auraviitta) — Open Hardware Road Safety Infrastructure

**Pohjoinen Aloite (Northern Initiative)**
Dedicated to Finland, Sweden, Norway, and all Nordic lands • 2026

**Concept author and creator:** Roman Kemov
**License:** Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
![Älyviitta - Moose Warning System](poster.png)
---
https://github.com/user-attachments/assets/ae06a8ff-81d0-4d36-9819-ce5cb965f7af
## Technical Specification — Version 1.1

Älyviitta is an open-source concept for a distributed wireless mesh network of intelligent roadside beacons acting as an "active fence." It is designed to provide drivers with early warning of wildlife — moose and reindeer — entering the roadway on regional and national highways, reducing collision risk.

> **Changelog v1.0 → v1.1:** This revision incorporates five engineering corrections identified during an independent technical audit of v1.0, covering mechanical fastening, sensor claims, power budget, cold-weather battery behavior, and mesh latency. Several items below are stated as **design targets pending field/lab validation**, not as confirmed performance — see the Risk Mitigation table in Section 6.

---

## 1. Installation Layout and Mesh Topology

The system is installed along both sides of the road and consists of two device types.

**Standard slave beacons** make up 90% of the network, spaced at 20-meter intervals. Their core function is receiving mesh alert packets and instantly triggering visual indicators.

**Master beacons** make up 10% of the network, placed every 100 meters (every fifth pole). They carry thermal-imaging sensors to detect animals approaching from the treeline.

To eliminate blind spots, each master beacon has a thermal sensor with a 120° field of view aimed at the forest edge. The 100 m spacing gives adjacent master beacons roughly 50% overlap in detection coverage for redundancy.

To prevent orientation errors during field installation, each master beacon has a clearly visible directional marker, allowing road maintenance crews to quickly aim the thermal sensor at the treeline rather than the roadway.

A motion sensor supplements wildlife detection, and an ambient light sensor allows the system to switch smoothly between day and night modes.

---
https://github.com/user-attachments/assets/a9680daf-9bc8-4f93-8144-9c08eb91fc38
## 2. Six-Section Modular Architecture (Flush-Thread → Bayonet Revision)

Each beacon is a slim, smooth cylinder, 25 mm in diameter and 1.2–1.5 m long.

### 2.1 Mechanical Fastening — Bayonet Latch with Mechanical Detent Pin *(v1.1 revision)*

Section-to-section joints previously used flush internal threading. **This has been replaced with a bayonet-style latch incorporating a spring-loaded mechanical detent pin.** Sections are aligned, rotated a partial turn (~30–45°) to seat, and the detent pin snaps into a locking groove, preventing the joint from backing out under vibration (traffic-induced micro-vibration, plow strikes) or thermal cycling (-40 °C ↔ +25 °C). Assembly remains tool-free — push, twist, and the detent audibly/tactilely confirms lock. A visible witness mark on the collar indicates full engagement for installers.

Concentric copper contact rings and spring-loaded pogo pins remain the electrical interconnect between Sections 6, 5, 4, and 3, now seated against a positively-latched mechanical joint rather than relying on thread friction alone. IP68 sealing is retained via silicone O-rings at each bayonet collar.

*Caveat: the detent mechanism itself must be validated for repeated engage/disengage cycles at -40 °C, since detent springs and pin/socket tolerances are also subject to cold-embrittlement — this has not yet been bench-tested.*

- **Section 6 — Solar cap:** flexible CIGS solar shell, 360° rotating mount. Master beacons additionally integrate a Grid-EYE 8×8 thermal array, motion sensor, ambient light sensor, and an NB-IoT/LTE-M cellular chip.
- **Section 5 — Optical housing:** clear polycarbonate tube housing bidirectional RGB LED arrays (red/green), directional per side.
- **Section 4 — Electronics module:** sealed enclosure housing the main MCU and the 868 MHz sub-GHz mesh radio.
- **Section 3 — Battery module:** reinforced tube housing a 1-meter low-temperature LiFePO₄ battery pack rated for operation to -40 °C; also serves as the beacon's internal structural spine. See Section 3 for the revised thermal/power management strategy.
- **Section 2 — Flex joint:** now specified as **Arctic-Grade TPU/Silicone Hybrid, glass transition temperature ≤ -55 °C** *(v1.1 revision, replacing generic polyurethane)*. This material choice keeps the damper elastomeric well below the system's -40 °C operating floor, allowing the beacon to deflect 45–90° under plow contact (e.g., Lumiauto-type equipment) and spring back to vertical without embrittlement fracture.
- **Section 1 — Anchor:** pointed high-strength composite ground spike for direct driving into frozen soil.

*Caveat: TPU/silicone hybrid Tg of -55 °C is a materials datasheet target for the compound class; the specific formulation, wall thickness, and fatigue life under repeated plow-strike loading at -40 °C still require cyclic bend testing before this claim can be considered field-confirmed.*

### 2.2 Sensor Suite Clarification *(v1.1 revision)*

- **PIR motion sensor:** re-scoped as a **short-range local trigger only, effective to approximately 12–15 m**, consistent with real PIR/Fresnel-lens performance. It is no longer claimed to provide 100 m-radius coverage.
- **Grid-EYE 8×8 thermal array:** performs detection over the full 100 m master-beacon range via **thermal gradient dynamics** (spatial/temporal contrast against background, motion of the thermal blob across the 8×8 grid) rather than absolute mass/height measurement, which an 8×8 array cannot physically resolve.
- **Optional ToF/LiDAR module:** an add-on connector is provided for a Time-of-Flight or LiDAR ranging module, enabling distance-based size estimation for higher-confidence object classification (e.g., distinguishing a moose from a person or a sun-warmed boulder) in deployments where false-positive/false-negative rates need tightening beyond thermal-gradient-only detection.

*Caveat: without the ToF/LiDAR option populated, classification remains gradient-pattern based and should be described to stakeholders as "heat-signature detection," not verified species/size classification.*

### 2.3 Hardware Split — Master vs. Slave Beacon

**Slave beacon (standard node — 90% of network)**, optimized for ultra-low power and low BOM cost (~€20):
- MCU: low-power microcontroller (e.g., ESP32-C3 or STM32L series)
- Radio: 868 MHz sub-GHz transceiver for mesh routing
- Optics: bidirectional high-brightness RGB LED driver
- Power: integrated LiFePO₄ charge controller optimized for sub-zero operation
- Role: passive actuator — receives mesh commands, activates accordingly, no local heavy processing

**Master beacon (local hub — 10% of network)**, the "eyes and brain" of a 100 m segment (~€41 fully loaded):
- Main processor: higher-performance multicore MCU for real-time thermal data filtering and lightweight on-device logic
- Detection: Grid-EYE 8×8 thermal array (120° FOV, Poka-Yoke alignment marker) + short-range PIR + ambient light sensor + optional ToF/LiDAR
- Cellular telemetry: NB-IoT/LTE-M modem with eSIM, reporting status to a national traffic management platform (e.g., Digitraffic)
- Radio: 868 MHz sub-GHz mesh node
- Firmware: Dynamic Green Wave routing algorithm and daily Heartbeat self-diagnostic protocol

---

## 3. Power Architecture and Cold-Weather Energy Strategy *(v1.1 revision)*

**Adaptive Duty-Cycle Mode below -20 °C:** below this threshold, mesh-listen windows, heartbeat frequency, and non-critical telemetry reporting are automatically stretched (longer sleep intervals, reduced RX duty cycle) to offset the reduced usable capacity and higher internal resistance of the LiFePO₄ pack at extreme cold. Alarm-path responsiveness (animal-detection alert relay) is explicitly excluded from duty-cycle stretching and remains full-rate at all times.

**Supercomputers — supercapacitor buffering:** a supercapacitor stage is added in Section 4/3 to source the high pulse currents required by the 1 Hz RGB alarm driver and radio TX bursts, decoupling these transients from the LiFePO₄ cell itself. This addresses the failure mode where cold-degraded battery internal resistance causes voltage sag under pulsed load, which could otherwise trip BMS low-voltage protection at the exact moment an alarm needs to fire.

**Passive micro-heating of the LFP cell:** waste heat from the MCU (Section 4) and CIGS panel driver electronics (Section 6) is channeled via a thermally-conductive path into a thermally-insulated compartment around the battery pack, providing passive warming without a dedicated active heater circuit (i.e., no additional continuous power draw for heating).

*Caveat — this is the most important open item in the whole document: passive waste heat from a µA–mA-class MCU and a solar controller is a small, intermittent heat source. Whether it is sufficient to keep the LFP cell meaningfully above ambient during a multi-day -40 °C cold snap with no sun (polar night, no CIGS output to harvest waste heat from) has not been thermally modeled or bench-tested. This claim should be treated as a hypothesis to validate, not a solved problem, until supported by thermal simulation or an instrumented cold-chamber test. The originally-cited 45–60 day autonomy figure still requires a full state-by-state power budget (deep sleep / mesh-listen / mesh-relay / heartbeat / alarm, each in mA at -40 °C) before it can be considered verified rather than aspirational.*

---

## 4. Radio, Snow/Ice Resilience, and Directional Alarm Logic *(v1.1 revision)*

**Antenna icing protection:** the mesh radio antenna (Section 6) is treated with a superhydrophobic anti-icing coating to reduce rime-ice accumulation, which can otherwise detune the antenna and degrade mesh range precisely during the icing conditions the system targets.

**Snow-height clearance:** the optical section (Section 5) and antenna are positioned **1.2–1.5 m above grade**, intended to remain above typical roadside snowpack and plow windrows in target deployment regions.

*Caveat: 1.2–1.5 m is the beacon's total housing height, not a guaranteed clearance above snow — in northern Finland/Lapland, plow-thrown windrows regularly exceed 1–1.5 m along heavily-plowed shoulders. This figure should be confirmed against site-specific snow-load survey data per deployment corridor, not assumed uniformly sufficient.*

**Mesh alert latency target — priority protocol:** alert packets (animal detection, sector red/green state changes) are routed on a dedicated high-priority channel/slot ahead of routine heartbeat and telemetry traffic, with a **design target of <20 ms per hop** for alert-class packets.

*Caveat: this is a protocol design target, not a measured/confirmed figure. Actual per-hop latency depends on the specific sub-GHz radio's air-time, channel contention, and the mesh stack's arbitration scheme under real multi-hop, multi-collision-domain conditions. This number needs to be validated with instrumented field or bench testing across a realistic hop count (a moose crossing a two-lane road happens in 2–4 seconds — end-to-end sector-formation latency across the worst-case number of hops, not just the best-case single hop, is the number that actually matters and should be published once measured.)*

**Directional Threat Focus:** when a master beacon detects an animal, the alarm response is spatially directional rather than uniform:
- **Epicenter (red):** roughly 10 beacons at the point of incursion light solid red, on the side of the road the animal is approaching from only.
- **Lateral boundary (green):** roughly 20 beacons in each direction along the corridor light green, creating a sharp red/green visual contrast that instinctively directs driver attention to the exact threat location during braking, rather than diffusing attention across the whole corridor.
- **Dynamic tracking:** if the animal crosses the road into the opposite treeline, the mesh network re-computes and shifts the red epicenter / green boundary sectors in real time to follow the animal's trajectory.
- **Reset:** once the animal exits the detection radius back into forest, the sector reverts to deep-sleep standby.

---

## 5. Northern Survival Physics

During polar night (*kaamos*), the vertical 360° CIGS panel collects diffuse ambient light even at low solar elevation angles. The LiFePO₄ pack's rated capacity, combined with the Adaptive Duty-Cycle and passive micro-heating strategies in Section 3, is targeted to provide 45–60 days of continuous unattended operation in full darkness — **pending the full power-budget and cold-chamber validation noted in Section 3.**

The optical housing carries a hydrophobic coating so wet snow sheds under its own weight and traffic-induced micro-vibration. Final condensation-prevention strategy (beyond IP68 seals and breathable membranes) will be confirmed through field trials across +5 °C to -30 °C temperature swings.

---

## 6. Project Economics (BOM)

Estimated mass-production cost is approximately €20 per slave beacon and €41 per master beacon.

Total infrastructure cost for 1 km of highway, equipped with 100 beacons across both sides, is approximately **€2,210**.

For comparison, traditional metal or mesh moose-fencing typically costs **€30,000–€50,000 per km**.

### Risk Mitigation & Technical Caveats (v1.1)

| # | v1.0 Risk Identified | v1.1 Mitigation Adopted | Status |
|---|---|---|---|
| 1 | Threaded joints loosen under vibration/thermal cycling | Bayonet latch + mechanical detent pin | Design change made; detent cold-cycle fatigue **not yet bench-tested** |
| 1b | Polyurethane damper stiffens/embrittles near -40 °C | Arctic-grade TPU/silicone hybrid, Tg ≤ -55 °C | Material spec upgraded; **cyclic plow-strike fatigue test pending** |
| 2 | PIR claimed at 100 m (physically unrealistic) | PIR re-scoped to 12–15 m local trigger; Grid-EYE handles 100 m via thermal-gradient dynamics | Resolved on paper; **field false-positive/negative rate not yet measured** |
| 2b | Mass/height classification claimed from 8×8 thermal array (not physically possible) | Claim downgraded to gradient-pattern detection; optional ToF/LiDAR module for real classification | Resolved for base config; **classification accuracy only as good as optional module, if populated** |
| 3 | No published power budget; 45–60 day autonomy unverified | Adaptive Duty-Cycle <-20 °C, supercapacitor pulse buffering, passive MCU/CIGS waste-heat warming | Mitigations added; **full state-by-state power budget and cold-chamber runtime test still outstanding — highest-priority open item** |
| 4 | LFP voltage sag under pulsed alarm load at -40 °C could trip BMS cutoff | Supercapacitor stage isolates pulse loads from the cell | Architecturally sound; **needs bench validation under -40 °C pulsed load** |
| 4b | Sub-GHz mesh latency unknown for multi-hop alarm propagation | Priority alert channel, <20 ms/hop design target | Target only, **not yet measured end-to-end across realistic hop counts** |
| 4c | Antenna icing degrades mesh range in snow/rime conditions | Superhydrophobic anti-icing coating | Mitigation added; **effectiveness under real rime-ice accretion not field-tested** |
| 4d | Beacon height vs. real plow windrow height in Lapland | 1.2–1.5 m housing height specified | Partial; **site-specific snow-load survey still needed per corridor** |

---

## 7. Deployment Plan and Target Applications

**Primary use case — autumn wildlife activity:** collision risk rises during dark autumn months, particularly during moose rutting season and before stable snow cover forms. Älyviitta can provide active roadside warning in this window without exposure to snowplow equipment.

**Proposed Phase 1 pilot — Arctic snowmobile trails:** official snowmobile routes in Lapland could serve as a controlled environment for initial winter testing of cold-temperature operation, mesh reliability, battery performance, thermal detection, and visibility — without heavy road-construction equipment involved.

**Proposed Phase 2 — public roads:** deployment on regional and national highways should follow successful field validation, including dedicated tests of the flex joint, housing, optical section, and full system under snow/ice loading from plowing equipment — and completion of the outstanding validations listed in the Risk Mitigation table above.
#### Benchmark Comparison: ADDWS (Sweden, Road 108) vs. Älyviitta
* **Trafikverket ADDWS Pilot:** Proven highly effective (66% reduction in wildlife-vehicle collisions) using PTZ cameras, radars, and VMS signs. However, deployment cost was ~€300,000 for a single point-based fauna passage.
* **Älyviitta Positioning:** Designed as a complementary, highly scalable **linear coverage layer** for long un-fenced road corridors where point-based camera/radar setups are economically unviable.
---

Open for international engineering collaboration, university research, and municipal-level road-safety pilot projects.















































