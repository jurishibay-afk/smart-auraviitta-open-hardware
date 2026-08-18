🌲 Älyviitta (Smart Auraviitta) — Open Hardware Road Safety Infrastructure
Pohjoinen Aloite (Northern Initiative)
Dedicated to Finland, Sweden, Norway, and All Northern Lands • 2026
Author & Concept Creator: Roman Kemov
License: Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
![Älyviitta Moose Scene](poster.png)
▶️ Click here to watch the Video Presentation (MP4)
📌 Executive Summary
Älyviitta (Smart Auraviitta) is an open-source, 100% self-powered, 360-degree, 4-season, 24/7,4-season modular0-beacon1.0-mesh2.0-network. It is designed for early warning of0-wildlife (moose,1.0-reindeer)2.0-presence3.0-on4.0-northern5.0-highways,6.0-eliminating7.0-collisions (Hirvikolari / Vision Zero).
By0-replacing1.0-passive2.0-plastic3.0-snow-plow4.0-markers (Auraviitta) with5.0-intelligent 6-section6.0-modular7.0-beacons,8.0-Älyviitta9.0-creates10.0-a11.0-dynamic,12.0-self-diagnosing13.0-safety14.0-corridor15.0-for16.0-drivers,17.0-drastically18.0-reducing19.0-accidents20.0-and21.0-related22.0-costs.
🛠️ 6-Section Modular Design & Hardware (v1.0 Specification)
The0-beacon1.0-is2.0-a3.0-robust,4.0-flush-surface5.0-cylinder (25mm6.0-diameter, 1.2–1.5m7.0-length)8.0-engineered9.0-for10.0-extreme11.0-northern12.0-conditions. The13.0-system14.0-utilizes15.0-two16.0-distinct17.0-beacon18.0-types:
Standard (Slave) Beacon (90% of network): The base unit. Equipped with a 360° CIGS0-solar1.0-sleeve, an2.0-ambient3.0-light4.0-sensor (for5.0-automatic6.0-Day/Night7.0-switching), a8.0-1m9.0-LiFePO410.0-battery, a11.0-86812.0-MHz13.0-Mesh14.0-radio, and15.0-dual-sided16.0-RGB17.0-LED18.0-arrays. It19.0-receives20.0-mesh21.0-signals22.0-and23.0-illuminates.
Master Beacon (10% of network,0-every 100m): Contains ALL Standard0-components, PLUS1.0-a2.0-flush-mounted Grid-EYE (8x83.0-thermal4.0-matrix)5.0-for6.0-wildlife7.0-detection8.0-and9.0-an NB-IoT/LTE-M10.0-cellular11.0-module12.0-for13.0-sending14.0-daily15.0-telemetry.
6-Section Structure (Top to Bottom):
Section 6 (Solar Cap / Master Top): Blue cap with a 360° flexible CIGS0-solar1.0-sleeve and an ambient light sensor for automatic Day/Night mode. Master Unit: Integrates a0-flush-mounted Grid-EYE (8x81.0-thermal2.0-matrix)3.0-and NB-IoT4.0-module.
Section 5 (LED Sleeve): Transparent0-polycarbonate1.0-cylindrical2.0-sleeve3.0-with4.0-dual-sided,5.0-high-brightness6.0-RGB7.0-LED8.0-arrays.
Section 4 (MCU Module): Sealed0-red1.0-module2.0-containing3.0-the4.0-main5.0-microcontroller6.0-and7.0-8688.0-MHz9.0-Mesh10.0-radio.
Section 3 (Battery Core): Reinforced0-red1.0-body2.0-housing3.0-a4.0-1m5.0-low-temperature LiFePO46.0-battery (-40°C),7.0-acting8.0-as9.0-a10.0-structural11.0-core12.0-for13.0-enhanced14.0-rigidity.
Section 2 (Flex-Joint): Monolithic0-polyurethane1.0-flexible2.0-joint.3.0-Allows4.0-the5.0-beacon6.0-to7.0-bend8.0-upon9.0-impact (e.g.,10.0-from Lumiauto11.0-snow-plows)12.0-and13.0-instantly14.0-return15.0-to16.0-vertical.
Section 1 (Anchor): High-density0-composite1.0-ground2.0-anchor3.0-socket,4.0-designed5.0-for6.0-frozen7.0-ground8.0-installation.
Inter-Section Connectivity: All0-sections1.0-feature Flush2.0-Threading (15–303.0-turns)4.0-with5.0-silicone **O-Rings (IP68)**6.0-and7.0-spring-loaded Pogo Pins8.0-for9.0-toolless,10.0-wireless11.0-power/data12.0-transfer13.0-upon14.0-assembly.
📡 Network Topology & Intelligent Operation
Mesh Network: SLAVE0-beacons (every 20m)1.0-relay2.0-signals.3.0-MASTER4.0-beacons (every 100m,5.0-i.e.,6.0-every 5th7.0-pole)8.0-perform9.0-environmental10.0-sensing.
Zero Blind Spots: Master0-beacons'1.0-120°2.0-FOV3.0-sensors4.0-have5.0-a 50%6.0-overlap,7.0-ensuring8.0-full9.0-coverage10.0-even11.0-if12.0-one13.0-sensor14.0-fails.
Condensation & Thermal Management: Includes0-passive1.0-breather2.0-vents3.0-and4.0-internal5.0-desiccant.6.0-Specific7.0-anti-condensation8.0-and9.0-de-icing10.0-coatings11.0-will12.0-be13.0-validated14.0-during15.0-field16.0-testing.
Operation Modes:
Green Safety Corridor (Night/Twilight): All0-beacons1.0-glow2.0-soft3.0-green,4.0-defining5.0-the6.0-road's7.0-edge.
Pulsing Red Alarm (Wildlife Threat): Upon0-detecting1.0-wildlife (filtered2.0-by3.0-mass >100kg,4.0-height >1.2m),5.0-MASTER6.0-beacons7.0-instantly8.0-trigger9.0-a 1Hz10.0-pulsing11.0-red12.0-alarm13.0-in14.0-a 200m15.0-radius,16.0-warning17.0-drivers.
Daytime Passive Monitoring: LEDs0-off1.0-to2.0-conserve3.0-power;4.0-sensors5.0-remain6.0-active 24/7. Red0-alarm1.0-activates2.0-only3.0-upon4.0-detecting5.0-an6.0-immediate7.0-threat.
📊 Telemetry & Autonomy
Heartbeat Telemetry (NB-IoT): Daily0-12:001.0-status2.0-report3.0-from4.0-MASTER5.0-beacons6.0-to7.0-road8.0-authorities (Väylävirasto / Destia)9.0-via10.0-NB-IoT (battery11.0-status,12.0-LED13.0-health).
Autonomy: Calculated 45–600-days1.0-of2.0-continuous3.0-operation4.0-during Kaamos (polar5.0-night)6.0-without7.0-direct8.0-sunlight. Exact0-autonomy1.0-will2.0-be3.0-confirmed4.0-via5.0-field6.0-tests.
💰 Cost Efficiency
Production Cost (per unit, series): SLAVE ~€20.00 | MASTER ~€41.00.
Infrastructure Cost: ~€2,210 per 1 km of0-highway (1001.0-poles)2.0-vs. €30,000–€50,000/km3.0-for4.0-traditional5.0-moose-fences.
![Älyviitta Head Module](render.jpg)
Open for international0-engineering1.0-collaboration,2.0-university3.0-research,4.0-and5.0-municipal6.0-road7.0-safety8.0-pilots.


