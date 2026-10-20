> note:- you just need to compete tasks and [Meshmerize_PS.pdf](https://github.com/the-robotronics-club/Project-X-Selection-Tasks/blob/dad5236d8f27beb7fc49fb64453f889b1e6ad99e/Line-Maze-Solver/Meshmerize_PS.pdf) is just to give you an idea of what competition actually is. 
# LMS Learning Resources

## Task 1 — Basic Coding: Centroid Estimation & Motor Clamping

### Core Technical Concepts

- **Weighted centroid formula:**
  $$\text{Position} = \frac{\sum_{i=0}^{N-1} (w_i \times v_i)}{\sum_{i=0}^{N-1} v_i}$$
  Where $w_i \in [-2, -1, 0, 1, 2]$ and $v_i$ is the calibrated reflectance reading.
- **Division-by-zero protection:** When all sensors read zero (the robot left the line completely), the denominator is zero. The function must detect this before division and return a sentinel value or the last valid position.
- **Clamping with sign preservation:** Limiting motor commands to a maximum magnitude while maintaining their positive or negative direction.

### Recommended Resources

1. **Pololu 3pi Robot User's Guide — Section 7.c: Advanced Line Following with 3pi (PID Control)**
   - Link: [Pololu 3pi Documentation](https://www.pololu.com/docs/0J21/7.c)
   - Type: Technical Documentation / Tutorial
   - Why it is recommended: Pololu wrote the reference implementation for multi-sensor centroid calculation used in competitive robotics. Section 7.c details how individual sensor readings convert into a position variable, how edge sensors represent extrema, and how the algorithm avoids division errors.

2. **Pololu QTR Sensors Arduino Library Source Code**
   - Link: [GitHub - pololu/qtr-sensors-arduino](https://github.com/pololu/qtr-sensors-arduino)
   - Type: Open-Source C++ Library
   - File to inspect: `QTRSensors.cpp` (specifically the `readLinePrivate` method)
   - Why it is recommended: Over 400 stars on GitHub. It demonstrates the exact accumulation loop, calibration normalization (0–1000 scale), and memory of the last known position when all sensors lose reflection.

3. **Unity Test Framework for Embedded C**
   - Link: [ThrowTheSwitch - Unity](http://www.throwtheswitch.org/unity)
   - Type: Testing Framework & Guide
   - Why it is recommended: The industry standard for unit-testing embedded C/C++ without hardware. Shows how to pass edge cases (all zeroes, maximum saturation, alternating readings) through mathematical functions and verify outputs using assertion macros.

---

## Task 2 — Datasheet Literacy: Active Components & Electrical Limits

### Core Technical Concepts

- **Absolute Maximum Ratings vs Recommended Operating Conditions:** Exceeding absolute maximums causes silicon breakdown or thermal destruction. Circuit designs must remain within recommended limits under worst-case ambient temperatures.
- **Darlington BJT vs Power MOSFET output stages:**
  - L298N: Bipolar Darlington transistors drop 1.8V to 3.2V across internal silicon, converting input power into heat.
  - TB6612FNG: Low-resistance MOSFETs ($R_{\text{DS(on)}} \approx 0.5\,\Omega$) drop roughly 0.5V at 1A.
- **Thermal dissipation calculation:**
  $$P_{\text{loss}} = V_{\text{drop}} \times I_{\text{load}}$$
  $$T_{\text{junction}} = T_{\text{ambient}} + (P_{\text{loss}} \times R_{\theta\text{JA}})$$

### Recommended Resources

1. **How to Read a Datasheet — SparkFun Electronics**
   - Link: [SparkFun Learn: How to Read a Datasheet](https://learn.sparkfun.com/tutorials/how-to-read-a-datasheet)
   - Type: Practical Written Guide
   - Why it is recommended: Explains how to extract pinouts, current ratings, voltage thresholds, truth tables, and timing diagrams without getting lost in manufacturing codes.

2. **EEVacademy Digital Design Part 4: Digital Logic Datasheets Explained — Dave Jones**
   - Link: [EEVblog YouTube Channel](https://www.youtube.com/watch?v=sO5A_c_j1mY)
   - Type: Video Tutorial (~30 mins)
   - Community Reception: High praise in engineering forums for showing real-world reading habits: jumping to absolute ratings, input/output voltage levels ($V_{\text{IH}}, V_{\text{IL}}, V_{\text{OH}}, V_{\text{OL}}$), and thermal charts.

3. **STMicroelectronics L298 Dual Full-Bridge Driver Datasheet**
   - Link: [ST L298 Datasheet PDF](https://www.st.com/resource/en/datasheet/l298.pdf)
   - Type: Component Datasheet
   - Key Sections to Study: Table 6 (Electrical Characteristics), specifically $V_{\text{CE(sat)}}$ (total drop up to 3.2V at 1A), logic input voltage levels, and Figure 6 (BJT switching circuit).

4. **Toshiba TB6612FNG Dual DC Motor Driver Datasheet**
   - Link: [Toshiba TB6612FNG Datasheet PDF](https://toshiba.semicon-storage.com/info/TB6612FNG_datasheet_en_20141001.pdf)
   - Type: Component Datasheet
   - Key Sections to Study: Absolute Maximum Ratings ($V_M = 15\,\text{V}$, $I_{\text{out}} = 1.2\,\text{A}$ average, $3.2\,\text{A}$ pulse), Power Dissipation versus Ambient Temperature graphs, and the `STBY` (Standby) pin logic.

---

## Task 3 — PID Control: Line Following & Loop Tuning

### Core Technical Concepts

- **Proportional ($K_p$):** Produces a correction proportional to current lateral offset. High $K_p$ decreases rise time but introduces hunting/oscillation.
- **Derivative ($K_d$):** Responds to the rate of error change ($\Delta\text{error} / \Delta t$). Acts as a damper on overshoot, especially when entering tight curves.
- **Integral ($K_i$):** Accumulates historical error over time to eliminate steady-state offset (e.g., motor asymmetry or track tilt). Usually set very low or omitted entirely in line followers to prevent oscillation and integral windup.
- **Sampling jitter:** Inconsistent loop times warp the derivative term ($\Delta e / \Delta t$) and destabilize the steering response. Fixed-rate execution via non-blocking timers is required.

### Recommended Resources

1. **Understanding PID Control — Brian Douglas (MATLAB Tech Talks)**
   - Link: [MATLAB YouTube Playlist: Understanding PID Control](https://www.youtube.com/playlist?list=PLn8PRpmsu08pQBgjxYFXSsODEF3Jqmm-y)
   - Type: 7-Part Video Series (Brian Douglas / MathWorks)
   - Community Reception: Widely considered the clearest visual and intuitive explanation of PID on YouTube. Comments consistently praise the physical analogies and the explanation of anti-windup and derivative filtering.
   - Essential Episodes:
     - *Part 1: What is PID Control?*
     - *Part 2: Expanding Beyond a Pendulum (P, PI, PD trade-offs)*
     - *Part 6: Manual Tuning and Ziegler-Nichols*

2. **Improving the Beginner's PID — Brett Beauregard**
   - Link: [Brett Beauregard Project Blog](http://brettbeauregard.com/blog/2011/04/improving-the-beginners-pid-introduction/)
   - Type: Technical Deep-Dive Series (Written)
   - Why it is recommended: Written by the author of the standard Arduino PID library. Breaks down practical problems in discrete MCU code:
     - Why sample time must be fixed and explicit.
     - Derivative kick: why differentiating measurement instead of error prevents violent jumps on setpoint changes.
     - Reset windup: clamping integrator state when actuator limits are hit.

3. **Advance PID Line Follower Tutorial — Arnab Kumar Das**
   - Link: [Advance PID Line Follower on YouTube](https://www.youtube.com/watch?v=2n55k8wFjX8)
   - Type: Practical Implementation Video
   - Community Reception: Thousands of active comments from robotics students. Focuses specifically on sensor weighting, tuning $K_p$ first until slight oscillation begins, then adding $K_d$ to damp out wobble on straight tracks.

---

## Task 4 — BOM Preparation: Component Selection under ₹10,000

### Core Technical Concepts

- **Motor matching:** BO motors (cheap plastic gearboxes, high backlash, uneven speeds) versus N20 micro metal gearmotors (precise brass gears, 300–600 RPM at 6V/12V, 3mm D-shaft) versus coreless competition motors.
- **Motor driver matching:** Continuous driver current must exceed the combined running current of both motors, with thermal headroom for stall current spikes.
- **Voltage matching:** Sensor output rails (3.3V vs 5V) must match ESP32 ADC pin limits without exceeding 3.3V.

### Recommended Resources

1. **TB6612FNG H-Bridge Motor Controller — Better than L298N? — DroneBot Workshop**
   - Link: [DroneBot Workshop TB6612FNG Video](https://www.youtube.com/watch?v=di_GkF_GqO4) / [Accompanying Article](https://dronebotworkshop.com/tb6612fng-h-bridge/)
   - Type: Video & Written Tutorial
   - Why it is recommended: Directly evaluates the L298N against modern MOSFET alternatives. Explains why older Darlington drivers waste battery power, shows wiring diagrams, and measures real voltage drops.

2. **Pololu Micro Metal Gearmotor Selection Guide**
   - Link: [Pololu Micro Metal Gearmotors](https://www.pololu.com/category/60/micro-metal-gearmotors)
   - Type: Manufacturer Specifications Table
   - Why it is recommended: Comprehensive datasheets listing gear ratios (30:1, 50:1, 100:1), no-load RPM, stall torque, stall current, and shaft dimensions. Used as the benchmark across student and professional robotics competitions.

3. **Indian Component Suppliers Directory**
   - [Robu.in](https://robu.in/) — Motors (N20, TT gearmotors), LiPo batteries, TB6612FNG breakouts, ESP32 boards, QTR reflectance arrays.
   - [ElectronicsComp.com](https://www.electronicscomp.com/) — Passive components, buck converters, connectors, perfboards.
   - [Robokits India](https://robokits.co.in/) — Chassis, wheels, brackets, high-discharge lithium packs.

---

## Task 5 — Power Budget & Battery Selection

### Core Technical Concepts

- **Current draw accounting:**
  - Idle: ESP32 (~80mA with Wi-Fi off, ~180–240mA during RF bursts), sensor array (~20–30mA), driver logic (~5mA).
  - Operating: Motor nominal running current (~150–250mA each).
  - Peak: Motor stall current (~800mA–1.5A each under aggressive direction reversal or wheel lock).
- **Runtime calculation:**
  $$\text{Runtime (hours)} = \frac{\text{Battery Capacity (Ah)}}{\text{Average Current Draw (A)}} \times \text{Derating Factor (0.7–0.8)}$$
- **C-rating requirement:**
  $$\text{Max Discharge Current (A)} = \text{Capacity (Ah)} \times C\text{-Rating}$$
- **Chemistry trade-offs:**
  - **LiPo (Lithium Polymer pouch):** High discharge rates (20C–40C+), low weight, thin form factor, but mechanically vulnerable to punctures.
  - **Li-ion (Cylindrical 18650):** Steel casing, high volumetric energy density, lower C-rating (typically 1C–3C for standard cells, up to 10C for high-drain cells like Sony VTC6), heavier.

### Recommended Resources

1. **Battery University — Isidor Buchmann**
   - Link: [Battery University Home](https://batteryuniversity.com/)
   - Key Articles:
     - [BU-205: Types of Lithium-ion](https://batteryuniversity.com/article/bu-205-types-of-lithium-ion)
     - [BU-402: What Is C-rate?](https://batteryuniversity.com/article/bu-402-what-is-c-rate)
     - [BU-501: Basics About Discharging](https://batteryuniversity.com/article/bu-501-basics-about-discharging)
   - Why it is recommended: The global reference for battery chemistry, internal resistance, discharge curves, and safety guidelines.

2. **ESP32 Battery Power and Brownout Troubleshooting — Andreas Spiess**
   - Link: [Andreas Spiess YouTube Channel](https://www.youtube.com/@AndreasSpiess) (Search: `#193 Comparison of 10 ESP32 Battery powered Boards` and `#387 Battery operated ESP32`)
   - Type: Practical Bench-Testing Videos
   - Community Reception: High credibility among embedded developers. Demonstrates real oscilloscope captures of millisecond current spikes and explains why weak battery voltage sag trips the ESP32 hardware brownout detector.

---

## Task 6 — Electronics & Hardware: Wiring, Grounding & Noise Suppression

### Core Technical Concepts

- **Common ground topology:** All power rails and sub-circuits must share a single reference ground. Without this, signal voltages between the ESP32 and motor driver float unpredictably. Star grounding isolates motor return current paths from sensitive MCU ground pins.
- **Motor inductive noise:** Brushed DC motors generate electrical arcs across their brushes. This induces high-frequency transients and back-EMF spikes that disrupt MCU logic.
- **Flyback protection:** Inductive loads require antiparallel diodes across H-bridge switches to absorb inductive kickback when PWM cuts off.
- **Decoupling capacitors:** Bulk electrolytic capacitors (100–470µF) near driver inputs absorb transient motor inrush current; 0.1µF ceramic capacitors near IC pins filter high-frequency noise.

### Recommended Resources

1. **Dealing with Motor Noise — Pololu Support**
   - Link: [Pololu Documentation: Dealing with Motor Noise](https://www.pololu.com/docs/0J15/9)
   - Type: Application Note
   - Why it is recommended: Clear, direct instructions on soldering three $0.1\,\mu\text{F}$ ceramic capacitors directly to DC motor terminals (one terminal-to-terminal, two terminal-to-case) and twisting power leads to minimize inductive coupling.

2. **EEVblog #859 — Bypass / Decoupling Capacitor Tutorial — Dave Jones**
   - Link: [EEVblog #859 on YouTube](https://www.youtube.com/watch?v=BcJ6UdDx1vg)
   - Type: Video (~35 mins)
   - Community Reception: Over 500,000 views. Explains the physics of Equivalent Series Resistance (ESR) and Equivalent Series Inductance (ESL), showing why bulk capacitors and ceramic bypass capacitors must work together in parallel.

3. **Troubleshooting Microcontroller Resets / Brownouts — SparkFun Tutorials**
   - Link: [SparkFun: Common Microcontroller Problems & Troubleshooting](https://learn.sparkfun.com/tutorials/troubleshooting-microcontroller-resets)
   - Type: Practical Diagnostic Guide
   - Why it is recommended: Step-by-step diagnostic order: verifying battery voltage under load with a multimeter, checking for voltage sag on the 3.3V rail using an oscilloscope, and diagnosing thermal shutdown on linear voltage regulators.

---

## Task 7 — Wireless Sensor Diagnostics: ESP32 Telemetry & Anomaly Detection

### Core Technical Concepts

- **Protocol selection on ESP32:**
  - **BLE (Bluetooth Low Energy):** Low power draw (~15–30mA peak bursts), short latency (7.5–15ms connection interval), direct pairing with smartphones and Web Bluetooth browsers.
  - **Wi-Fi (UDP/WebSockets):** Higher throughput, longer range, but higher power draw (~150–250mA continuous). UDP broadcast prevents transport-layer stalling if a packet is lost mid-run.
  - **Classic Bluetooth (SPP):** Easy serial emulation on Android/Windows, but incompatible with iOS and draws excessive battery current.
- **Distinguishing sensor hardware faults from line curves:**
  - *Spatial continuity:* A valid line transition causes adjacent sensors to sweep smoothly (e.g., S3 drops as S4 rises). A mechanical contact fault on a bump causes an abrupt drop to zero or rail-spike on a single pin while adjacent pins stay stable.
  - *Delta-rate thresholding:* High inter-sample delta ($|v_t - v_{t-1}| > \text{threshold}$) on a single channel over high-frequency intervals indicates intermittent contact.

### Recommended Resources

1. **Serial Studio — Open-Source Telemetry Dashboard**
   - Link: [GitHub - Serial-Studio/Serial-Studio](https://github.com/Serial-Studio/Serial-Studio)
   - Type: Cross-Platform Telemetry GUI (5,000+ stars)
   - Why it is recommended: Connects directly via BLE, Wi-Fi UDP/TCP, or UART. Automatically plots multiple analog sensor curves in real time, displays bar graphs, and logs incoming data to CSV for anomaly analysis.

2. **ESP32 Web Server using WebSockets — Random Nerd Tutorials**
   - Link: [Random Nerd Tutorials ESP32 WebSocket Server](https://randomnerdtutorials.com/esp32-websocket-server-arduino/)
   - Type: Practical Step-by-Step Guide
   - Why it is recommended: The benchmark tutorial for streaming sensor readings from an ESP32 to a browser interface with minimal overhead.

3. **ESP32 BLE Server and Client Tutorial — Random Nerd Tutorials**
   - Link: [Random Nerd Tutorials ESP32 BLE Server](https://randomnerdtutorials.com/esp32-ble-server-client/)
   - Type: Implementation Guide
   - Why it is recommended: Shows how to create custom BLE characteristics to notify connected mobile apps or PC dashboards without maintaining an active Wi-Fi router.

---

## Task 8 — Maze-Solving Algorithms: Left-Hand Rule, DFS & Path Simplification

### Core Technical Concepts

- **Wall-preference rules (Left-Hand / Right-Hand Rule):** Works on simple mazes (simply connected mazes without loops or isolated islands). At every intersection:
  1. Turn left if possible.
  2. Else go straight if possible.
  3. Else turn right if possible.
  4. Else turn around (180° back).
- **Path reduction (dead-end elimination):** Every time the robot hits a dead end, it turns around (`B`). The combination of entering a dead end, turning back, and exiting can be simplified into a single turn:
  - $L + B + R \rightarrow S$ (Left, Back, Right simplifies to Straight)
  - $L + B + S \rightarrow R$
  - $L + B + L \rightarrow S$
  - $S + B + L \rightarrow R$
  - $S + B + S \rightarrow B$
  - $R + B + L \rightarrow B$
- **DFS / Trémaux's algorithm vs Wall-following:** For mazes with closed loops or floating islands, wall-following gets trapped in infinite circles. DFS models junctions as nodes and paths as edges, keeping a visited table to guarantee exhaustive exploration.

### Recommended Resources

1. **Pololu 3pi Robot User's Guide — Section 8: Maze Solving**
   - Link: [Pololu 3pi Maze Solving Guide](https://www.pololu.com/docs/0J21/8.a)
   - Subsections to read:
     - *8.a: Solving a Line Maze*
     - *8.c: Left-Hand-on-the-Wall*
     - *8.d: Recording the Path*
     - *8.e: Simplifying the Solution*
     - *8.f: The Complete Maze-Solving Code*
   - Why it is recommended: The definitive open source tutorial explaining junction detection, the algebraic string replacement algorithm for turn simplification, and the transition from exploration to replay run.

2. **Autonomous Maze-Solving Robot — Instructables**
   - Link: [Instructables: Autonomous Maze-Solving Robot](https://www.instructables.com/Autonomous-Maze-Solving-Robot/)
   - Type: Step-by-Step Project Guide
   - Community Reception: Millions of views across STEM robotics competitions. Contains clear diagrams illustrating junction identification (crossings, T-junctions, right-angle turns) and turn-array compression.

3. **Micromouse Online — Peter Harrison**
   - Link: [Micromouse Online Blog](https://micromouseonline.com/)
   - Type: Engineering Blog & Algorithm Tutorials
   - Why it is recommended: Run by world champion robotics engineer Peter Harrison. Explains the transition from simple line-maze heuristics to formal graph search (Flood-Fill, Dijkstra, and turn-penalty weightings).

---

## Task 9 — LMS Implementation Challenge: Firmware Pipeline

### Core Technical Concepts

- **Sensor min-max calibration:** Read surface reflection over black and white areas at startup. Normalize raw 12-bit ADC readings ($0–4095$) into a uniform scale ($0–1000$).
- **Deterministic control loop:** Run the sensor read, PID calculation, and motor updates inside a fixed time window using `millis()` or `micros()` rather than blocking `delay()` calls.
- **Differential steering mixing:**
  $$\text{Left Speed} = \text{Base Speed} + \text{PID Output}$$
  $$\text{Right Speed} = \text{Base Speed} - \text{PID Output}$$
- **Lost-line recovery state machine:** When all sensors read white, determine recovery action based on the last known error sign:
  - If last error was positive, pivot right until center sensor detects black.
  - If last error was negative, pivot left until center sensor detects black.
  - If no line is found after a configurable timeout (e.g., 500ms), halt both motors safely.

### Recommended Resources & Reference Repositories

1. **ESP-32-Line-Follower by amjed-ali-k**
   - Link: [GitHub - amjed-ali-k/ESP-32-Line-Follower](https://github.com/amjed-ali-k/ESP-32-Line-Follower)
   - Type: Complete Arduino/ESP32 Repository
   - Key Features: Demonstrates reflectance array calibration, PID calculation, and motor speed clamping tailored to the ESP32 platform.

2. **DC Motor Speed & Position Control — Curio Res**
   - Link: [Curio Res YouTube Channel](https://www.youtube.com/@curiores)
   - Videos: [DC Motor PID Speed Control](https://www.youtube.com/watch?v=Xx0Tt-g_uUA) and [Position Control with Encoders](https://www.youtube.com/watch?v=dTGITLnYAY0)
   - Community Reception: High-production animations explaining PID error computation, motor PWM conversion, and handling deadbands. Useful if implementing the optional encoder speed-control extension.

3. **ESP32 Arduino Core LEDC Peripheral Reference**
   - Link: [Espressif Arduino ESP32 LEDC API](https://docs.espressif.com/projects/arduino-esp32/en/latest/api/ledc.html)
   - Type: Official Documentation
   - Why it is recommended: Explains hardware PWM channels, timer resolutions, and frequency configuration on ESP32 GPIOs for motor driver inputs.

---

## Quick Reference: Resource Summary

| Task | Primary Documentation / Reference | Recommended Video / Visual Guide | Code Reference |
| :--- | :--- | :--- | :--- |
| **1 — Basic Coding** | [Pololu 3pi Guide (7.c)](https://www.pololu.com/docs/0J21/7.c) | ThrowTheSwitch Unity Unit Testing Guide | [pololu/qtr-sensors-arduino](https://github.com/pololu/qtr-sensors-arduino) |
| **2 — Datasheet Literacy** | [SparkFun Reading Datasheets](https://learn.sparkfun.com/tutorials/how-to-read-a-datasheet) | [EEVacademy: Logic Datasheets](https://www.youtube.com/watch?v=sO5A_c_j1mY) | [ST L298](https://www.st.com/resource/en/datasheet/l298.pdf) / [Toshiba TB6612](https://toshiba.semicon-storage.com/info/TB6612FNG_datasheet_en_20141001.pdf) |
| **3 — PID Control** | [Beauregard: Beginner's PID](http://brettbeauregard.com/blog/2011/04/improving-the-beginners-pid-introduction/) | [Brian Douglas: MATLAB Tech Talks](https://www.youtube.com/playlist?list=PLn8PRpmsu08pQBgjxYFXSsODEF3Jqmm-y) | [Arnab Kumar Das Line Follower](https://www.youtube.com/watch?v=2n55k8wFjX8) |
| **4 — BOM Preparation** | [Pololu Micro Metal Specs](https://www.pololu.com/category/60/micro-metal-gearmotors) | [DroneBot Workshop: TB6612FNG](https://www.youtube.com/watch?v=di_GkF_GqO4) | Robu.in / ElectronicsComp parts list |
| **5 — Power Budget** | [Battery University (BU-205, BU-402)](https://batteryuniversity.com/) | [Andreas Spiess: ESP32 Power & Brownouts](https://www.youtube.com/@AndreasSpiess) | Power calculation spreadsheet / math |
| **6 — Electronics & Wiring** | [Pololu: Dealing with Motor Noise](https://www.pololu.com/docs/0J15/9) | [EEVblog #859: Decoupling Capacitors](https://www.youtube.com/watch?v=BcJ6UdDx1vg) | [SparkFun Reset Troubleshooting](https://learn.sparkfun.com/tutorials/troubleshooting-microcontroller-resets) |
| **7 — Wireless Diagnostics** | [Random Nerd Tutorials ESP32 Comms](https://randomnerdtutorials.com/) | [Serial Studio Visualizer Walkthrough](https://github.com/Serial-Studio/Serial-Studio) | [Serial-Studio/Serial-Studio](https://github.com/Serial-Studio/Serial-Studio) |
| **8 — Maze Algorithms** | [Pololu 3pi Maze Guide (8.a–8.f)](https://www.pololu.com/docs/0J21/8.a) | [Instructables Maze Solver Guide](https://www.instructables.com/Autonomous-Maze-Solving-Robot/) | [Peter Harrison: Micromouse Online](https://micromouseonline.com/) |
| **9 — LMS Implementation** | [Espressif LEDC PWM API](https://docs.espressif.com/projects/arduino-esp32/en/latest/api/ledc.html) | [Curio Res Motor Control](https://www.youtube.com/@curiores) | [amjed-ali-k/ESP-32-Line-Follower](https://github.com/amjed-ali-k/ESP-32-Line-Follower) |
