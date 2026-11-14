# CAT2 — 8051 Toolchain Setup and LED Interfacing

## EXP
CAT2

## DATE
20/07/2026

## NAME OF EXP
8051 Tool Chain Setup – Development Board – AT89S52

## HARDWARE SETUP / PLATFORM

| Component | Details |
|---|---|
| Microcontroller | AT89S52 |
| Architecture | 8051 |
| Development Environment | Keil µVision |
| Programming Language | Embedded C |
| Output Device | LED |
| GPIO Pin | P1.0 |
| Current-limiting resistor | 330 Ω (proposed circuit) |

## TASK NO

1. Hardware Board Bring-Up
2. Bare-Metal LED Blink
3. Custom Library Function for Delay Functionality

## CIRCUIT DIAGRAM

<img width="1672" height="941" alt="AT89S52 LED Blink Circuit Diagram" src="https://github.com/user-attachments/assets/dcbf64e2-fcf7-4884-84f6-3f7bb969ccfc" />


*The diagram represents a proposed active-high LED connection. The actual board wiring has not been independently verified.*

## CORE LOGIC / PSEUDOCODE / CODE BASE

### 1. Hardware Board Bring-Up
- Identify the AT89S52 microcontroller and development board.
- Identify the power supply and programming interface.
- Locate the GPIO pins and required peripherals.
- Verify the board's power and ground connections.

### 2. Bare-Metal LED Blink
- Configure P1.0 as the LED control output.
- Toggle the output continuously using direct bit-level access.
- Introduce a delay between successive state changes.

### 3. Custom Delay Function
- Define a reusable `delay_ms()` function.
- Use nested software loops to generate a time delay.
- Pass the required delay duration as a function argument.
- Call the function to maintain the LED blinking interval.

### IMPLEMENTATION

The program uses the `reg51.h` header and the `sbit` keyword to access P1.0 directly.

The LED state is toggled using:

```c
LED = ~LED;
```

A custom delay function is called with an argument of `500`, producing an approximate half-second delay according to the loop implementation and processor clock.

## INFERENCE

The experiment introduces the AT89S52 development environment and basic 8051 GPIO programming. A custom software delay function is used to control the blinking interval of an LED through port P1.0. It demonstrates direct register-level access and reusable delay implementation in Embedded C.

## PROJECT FILES

- `week2_l.c` — Embedded C source code
- `week2.uvproj` — Keil project configuration
- `STARTUP.A51` — Startup assembly file
- `Objects/week2.hex` — Generated HEX firmware
