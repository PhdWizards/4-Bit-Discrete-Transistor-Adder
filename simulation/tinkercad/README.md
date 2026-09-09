# Simulation
This folder contains the circuit simulation used during the development of the project.
The simulation was created to verify the digital logic and the binary-to-BCD conversion before moving to the final schematic and PCB implementation.


## Overview
The simulated circuit takes a **5-bit binary input** and converts it into a decimal value displayed on two 7-segment displays.
The binary input is provided using DIP switches. The logic circuit processes the input and produces the corresponding BCD representation for the:
- **Tens digit**
- **Ones digit**
Two **CD4511** BCD-to-7-segment decoder/drivers are used to control the displays.


## Circuit
The simulation contains the following main functional blocks:
```text
          5-bit Binary Input
                 │
                 ▼
        ┌──────────────────┐
        │ Digital Logic    │
        │                  │
        │ 74HC04           │
        │ 74HC08           │
        │ 74HC32           │
        │ 74HC283          │
        └────────┬─────────┘
                 │
                 ▼
          BCD Conversion
                 │
          ┌──────┴──────┐
          ▼             ▼
       Tens BCD      Ones BCD
          │             │
          ▼             ▼
      CD4511          CD4511
          │             │
          ▼             ▼
     7-Segment       7-Segment
      Display         Display
```


## Components Used

### Logic ICs
| Component | Function |
|-----------|----------|
| 74HC04 | NOT gates |
| 74HC08 | AND gates |
| 74HC32 | OR gates |
| 74HC283 | 4-bit binary adder |
| CD4511 | BCD-to-7-segment decoder/driver |

### Other Components
- 2 × 7-segment displays
- DIP switches for binary input
- Current-limiting resistors
- 5 V power supply


## Input
The input is selected using five DIP switches:
```text
B4 B3 B2 B1 B0
```
Each switch represents one bit of the binary input.
The 5-bit input can represent values from:
```text
00000₂ = 0₁₀
```
to:
```text
11111₂ = 31₁₀
```
For example:
```text
Input: 10101₂
```
represents:
```text
21₁₀
```


## Output
The resulting binary value is converted into BCD and split into two decimal digits:
```text
          5-bit Binary
                │
                ▼
        ┌───────────────┐
        │ BCD Conversion│
        └───────┬───────┘
                │
       ┌────────┴────────┐
       ▼                 ▼
   Tens BCD           Ones BCD
       │                 │
       ▼                 ▼
    CD4511             CD4511
       │                 │
       ▼                 ▼
  7-Segment          7-Segment
    Display            Display
```
For example:
```text
Binary: 10101₂

Decimal: 21₁₀

Tens BCD:
0010

Ones BCD:
0001

```
The two 7-segment displays therefore show:
```text
21
```


## Simulation Screenshot
The following image shows the complete simulated circuit in Tinkercad:
![Tinkercad Simulation](tinkercad.png)


## Tinkercad Simulation
The complete interactive simulation is available on Tinkercad:
[**Open Tinkercad Simulation**](https://www.tinkercad.com/things/4N6F5v3ThxK-5-bit-to-bcd-double-dabble)
The simulation can be used to change the binary input and observe the corresponding decimal output on the two 7-segment displays.


## Verification
The simulation was used to verify the main logic of the circuit before moving to the physical implementation.
The following functions were tested:
- 5-bit binary input
- Digital logic processing
- Binary-to-BCD conversion
- Tens digit generation
- Ones digit generation
- CD4511 decoder operation
- 7-segment display output
Different binary input combinations were tested to ensure that the displayed decimal value matched the expected result.


## Example
One example of the simulation is:
```text
Binary Input:
10101₂

Expected Decimal Output:
21₁₀

BCD:
Tens  = 0010
Ones  = 0001

7-Segment Display:
21
```


## Development Process
The simulation was developed as part of the overall hardware design process:

```text
Logic Design
     ↓
Circuit Simulation
     ↓
KiCad Schematic
     ↓
PCB Design
     ↓
PCB Manufacturing
     ↓
Component Assembly
     ↓
Hardware Testing
```
The simulation helped verify the logic before committing to the final PCB implementation.

The `tinkercad.txt` file contains the link to the interactive Tinkercad simulation.
For the complete project, see the main repository documentation:
[**Back to Main README**](../README.md)
