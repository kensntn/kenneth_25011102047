# CAT3 — Four-Mode LED Pattern Generator Using Push-Button Control

**EXP:** CAT3

**DATE:** Not specified

**NAME OF EXP:** Four-Mode LED Pattern Generator Using Push-Button Control

**HARDWARE SETUP / PLATFORM:**
- Microcontroller: AT89S52
- Architecture: 8051
- IDE: Keil µVision
- Clock configuration in Keil project: 33 MHz
- LEDs: Four LEDs controlled through Port 1 (P1.0–P1.3)
- Push-button: Connected to P2.6 (active LOW)

**TASK NO:**
- Configure four LEDs as digital outputs.
- Read a push-button input using GPIO.
- Generate four different LED patterns.
- Implement software debouncing for reliable button detection.
- Change the LED operating mode with each valid button press.

**CIRCUIT DIAGRAM:**

<img width="1671" height="941" alt="CAT3 Four-Mode LED Pattern Generator" src="https://github.com/user-attachments/assets/5481648c-a74f-484a-af9b-7469eff5735f" />


**CORE LOGIC / PSEUDOCODE / CODE BASE:**

**1. GPIO Configuration**
- P1.0–P1.3 are used to control the four LEDs.
- P2.6 is configured as the active-LOW push-button input.
- P2.3 is set LOW in the initialization section.

**2. Button Detection**
- Continuously check the P2.6 input.
- When the button is pressed, introduce a 20 ms delay for debouncing.
- Confirm the button state and wait for its release.
- Register one mode change for each valid press.

**3. LED Operating Modes**

- **Mode 1 — Running LED:** LEDs turn ON sequentially from P1.0 to P1.3.
- **Mode 2 — Binary Counter:** Displays binary values from 0000 to 1111.
- **Mode 3 — Alternating Pattern:** Alternates between 0101 and 1010.
- **Mode 4 — All LED Flash:** All four LEDs turn ON and OFF together.

**4. Mode Switching**
- The system starts in Mode 1.
- Each valid button press advances to the next mode.
- After Mode 4, the sequence returns to Mode 1.

**INFERENCE:**

The experiment demonstrates GPIO-based LED control using the AT89S52 microcontroller. Four LED patterns are generated using software-controlled delays, while a push-button with software debouncing is used to switch between operating modes.
