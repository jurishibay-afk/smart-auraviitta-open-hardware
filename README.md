Älyviitta (Smart Auraviitta) — Open Hardware Road Safety Infrastructure

> **Pohjoinen Aloite (Northern Initiative)**  
> *Dedicated to Finland, Sweden, Norway, and All Northern Lands • 2026*  
> **Author & Concept Creator:** Roman Kemov  
> **License:** Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)

[![Älyviitta Moose Scene](poster.png)](video.mp4)

---

## 📌 Executive Summary

**Älyviitta (Smart Auraviitta)** is an open-source, modular, solar-powered roadside beacon mesh network designed for early warning of wildlife (moose, reindeer) presence on northern highways, thus eliminating collisions (**Hirvikolari / Vision Zero**).

By replacing passive plastic snow-plow markers (*Auraviitta*) with intelligent 6-section modular beacons equipped with thermal sensors (Grid-EYE), Sub-GHz mesh radios, and a 360° CIGS solar sleeve, Älyviitta creates a dynamic, self-diagnosing safety corridor for drivers, drastically reducing accidents and related costs.

---

## 🛠️ 6-Section Modular Design & Hardware (v1.0 Specification)

The beacon is a robust cylinder (25mm diameter, 1.2–1.5m length) engineered for extreme northern conditions, featuring toolless assembly via **Flush Threading** and **Concentric Contact Flanges**.

1.  **Section 1 (Anchor):** High-density composite ground anchor socket, designed for frozen ground installation.
2.  **Section 2 (Flex-Joint):** Monolithic polyurethane flexible joint. Allows the beacon to bend upon impact (e.g., from *Lumiauto* snow-plows) and instantly return to vertical.
3.  **Section 3 (Battery Core):** Reinforced red body housing a 1m low-temperature **LiFePO4** battery (-40°C), acting as a structural core for enhanced rigidity.
4.  **Section 4 (MCU Module):** Sealed red module containing the main microcontroller (MCU) and 868 MHz Mesh radio.
5.  **Section 5 (LED Dome):** Transparent polycarbonate dome with dual-sided, high-brightness RGB LED arrays (Green/Red).
6.  **Section 6 (Solar Cap / Master Top):** Blue cap with a 360° flexible **CIGS** solar sleeve.
    *   *Master Version:* This section integrates a flush-mounted **Grid-EYE** (8x8 thermal matrix) for wildlife detection and an **NB-IoT/LTE-M** cellular module.

**Inter-Section Connectivity:** Sections feature **Flush Threading** (15–30 turns) with silicone **O-Rings (IP68)** and spring-loaded **Pogo Pins** for toolless, wireless power/data transfer upon assembly.

---

## 📡 Network Topology & Intelligent Operation

*   **Mesh Network:** SLAVE beacons (every 20m) relay signals. MASTER beacons (every 100m, i.e., every 5th pole) perform environmental sensing.
*   **Zero Blind Spots:** Master beacons' 120° FOV sensors have a 50% overlap, ensuring full coverage even if one sensor fails.
*   **Smart Thermal Management:** Includes passive breather vents, internal silica gel, and active **Smart Pulse Heating** (ITO film on optics, activated by sensor data for 5-10s every 5-10min) for condensation/ice prevention. **The exact configuration will be finalized during field tests.**

### Operation Modes:
*   **Green Safety Corridor (Night/Twilight):** All beacons continuously glow soft green, defining the road's edge.
*   **Pulsing Red Alarm (Wildlife Threat):** Upon detecting wildlife (filtered by mass >100kg, height >1.2m), MASTER beacons instantly trigger a **1Hz pulsing red alarm** in a 200m radius, warning drivers.
*   **Daytime Passive Monitoring:** LEDs off to conserve power; sensors remain active 24/7. **Red alarm activates only upon detecting an immediate threat.**

---

## 📊 Telemetry & Autonomy

*   **Heartbeat Telemetry (NB-IoT):** Daily 12:00 status report from MASTER beacons to road authorities (*Väylävirasto / Destia*) via NB-IoT (battery level & LED health), enabling predictive maintenance.
*   **Autonomous Power (Optional Off-Grid Kit):** For remote locations, solar panels on a separate console above the beacon, a vertical wind generator, and an integrated UPS with LiFePO4 batteries are optionally installed. Base units use standard grid power.
*   **Autonomy:** Calculated **45–60 days** of continuous operation during *Kaamos* (polar night) without direct sunlight. **The final autonomy will be confirmed via field tests.**

---

## 💰 Cost Efficiency

*   **Production Cost (per unit, series):** SLAVE ~€20.00 | MASTER ~€41.00.
*   **Infrastructure Cost:** **~€2,210 per 1 km** of highway (100 poles) vs. **€30,000–€50,000/km** for traditional moose-fences.

---

*Open for international engineering collaboration, university research, and municipal road safety pilots. The Älyviitta project aims to set a new standard for road safety in northern regions, leveraging open-source principles for rapid adoption and widespread impact.*
