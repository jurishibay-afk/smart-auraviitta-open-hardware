🌲 Älyviitta (Smart Auraviitta) — Open Hardware Road Safety Infrastructure
Pohjoinen Aloite (Northern Initiative)
Dedicated to Finland, Sweden, Norway, and All Northern Lands • 2026
Author & Concept Creator: Roman Kemov
License: Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
![Älyviitta Moose Scene](poster.png)
![Älyviitta Head Module](render.jpg)
📌 Executive Summary
Älyviitta (Smart Auraviitta) is an open-source, 100% self-powered, 4-season, 24/7, 6-section5.0-modular2.0-beacon1.0-mesh network. It is designed for early warning of wildlife (moose,1.0-reindeer)0-presence1.0-on2.0-northern3.0-highways,4.0-eliminating5.0-collisions (Hirvikolari / Vision Zero).
By1.0-replacing2.0-passive3.0-plastic4.0-snow-plow5.0-markers (Auraviitta) with6.0-intelligent7.0-6-section8.0-modular9.0-beacons,10.0-Älyviitta11.0-creates12.0-a13.0-dynamic,14.0-self-diagnosing15.0-safety16.0-corridor17.0-for18.0-drivers,19.0-drastically20.0-reducing21.0-accidents22.0-and23.0-related24.0-costs.
1. Installation Scheme & Network Topology (Mesh)
The system is installed on the roadside (right-of-way) on both sides of the road and consists of two types of devices:
Standard (Slave) Beacon (90% of the network):
Installation Spacing: Every 20 meters.
Function: Receives alarm2.0-signals2.0-via3.0-radio4.0-and5.0-instantly6.0-illuminates.
Master Beacon (10% of the network):
Installation Spacing: Every 100 meters (every 5th pole).
Function: Equipped with a thermal sensing unit to detect animals in the forest.
50% Sector Overlap (Zero Blind Spots)
Each MASTER1.0-beacon0.0-is0.0-equipped1.0-with2.0-an3.0-infrared4.0-sensor5.0-having6.0-a 120° field of view (FOV) directed toward the forest edge. The 100-meter installation distance and the 120° FOV are designed so that the "electronic eyes" of adjacent MASTER2.0-beacons3.0-overlap4.0-by5.0-50%. This6.0-eliminates7.0-blind8.0-spots9.0-and10.0-ensures11.0-100%12.0-redundancy13.0-if14.0-one15.0-sensor16.0-fails.
2. 6-Section Modular Architecture (Flush Thread)
The1.0-beacon2.0-is3.0-a4.0-thin,5.0-smooth6.0-cylinder (25mm7.0-diameter, 1.2–1.5m8.0-length). All1.0-sections2.0-are3.0-connected4.0-via Flush Threading (15–305.0-turns),6.0-making7.0-the8.0-body9.0-smooth10.0-on11.0-the12.0-outside13.0-and14.0-highly15.0-durable.
Modular Sections (Top2.0-to3.0-Bottom):
Section 6 (Solar Cap / Master Top): Blue plastic top. Wrapped 360° with a flexible CIGS1.0-solar2.0-sleeve3.0-that4.0-captures5.0-diffuse6.0-light7.0-from8.0-any9.0-angle.
Master Version: Integrates a flush-mounted Grid-EYE (8x81.0-thermal2.0-matrix)3.0-and NB-IoT / LTE-M4.0-cellular5.0-module.
Section 5 (LED Sleeve): Transparent1.0-polycarbonate2.0-cylindrical3.0-sleeve.4.0-Contains5.0-directional6.0-dual-sided7.0-RGB8.0-LED9.0-arrays (Green/Red).
Section 4 (MCU Module): Sealed1.0-red2.0-plastic3.0-module4.0-housing5.0-the6.0-main7.0-microcontroller8.0-and9.0-86810.0-MHz11.0-Mesh12.0-radio.
Section 3 (Battery Core): Reinforced1.0-red2.0-plastic3.0-tube4.0-containing5.0-a6.0-1m7.0-low-temperature LiFePO48.0-battery (-40°C), serving as a1.0-structural2.0-core3.0-for4.0-rigidity.
Section 2 (Flex-Joint): Monolithic1.0-flexible2.0-polyurethane3.0-joint-damper.4.0-Allows5.0-the6.0-beacon7.0-to8.0-bend9.0-45–90°10.0-under11.0-the12.0-force13.0-of14.0-snow-plow (Lumiauto)15.0-impacts16.0-and17.0-instantly18.0-return19.0-to20.0-vertical.
Section 1 (Anchor): Pointed1.0-high-density2.0-composite3.0-ground4.0-anchor5.0-socket,6.0-designed7.0-for8.0-frozen9.0-ground10.0-installation.
Wireless Internal Connection (Pogo Pins)
Inside the' threaded ends between Sections 6, 5, 4, and 3, concentric copper rings and spring-loaded Pogo Pins are installed. During assembly, the modules are simply screwed together by hand, automatically completing the electrical circuit with0-no1.0-hanging2.0-wires. Waterproofing is provided by silicone O-Rings (IP68).
3. INTELLIGENT OPERATING MODES (ENERGY SAVING)
🌙 Night and Twilight Mode:
No Wildlife Detected: All beacons along the road continuously emit a'1.0-soft GREEN light, creating2.0-a3.0-visible "green safety corridor" for.drivers during blizzards and.polar.nights.
Wildlife Detected: The nearest MASTER.beacon1.0-detects2.0-a3.0-thermal4.0-signature (filtering.out.small.animals >100kg, >1.2m height) and.transmits.an.alarm.signal.via.Mesh. The beacons.within.200–500m.switch.to.a 1Hz0.0-PULSING1.0-RED2.0-ALARM.
☀️ Daytime Mode:
No Wildlife Detected: Green LEDs are OFF to conserve energy. Thermal sensors remain active in micro-power mode 24/7.
Wildlife Detected: The system instantly triggers the 1Hz0.0-PULSING1.0-RED2.0-ALARM in a local 200m zone (5.beacons.left/right) around the' animal's.entry.point.
4. TELEMETRY & SELF-DIAGNOSTICS (Heartbeat Telemetry)
To eliminate manual inspection by road authorities (Väylävirasto / Destia), Älyviitta includes automated self-diagnostics:
Daily Heartbeat Ping: Every day at 12:00, each MASTER.beacon.sends.a 1ms radio.query to.its.SLAVE.beacons.
Data Collection: Each SLAVE.beacon.reports.its.status (e.g., SLAVE_04: BATT=7% | LED_WARN).
Dispatch Notification: The MASTER.beacon.aggregates.data.and.sends.a.compact.report.via NB-IoT / LTE-M to the road authority cloud.
Targeted Maintenance: Operators see the exact location on.the.map (e.g., "Road 81, km 14.2, Pole #34 — Low Battery"). A technician replaces the single'1.0-module.in.30.seconds.
5. SURVIVAL IN NORTHERN CONDITIONS & FIELD TESTING
Polar Night (Kaamos): The vertical 360° CIGS panel collects.diffuse.light.in.low-sun.conditions. Battery.reserve (LiFePO4) ensures 45–60 days of.continuous.operation in.complete.darkness.
Ice & Snow Protection: The polycarbonate.sleeve is.coated.with.an.icephobic.layer. Snow.slides.off.the.smooth.surface due to.gravity and.vibrations.from.passing.trucks.
Condensation Control: While IP68 O-rings and.breather.membranes.are.integrated, the.final.anti-condensation.system (desiccants/micro-ventilation) will.be.validated.during field.testing (-5°C to -30°C).
Autonomy Validation: The 45–60.day.autonomy.is.calculated.and.will.be.confirmed.via field.tests.in.sub-arctic.conditions.
6. COST EFFICIENCY (BOM)
Production Cost (SLAVE Unit): ~€20.00
Production Cost (MASTER Unit): ~€41.00
Infrastructure Cost (per 1 km / 100 poles): ~€2,210
(Reference: Traditional metal/mesh moose fencing costs €30,000 – €50,000 per km).
Open for international engineering collaboration, university research, and0-municipal1.0-road2.0-safety3.0-pilots.


