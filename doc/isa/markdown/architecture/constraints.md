## CONSTRAINT DEFINITIONS

Constraints in RISC-V ISA refer to limitations or rules regarding how certain instructions or fields can be used:

- **Immediate Constraints**: Specifies the range and format of immediate values that can be used in specific instructions.
- **Register Constraints**: Defines which registers can be used for specific operations (e.g., integer registers vs. floating-point registers).
- **Alignment Constraints**: Specifies memory alignment requirements for load and store operations.

Format of a line in the table:

`<constraint name> <constraint expression> <hint>`

| constraint name | constraint expression                     | hint        |
|-----------------|:------------------------------------------|:------------|
| `simm_6`        | `imm >= -32 && imm < 32`                  |             |
| `simm_9`        | `imm >= -256 && imm < 256`                |             |
| `simm_10`       | `imm >= -512 && imm < 512`                |             |
| `simm_12`       | `imm >= -2048 && imm < 2048`              |             |
| `imm_5`         | `imm >= 0 && imm <= 0b11111`              |             |
| `imm_6`         | `imm >= 0 && imm <= 0b111111`             |             |
| `imm_7`         | `imm >= 0 && imm <= 0b1111111`            |             |
| `imm_8`         | `imm >= 0 && imm <= 0b11111111`           |             |
| `imm_9`         | `imm >= 0 && imm <= 0b111111111`          |             |
| `imm_10`        | `imm >= 0 && imm <= 0b1111111111`         |             |
| `imm_12`        | `imm >= 0 && imm <= 0b111111111111`       |             |
| `imm_18`        | `imm >= 0 && imm <= 0b111111111111111111` |             |
| `imm_nz`        | `imm != 0`                                |             |
| `imm_x2`        | `(imm & 0b1) == 0`                        |             |
| `imm_x4`        | `(imm & 0b11) == 0`                       |             |
| `imm_x8`        | `(imm & 0b111) == 0`                      |             |
| `imm_x16`       | `(imm & 0b1111) == 0`                     |             |
| `rd_b3`         | `rd  >= 8 && rd  <= 15`                   |             |
| `rs1_b3`        | `rs1 >= 8 && rs1 <= 15`                   |             |
| `rs2_b3`        | `rs2 >= 8 && rs2 <= 15`                   |             |
| `rd_eq_rs1`     | `rd == rs1`                               |             |
| `rd_eq_ra`      | `rd == 1`                                 | `rd=1`      |
| `rd_eq_sp`      | `rd == 2`                                 | `rd=2`      |
| `rd_eq_x0`      | `rd == 0`                                 | `rd=0`      |
| `rs1_eq_sp`     | `rs1 == 2`                                |             |
| `rs1_eq_x0`     | `rs1 == 0`                                |             |
| `rs2_eq_x0`     | `rs2 == 0`                                | `rs2=0`     |
| `rd_ne_x0_x2`   | `rd != 0 && rd != 2`                      | `rd!={0,2}` |
| `rd_ne_x0`      | `rd != 0`                                 | `rd!=0`     |
| `rs1_ne_x0`     | `rs1 != 0`                                |             |
| `rs2_ne_x0`     | `rs2 != 0`                                | `rs2!=0`    |
| `rs2_eq_rs1`    | `rs2 == rs1`                              |             |
| `rs1_eq_ra`     | `rs1 == 1`                                |             |
| `imm_eq_zero`   | `imm == 0`                                |             |
| `imm_eq_n1`     | `imm == -1`                               |             |
| `imm_eq_p1`     | `imm == 1`                                |             |
| `csr_eq_0x001`  | `imm == 0x001`                            |             |
| `csr_eq_0x002`  | `imm == 0x002`                            |             |
| `csr_eq_0x003`  | `imm == 0x003`                            |             |
| `csr_eq_0xc00`  | `imm == 0xc00`                            |             |
| `csr_eq_0xc01`  | `imm == 0xc01`                            |             |
| `csr_eq_0xc02`  | `imm == 0xc02`                            |             |
| `csr_eq_0xc80`  | `imm == 0xc80`                            |             |
| `csr_eq_0xc81`  | `imm == 0xc81`                            |             |
| `csr_eq_0xc82`  | `imm == 0xc82`                            |             |

:Constraint Definitions

This table lists and defines the constraints and limitations imposed by the RISC-V ISA on various instructions, operands, and operations.

These constraints ensure compatibility and reliable operation across various implementations of RISC-V processors.
