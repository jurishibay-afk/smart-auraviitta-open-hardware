🌲 Älyviitta (Smart Auraviitta) — Open Hardware Road Safety Infrastructure
Pohjoinen Aloite (Northern Initiative)
Dedicated to Finland, Sweden, Norway, and All Northern Lands • 2026
Author & Concept Creator: Roman Kemov
License: Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
![Älyviitta Moose Scene](poster.png)
▶️ Click here to watch the Video Presentation (MP4)
📌 Executive Summary
Älyviitta (Smart Auraviitta) is an open-source, 100% self-powered, 4-season, 24/7, 6-section modular beacon mesh network. It is designed for early warning of wildlife (moose, reindeer) presence on rural highways, preventing collisions (Hirvikolari / Vision Zero).
By replacing passive plastic snow-plow markers (Auraviitta) with intelligent 6-section modular beacons equipped with thermal sensors (Grid-EYE), Sub-GHz mesh radios, and a 360° CIGS solar sleeve, Älyviitta creates a dynamic, self-diagnosing safety corridor for drivers, drastically reducing accidents and related costs.
1. Installation Scheme & Network Topology (Mesh)
The system is installed on the roadside (right-of-way) on both sides of the road and consists of two types of devices:
Standard (Slave) Beacon (90% of the network):
Installation Spacing: Every 20 meters.
Function: Receives radio alarm signals and illuminates instantly.
Master Beacon (MASTER) (10% of the network):
Installation Spacing: Every 100 meters (every 5th beacon).
Function: Equipped with a thermal sensing unit to detect animals in the forest.
50% Sector Overlap (Zero Blind Spots)
Each MASTER beacon is equipped with an infrared sensor with a 120° field of view (FOV) directed towards the forest edge. The 100-meter installation distance and 120° FOV are calculated so that the "electronic eyes" of adjacent MASTER beacons overlap by 50%. This eliminates blind spots and guarantees 100% redundancy in case of a single sensor failure.
2. 6-Section Modular Architecture (Flush Thread)
The beacon is a thin, smooth cylinder with a diameter of 25 mm and a length of 1.2–1.5 m. All elements are connected via internal threading (flush / Flush Thread) with a long pitch (15–30 turns), making the body smooth on the outside and highly durable.
Modular Sections (Top to Bottom):
Section 6 (CIGS Solar Cap / SOLAR CAP): Blue plastic top. A flexible 360° CIGS solar film is wrapped around it, collecting diffuse light from any azimuth.
Master Beacon: This section integrates a flush-mounted Grid-EYE infrared thermal imager (8x8 matrix) and an NB-IoT / LTE-M cellular chip.
Section 5 (Optical Sleeve / LED SLEEVE): Transparent polycarbonate cylindrical sleeve. Inside, directional dual-sided RGB LED arrays (green and red light) are installed.
Section 4 (Electronic Brain / MCU & RADIO): Red sealed plastic compartment. Contains the control board (microcontroller) and a Sub-GHz (868 MHz in EU) radio chip for creating a Mesh network.
Section 3 (Battery Compartment / BATTERY CORE): Red plastic tube. Contains a 1-meter long, cold-resistant LiFePO4 cylindrical battery (down to -40°C), which serves as the internal spine (core) for the beacon's rigidity.
Section 2 (Flexible Insert / FLEX-JOINT): Monolithic elastic polyurethane damper-hinge. It allows the beacon to deflect by 45–90° upon impact from a wave of wet snow from a snow-plow (Lumiauto) and instantly return to its original vertical position.
Section 1 (Tip / ANCHOR): Pointed, high-strength polymer stake (replaceable socket), driven into frozen ground.
Wireless Internal Connection (Pogo Pins)
Inside the threaded ends between Sections 6, 5, 4, and 3, concentric copper traces (contact rings) and spring-loaded Pogo Pins are installed. During assembly, the parts are simply screwed together by hand like a light bulb, and the circuit closes automatically. There are no hanging wires inside the beacon that could break or twist. Watertightness of the connections is ensured by silicone O-Rings (IP68).
3. INTELLIGENT OPERATING MODES (ENERGY SAVING)
🌙 Night and Twilight Mode:
No Animals Detected: All beacons along the road continuously emit a soft GREEN light, creating a "green safety corridor" for drivers and improving road visibility during blizzards and polar nights.
Moose Detected: The nearest MASTER beacon detects a thermal signature on the forest edge (filtering small animals by analyzing mass >100 kg and thermal signature height >1.2 m) and transmits an alarm signal via the Mesh radio channel. A chain of beacons within 200–500 meters around the detection zone switches to 1 Hz PULSING BRIGHT RED light.
☀️ Daytime Mode:
No Animals Detected: Green illumination is completely turned off to save energy. IR matrix sensors continue to monitor in micro-power mode 24/7.
Moose Detected: The system instantly activates a PULSING BRIGHT RED alarm strictly in the local zone (5 beacons to the right and 5 beacons to the left of the animal's entry epicenter – 200 meters radius), attracting the driver's attention on a sunny highway.
4. TELEMETRY & SELF-DIAGNOSTICS (Heartbeat Telemetry)
To eliminate manual system monitoring by Finnish road authorities (Väylävirasto / Destia), Älyviitta incorporates an automated self-diagnostic algorithm:
Daily Heartbeat Ping: Every day at exactly 12:00 PM, each MASTER beacon sends a short 1-millisecond radio query to its group of SLAVE beacons.
Data Collection: Each SLAVE beacon reports its health status within milliseconds (e.g., SLAVE_04: BATT=7% | LED_WARN – low battery charge, one LED burned out).
Dispatch Notification: The MASTER beacon aggregates the information and, via its integrated NB-IoT / LTE-M cellular modem, sends a concise digital report to the Road Authority cloud.
Targeted Maintenance: The operator at the control panel sees the exact coordinates on a map (e.g., "Road 81, km 14.2, Beacon #34 – Critical battery discharge"). A technician drives to the location with one spare section, screws it in within 30 seconds, and leaves. Maintenance incurs zero unnecessary costs.
5. SURVIVAL PHYSICS IN NORTHERN CONDITIONS & FIELD TESTING
Polar Night (Kaamos): The vertically positioned 360° CIGS panel collects diffuse twilight even with a low sun angle. The LiFePO4 battery's reserve capacity is sufficient for 45–60 days of continuous autonomous operation in complete darkness without direct sunlight.
Ice and Snow Protection: The polycarbonate sleeve of Section 5 is treated with a hydrophobic lacquer to prevent ice buildup. Wet snow from snow-plows (Lumiauto) slides off the smooth, round surface due to gravity and natural micro-vibration of the beacon from passing truck winds.
Condensation Control: Despite integrated IP68 protection (silicone O-Rings) and breathable membranes for pressure equalization, the final configuration of the internal condensation control system (selection of desiccant types or need for micro-ventilation) will be determined by field climatic tests in conditions of sharp temperature drops from +5°C to -30°C.
Autonomy Validation: The stated autonomy of 45–60 days is a calculated estimate. The exact efficiency of diffuse light collection by CIGS panels during polar night (absence of direct sunlight) and the optimal LiFePO4 battery capacity will be confirmed during field tests beyond the Arctic Circle. This will guarantee 100% stable Mesh network operation during the darkest period of the year.
6. PROJECT ECONOMICS (BOM)
Production Cost (SLAVE Beacon, in series): ~€20.00
Production Cost (MASTER Beacon, in series): ~€41.00
Infrastructure Cost per 1 km of Road (100 beacons on both sides): ~€2,210
(For reference: Traditional metal/mesh moose fencing costs €30,000 – €50,000 per km).
Open for international engineering collaboration, university research, and municipal road safety pilots. The Älyviitta project aims to set a new standard for road safety in northern regions, leveraging open-source principles for rapid adoption and widespread impact.


