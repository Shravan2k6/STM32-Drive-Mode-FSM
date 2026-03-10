**Project: Multi-State Logic & Automotive Drive Mode Emulation**

**Development Toolchain**

**Hardware:** STM32F446RE (ARM Cortex-M4)  
**Language:** C (HAL Framework)  
**Key Peripherals:** TIM2 (PWM Mode), ADC1 (12-bit), UART2 (Asynchronous)  
**Software:** 

* **Hardware Configuration:** **STM32CubeMX**. Used for visual pinout mapping.  
* **IDE:** **STM32CubeIDE (Eclipse-based)**. Used for C-language development.  
* **Terminal Emulator:** **PuTTY**.

### **Objective**

To design a robust control logic system that simulates an automotive "Drive Mode" selector. The goal was to implement a stable **Finite State Machine (FSM)** that transitions between four distinct operational profiles based on user input, with visual feedback provided via modulated LED patterns.

### **State Machine Architecture**

The system was engineered with four discrete operational states, each with unique timing and telemetry profiles:

* **Mode 0: Engine OFF** – System idle; all actuators (LEDs) deactivated.  
* **Mode 1: ECO** – Low-frequency visual feedback (Slow Single LED Blink); optimized for power-saving simulation.   
* **Mode 2: SPORT** – High-frequency visual feedback (Fast Dual LED Alternate Blink); simulating high-performance responsiveness.  
* **Mode 3: RACE** – Maximum frequency visual feedback(Extremely Fast Triple LED Sequential Blink); simulating peak performance and low-latency output.

### **Technical Implemetation**

**Interrupt-Driven Input:** Implemented a logic gate to detect mode transitions via the onboard Blue User Button / External Switch, ensuring clean state switching without "bounce" or erratic behavior.

**Timing Control:** Used non-blocking `HAL_GetTick()` logic to manage LED flash rates. This ensured that the UART telemetry remained "live" even while the LEDs were in their "off" cycle of a blink.

**Serial Integration:** Integrated USART2 to broadcast the current "Drive Mode" to a terminal (PuTTY), simulating a vehicle’s dashboard display.

### **Learnt**

1. **Logical Scalability:** The ability to manage multiple "If-Else" or "Switch-Case" conditions without crashing the program.  
2. **User Experience (UX) Design:** Translating abstract code into meaningful visual indicators that a human user can understand immediately.  
3. **Code Organization:** Structuring a main loop to handle state-specific tasks efficiently

### **Results**

The firmware successfully emulated a seamless transition between driving profiles. The use of UART debugging confirmed that the state transitions were instantaneous and that the timing intervals for each mode remained precise within ±1ms.

**Personal Takeaway:**

*"This project was my first deep dive into Finite State Machines (FSM). I learned that complex system behavior is best managed by breaking it into discrete, predictable states. It taught me how to maintain code scalability—ensuring that adding a new 'Mode' doesn't break the existing logic, a core principle in automotive ECU programming."*

**Developed by:** Shravan Shyampuriya

