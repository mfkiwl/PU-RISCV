## INSTRUCTION ENCODINGS

RISC-V instructions are encoded using fixed-length formats (32 or 64 bits) to simplify decoding and execution. The encoding specifies fields such as opcode, register specifiers (`rs1`, `rs2`, `rd`), immediate values, and function codes (`funct3`, `funct7`) where applicable. This structured approach enables straightforward instruction fetch and decode stages in the processor pipeline, contributing to overall performance efficiency.

Format of a line in the table:

`<codec> <format> [<argument> ... ]`

`<codec> denotes a distinct instruction type, subtype and format`

`[<argument> ... ] lists operands declared in opcodes as a cross-check`

`Codecs with a · sign denote a subtype of the higher level type`

`Codecs with a + sign denote a format variant for the same type`

`i.e. <type(·subtype+format)?> where codec is the distinct codec`

| codec        | format                   | argument                |
|--------------|:-------------------------|:------------------------|
| `u`          | `rd,imm`                 | `rd imm20`              |
| `u+o`        | `rd,offset`              | `rd oimm20`             |
| `uj`         | `rd,offset`              | `rd jimm20`             |
| `i+o`        | `rd,rs1,offset`          | `rd rs1 imm12`          |
| `i`          | `rd,rs1,imm`             | `rd rs1 imm12`          |
| `i·sh5`      | `rd,rs1,imm`             | `rd rs1 shamt5`         |
| `i·sh6`      | `rd,rs1,imm`             | `rd rs1 shamt6`         |
| `i·sh7`      | `rd,rs1,imm`             | `rd rs1 shamt7`         |
| `i·csr`      | `rd,csr,rs1`             | `rd rs1 csr12`          |
| `i·csr+i`    | `rd,csr,zimm`            | `rd zimm csr12`         |
| `i+l`        | `rd,offset(rs1)`         | `rd rs1 oimm12`         |
| `i+lf`       | `frd,offset(rs1)`        | `frd rs1 oimm12`        |
| `s`          | `rs2,offset(rs1)`        | `rs1 rs2 simm12`        |
| `sb`         | `rs1,rs2,offset`         | `rs1 rs2 sbimm12`       |
| `s+f`        | `frs2,offset(rs1)`       | `rs1 frs2 simm12`       |
| `r`          | `rd,rs1,rs2`             | `rd rs1 rs2`            |
| `r+fr`       | `frd,rs1`                | `frd rs1`               |
| `r+rf`       | `rd,frs1`                | `rd frs1`               |
| `r+rff`      | `rd,frs1,frs2`           | `rd frs1 frs2`          |
| `r+3f`       | `frd,frs1,frs2`          | `frd frs1 frs2`         |
| `r·m+ff`     | `rm,frd,frs1`            | `frd frs1 rm`           |
| `r·m+fr`     | `rm,frd,rs1`             | `frd rs1 rm`            |
| `r·m+rf`     | `rm,rd,frs1`             | `rd frs1 rm`            |
| `r·m+3f`     | `rm,frd,frs1,frs2`       | `frd frs1 frs2 rm`      |
| `r4·m`       | `rm,frd,frs1,frs2,frs3`  | `frd frs1 frs2 frs3 rm` |
| `r·a`        | `aqrl,rd,rs2,(rs1)`      | `rd rs1 rs2 aq rl`      |
| `r·l`        | `aqrl,rd,(rs1)`          | `rd rs1 aq rl`          |
| `r·f`        | `pred,succ`              | `pred succ`             |
| `r+sf`       | `rs1`                    | `rs1`                   |
| `r+sfa`      | `rs1,rs2`                | `rs1 rs2`               |
| `cb`         | `rs1,rs2,offset`         | `crs1q cimmb`           |
| `cb·imm`     | `rd,rs1,imm`             | `crs1rdq cnzimmi`       |
| `cb·sh5`     | `rd,rs1,imm`             | `crs1rdq cimmsh5`       |
| `cb·sh6`     | `rd,rs1,imm`             | `crs1rdq cimmsh6`       |
| `ci`         | `rd,rs1,imm`             | `crs1rd cnzimmi`        |
| `ci·sh5`     | `rd,rs1,imm`             | `crs1rd cimmsh5`        |
| `ci·sh6`     | `rd,rs1,imm`             | `crs1rd cimmsh6`        |
| `ci·16sp`    | `rd,rs1,imm`             | `crs1rd cimm16sp`       |
| `ci·lwsp`    | `rd,offset(rs1)`         | `crd cimmlwsp`          |
| `ci·ldsp`    | `rd,offset(rs1)`         | `crd cimmldsp`          |
| `ci·lqsp`    | `rd,offset(rs1)`         | `crd cimmlqsp`          |
| `ci·lwsp+f`  | `frd,offset(rs1)`        | `cfrd cimmlwsp`         |
| `ci·ldsp+f`  | `frd,offset(rs1)`        | `cfrd cimmldsp`         |
| `ci·li`      | `rd,rs1,imm`             | `crs1rd cimmi`          |
| `ci·lui`     | `rd,imm`                 | `crd cimmui`            |
| `ci·none`    | `none`                   |                         |
| `ciw·4spn`   | `rd,rs1,imm`             | `crdq cimm4spn`         |
| `cj`         | `rd,offset`              | `cimmj`                 |
| `cj·jal`     | `rd,offset`              | `cimmj`                 |
| `cl·lw`      | `rd,offset(rs1)`         | `crdq crs1q cimmw`      |
| `cl·ld`      | `rd,offset(rs1)`         | `crdq crs1q cimmd`      |
| `cl·lq`      | `rd,offset(rs1)`         | `crdq crs1q cimmq`      |
| `cl·lw+f`    | `frd,offset(rs1)`        | `cfrdq crs1q cimmw`     |
| `cl·ld+f`    | `frd,offset(rs1)`        | `cfrdq crs1q cimmd`     |
| `cr`         | `rd,rs1,rs2`             | `crs1rd crs2`           |
| `cr·mv`      | `rd,rs1,rs2`             | `crd crs2`              |
| `cr·jalr`    | `rd,rs1,offset`          | `crd0 crs1`             |
| `cr·jr`      | `rd,rs1,offset`          | `crd0 crs1`             |
| `cs`         | `rd,rs1,rs2`             | `crs1rdq crs2q`         |
| `cs·sw+f`    | `frs2,offset(rs1)`       | `crs1q cfrs2q cimmw`    |
| `cs·sd+f`    | `frs2,offset(rs1)`       | `crs1q cfrs2q cimmd`    |
| `cs·sw`      | `rs2,offset(rs1)`        | `crs1q crs2q cimmw`     |
| `cs·sd`      | `rs2,offset(rs1)`        | `crs1q crs2q cimmd`     |
| `cs·sq`      | `rs2,offset(rs1)`        | `crs1q crs2q cimmq`     |
| `css·swsp`   | `rs2,offset(rs1)`        | `crs2 cimmswsp`         |
| `css·sdsp`   | `rs2,offset(rs1)`        | `crs2 cimmsdsp`         |
| `css·sqsp`   | `rs2,offset(rs1)`        | `crs2 cimmsqsp`         |
| `css·swsp+f` | `frs2,offset(rs1)`       | `cfrs2 cimmswsp`        |
| `css·sdsp+f` | `frs2,offset(rs1)`       | `cfrs2 cimmsdsp`        |

:Instruction Encodings

This table provides an overview of the encoding formats used for representing instructions in the RISC-V ISA, including their bit-level structures, opcode assignments, operand fields, and any additional control bits necessary for proper execution.
