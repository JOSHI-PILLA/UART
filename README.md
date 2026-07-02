# Universal Asynchronous Receiver Transmitter

# UART Protocol — Implementation, Simulation & Comparative Analysis

A study of UART (Universal Asynchronous Receiver Transmitter) communication implemented and verified across three development environments: **Keil µVision (8051 Assembly)**, **Proteus Design Suite** (circuit simulation), and **Arduino via Tinkercad** (C++/Serial library).

**Author:** Pilla Joshi — B.Tech, Electronics and Communication Engineering

---

## Abstract

This project implements and verifies UART communication using a low-level, register-based approach (8051 Assembly in Keil µVision, validated in Proteus) alongside a high-level, library-driven approach (Arduino UNO in Tinkercad). The goal is to demonstrate UART functionality on both ends of the abstraction spectrum and compare code complexity, development time, and hardware control.

## Objectives

- Understand UART's working principle at both the hardware register level and the software abstraction level.
- Implement UART transmission using 8051 Assembly language in Keil µVision.
- Validate the implementation via circuit simulation in Proteus using the generated HEX file.
- Implement equivalent UART functionality using Arduino in Tinkercad with built-in serial libraries.
- Compare both approaches by code complexity, development effort, and usability.

## Introduction

UART is an asynchronous serial communication protocol using two lines — **TX** (transmit) and **RX** (receive) — commonly used for communication between microcontrollers, sensors, and computers. Implementing it requires configuring the baud rate, data frame format, and TX/RX control logic — either manually via hardware registers (8051 Assembly) or through abstracted libraries (Arduino).

## Tools & Platforms

| Platform | Role | Output Verified |
|---|---|---|
| Keil µVision | Assembly-level UART code development & debugging for 8051 | Disassembly window, register states |
| Proteus Design Suite | Virtual circuit simulation using compiled HEX file | Virtual Terminal showing transmitted string |
| Tinkercad Circuits | Arduino UNO based UART implementation using C++ | Serial Monitor showing repeated string output |

## Implementation

### 1. Keil µVision — 8051 Assembly

Direct configuration of the `SCON` register for UART mode, `TMOD`/`TH1` for Timer-1 based baud rate generation, and manual handling of `SBUF` plus the `TI` flag for character-by-character transmission (baud rate 9600).


### 2. Proteus Design Suite — Circuit Simulation

The Assembly program was compiled into a HEX file and loaded into an AT89C51 circuit in Proteus. A Virtual Terminal connected to RXD/TXD confirmed correct real-time UART transmission — verifying the register-level configuration without physical hardware (Figure 2).

### 3. Tinkercad — Arduino UNO (C++)

The same functionality reimplemented using Arduino's built-in Serial library, which abstracts away register-level configuration entirely.


## Comparative Analysis: Assembly vs Arduino

| Aspect | Keil / 8051 Assembly | Arduino (Tinkercad) |
|---|---|---|
| Programming Level | Low-level, register-based | High-level, library-based |
| Lines of Code | ~19 lines (manual control logic) | ~6 lines (built-in functions) |
| UART Setup | Manual SCON, TMOD, TH1 register config | Single call: `Serial.begin(9600)` |
| Data Transmission | Manual SBUF load + TI flag polling loop | Single call: `Serial.println()` |
| Learning Curve | Steep — requires hardware register knowledge | Gentle — abstracted hardware details |
| Development Time | Higher — more debugging at register level | Lower — rapid prototyping |
| Code Readability | Moderate (needs inline comments) | High — self-explanatory function names |
| Hardware Control | Full, precise control over UART hardware | Limited to library-exposed functionality |
| Best Suited For | Embedded systems education, optimization | Rapid prototyping, IoT applications |

### Key Observations

- **~68% fewer lines of code:** Arduino needed only ~6 lines versus ~19 lines of register-level Assembly for the same UART output.
- **Abstraction vs. control trade-off:** Arduino's Serial library trades fine-grained hardware control for speed and simplicity; Assembly trades development speed for precise register/timing control.
- **Debugging effort:** Assembly debugging required monitoring `SCON`, the `TI` flag, `SBUF`, and disassembly windows; Arduino debugging was limited to reading Serial Monitor output.
- **Educational value:** The Assembly implementation gives deeper insight into how UART hardware actually operates, which the Arduino abstraction conceals.

## Conclusion

This project demonstrated UART communication across three complementary platforms. The 8051 Assembly implementation (Keil, validated in Proteus) provided a foundational, register-level understanding of UART hardware operation. The Arduino implementation (Tinkercad) showed how high-level libraries drastically simplify UART communication, cutting code volume and development time at the cost of some hardware-level control. Together, they illustrate the core trade-off between low-level hardware mastery and high-level development efficiency in embedded systems and IoT platform choice.
