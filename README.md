# Custom 3-Bit CPU Design Using Digital Logic Simulator

A complete CPU design and implementation project developed using the **Digital Logic Simulator**. This project demonstrates the construction of a simple processor from basic digital logic components, including the ALU, Register File, RAM, Program Counter, Control Unit, and Instruction Set Architecture (ISA).

---

## Project Overview

This processor was designed according to the following specifications:

| Component | Specification |
|------------|--------------|
| CPU Word Size | 3 Bits |
| ALU Operations | ADD, NOT, SHR |
| Number of Registers | 3 |
| RAM Size | 9 Words |
| RAM Word Size | 17 Bits |
| Instruction Size | 17 Bits |
| Branch Instructions | JMP, JC |
| Design Tool | Digital Logic Simulator |

---

## Features

- Custom 3-bit CPU architecture
- Hierarchical circuit design methodology
- Custom Arithmetic Logic Unit (ALU)
- Multi-register register file
- Custom RAM implementation
- Instruction decoding and execution
- Immediate and register-based operations
- Conditional and unconditional branching
- Complete CPU integration and verification

---

## CPU Architecture

The CPU consists of the following major components:

```text
CPU
├── Control Unit
├── Program Counter (PC)
├── Instruction Decoder
├── Arithmetic Logic Unit (ALU)
├── Register Set
├── RAM
└── Branching Logic
```

---

## Arithmetic Logic Unit (ALU)

The ALU performs all arithmetic and logical operations supported by the processor.

### Supported Operations

| Opcode | Operation |
|----------|-----------|
| 00 | ADD |
| 01 | NOT |
| 10 | SHR |

### ALU Submodules

- 3-Bit Adder
- 3-Bit NOT Circuit
- 3-Bit Shift Right Circuit
- ALU Control Logic

---

## Register File

The processor contains three 3-bit registers.

### Registers

| Register | Description |
|-----------|-------------|
| R0 | General Purpose Register |
| R1 | General Purpose Register |
| R2 | General Purpose Register |

### Construction Hierarchy

```text
1-Bit Register
      ↓
3-Bit Register
      ↓
3-Register Register File
```

---

## Memory System

The memory subsystem was built hierarchically from basic RAM cells.

### Memory Hierarchy

```text
1×1 RAM
   ↓
1×17 RAM
   ↓
9×17 RAM
```

### RAM Specifications

| Parameter | Value |
|------------|--------|
| Number of Locations | 9 |
| Word Size | 17 Bits |
| Address Width | 4 Bits |

---

## Instruction Set Architecture (ISA)

The CPU uses a custom 17-bit instruction format.

### Register Mode Instructions

#### Format

```text
| Type (2) | Operation (2) | Ra (2) | Rb (2) | Unused (9) |
```

#### Type Code

```text
00 = Register Mode
```

#### Supported Instructions

```assembly
ADD Ra, Rb
NOT Ra
SHR Ra, Rb
```

---

### Immediate Mode Instructions

#### Format

```text
| Type (2) | Operation (2) | Register (2) | Constant (3) | Unused (8) |
```

#### Type Code

```text
01 = Immediate Mode
```

#### Example Instructions

```assembly
ADD R1, 5
ADD R2, 1
```

---

### Branch Instructions

#### Format

```text
| Type (2) | Operation (2) | Address (4) | Unused (9) |
```

#### Type Code

```text
10 = Branch Mode
```

#### Supported Instructions

```assembly
JMP ADDRESS
JC ADDRESS
```

---

## Sample Program

The following assembly program was used to verify CPU functionality:

```assembly
JMP START

START:
ADD R1, 5

JMPTO:
ADD R1, 4

JC JMPTO

ADD R2, 1

SHR R1, R2

NOT R1
```

This sample program demonstrates:

- Immediate arithmetic operations
- Register operations
- Conditional branching
- Unconditional branching
- Shift operations
- Logical operations

---

## Program Counter

The CPU includes:

- 4-Bit Program Counter
- 4-Bit Increment Adder
- Branch Address Loading Logic

These components allow sequential instruction execution and branching.

---

## Control Unit

The Control Unit is responsible for:

- Instruction decoding
- ALU control signal generation
- Register write control
- Memory control
- Branch control
- Program Counter control

---

## Verification

The processor was verified by executing machine code instructions one at a time and observing:

- ALU outputs
- Register contents
- RAM contents
- Program Counter values
- Branch execution behavior

All components were tested individually before full CPU integration.

---

## Project Structure

```text
.
├── CPU.dig
├── ALU/
│   ├── Adder.dig
│   ├── NOT.dig
│   └── SHR.dig
├── Registers/
│   ├── 1bit_Register.dig
│   ├── 3bit_Register.dig
│   └── Register_File.dig
├── Memory/
│   ├── RAM_1x1.dig
│   ├── RAM_1x17.dig
│   └── RAM_9x17.dig
├── Control_Unit/
├── Documentation/
│   └── Project_Report.pdf
└── README.md
```

---

## Simulation Setup

### Requirements

- Digital Logic Simulator
- Project `.dig` files

### Running the Project

1. Clone the repository

```bash
git clone https://github.com/your-username/custom-3bit-processor.git
```

2. Open the project using the Digital Logic Simulator.

3. Load the top-level CPU circuit.

4. Initialize RAM with the sample machine code.

5. Execute instructions step-by-step using the clock input.

6. Observe outputs through:
   - Registers
   - ALU
   - RAM
   - Program Counter

---

## Demonstration Video

A complete demonstration video showing the processor execution is available below:

```text
https://drive.google.com/file/d/1Fk2fzDmPmQVqb2W4sDPCWAil16oCDO0q/view?usp=sharing
```

---

## Learning Outcomes

This project helped develop practical understanding of:

- Computer Architecture
- Processor Design
- Digital Logic Design
- Instruction Set Architecture
- Arithmetic Logic Units
- Register Files
- Memory Organization
- Control Unit Design
- CPU Verification Techniques

---

## Author

**Md. Sumon Ali**  
Department of Computer Science and Engineering  
Rajshahi University of Engineering & Technology (RUET)

---

## License

This project was developed for academic and educational purposes.
