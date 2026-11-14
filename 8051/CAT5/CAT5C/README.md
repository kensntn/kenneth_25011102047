# EXPERIMENT DETAILS

**EXP:** CONTINUOUS ASSESSMENT 5 (CAT5)  
**DATE:** 10/08/2026  
**NAME OF EXP:** Hardware Timer and Interrupt-Based Timing for LED Fading, Pulse Generation, and Stepper Motor Control  
**HARDWARE SETUP / PLATFORM:** AT89S52 (11.0592 MHz) + 8051 Development Board

---

# TASK 5C — STEPPER MOTOR SPEED AND DIRECTION CONTROL

<sub>Optional task for this week</sub>

## Experiment Aim

To control stepper motor rotation using Timer 0 interrupts. The timer determines when the next motor step is applied, and changing the interval between steps changes the motor speed.

## Hardware Setup

| Item | Details |
|---|---|
| Microcontroller | AT89S52 |
| Clock frequency | 11.0592 MHz |
| Output device | Stepper motor |
| Timing source | Timer 0 interrupt |
| Control method | Interrupt-based step sequencing |

## Circuit Diagram

![CAT5C Circuit Diagram](circuit.png)

## Step Pattern

The motor is driven by applying the following four output patterns in sequence:

```text
Step 1  →  1000
Step 2  →  0100
Step 3  →  0010
Step 4  →  0001
```

After the fourth pattern, the sequence starts again from the first. Repeating this order produces continuous stepping.

## Speed Control

The interval between consecutive step patterns determines the stepping speed.

| Speed selection | Interval per step |
|---|---:|
| Slow | 100 ms |
| Medium | 50 ms |
| Fast | 10 ms |

A smaller interval means the next step is applied sooner, increasing the stepping speed.

## Interrupt Operation

Timer 0 provides the timing event for each motor step. When its interrupt occurs, the controller performs the following operations:

1. Select the next pattern from the step sequence.
2. Send that pattern to the motor interface.
3. Advance the sequence position.
4. Continue from the beginning after the final pattern.

The timer interval is adjusted to obtain the required speed setting.

## Program Flow

```text
Initialize step sequence
          |
Configure Timer 0
          |
Enable timer interrupt
          |
Timer 0 interrupt occurs
          |
Output next step pattern
          |
Advance sequence position
          |
Repeat
```

## Inference

The experiment demonstrates how Timer 0 interrupts can control the timing of stepper motor excitation. A repeating four-pattern sequence drives the motor, while the interval between successive patterns determines the stepping speed. Using timer interrupts avoids depending on software delay loops for step timing.

**Implementation note:** The supplied experiment description specifies the step sequence and speed intervals, but does not provide a separate direction-reversal sequence or direction-control input.
