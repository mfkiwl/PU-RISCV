## MAJOR OPCODES

Major opcodes in RISC-V encompass essential instruction categories such as arithmetic, logical operations, memory access, and control flow. Each major opcode represents a group of related instructions that share common functionalities and operand types, contributing to the versatility and efficiency of the RISC-V ISA across diverse computing applications.

| 6..5     | 4..2     | name             |
|----------|:---------|:-----------------|
| `6..5=0` | `4..2=0` | `LOAD`           |
| `6..5=0` | `4..2=1` | `LOAD-FP`        |
| `6..5=0` | `4..2=2` | `custom-0`       |
| `6..5=0` | `4..2=3` | `MISC-MEM`       |
| `6..5=0` | `4..2=4` | `OP-IMM`         |
| `6..5=0` | `4..2=5` | `AUIPC`          |
| `6..5=0` | `4..2=6` | `OP-IMM-32`      |
| `6..5=0` | `4..2=7` | `48-bit`         |
| `6..5=1` | `4..2=0` | `STORE`          |
| `6..5=1` | `4..2=1` | `STORE-FP`       |
| `6..5=1` | `4..2=2` | `custom-1`       |
| `6..5=1` | `4..2=3` | `AMO`            |
| `6..5=1` | `4..2=4` | `OP`             |
| `6..5=1` | `4..2=5` | `LUI`            |
| `6..5=1` | `4..2=6` | `OP-32`          |
| `6..5=1` | `4..2=7` | `64-bit`         |
| `6..5=2` | `4..2=0` | `MADD`           |
| `6..5=2` | `4..2=1` | `MSUB`           |
| `6..5=2` | `4..2=2` | `NMSUB`          |
| `6..5=2` | `4..2=3` | `NMADD`          |
| `6..5=2` | `4..2=4` | `OP-FP`          |
| `6..5=2` | `4..2=5` | `reserved`       |
| `6..5=2` | `4..2=6` | `custom-2,rv128` |
| `6..5=2` | `4..2=7` | `48-bit`         |
| `6..5=3` | `4..2=0` | `BRANCH`         |
| `6..5=3` | `4..2=1` | `JALR`           |
| `6..5=3` | `4..2=2` | `reserved`       |
| `6..5=3` | `4..2=3` | `JAL`            |
| `6..5=3` | `4..2=4` | `SYSTEM`         |
| `6..5=3` | `4..2=5` | `reserved`       |
| `6..5=3` | `4..2=6` | `custom-3,rv128` |
| `6..5=3` | `4..2=7` | `>80-bit`        |

:Major Opcodes

 The major opcodes table categorizes and lists the primary opcodes utilized in the RISC-V instruction set architecture, essential for navigating and comprehending the instruction set's core functionalities.
