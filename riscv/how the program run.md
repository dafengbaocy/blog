### 编译过程

1. 解释型语言：Interpreter is a program that executes other  program 
2. 编译型语言

compiler：

**Input**: High-Level Language Code (e.g., foo.c) §

**Output**: Assembly Language Code (e.g., foo.s for RISC-V)

- Pseudo-instructions: instructions that  assembler understands but not in machine

assembler

**Input**: Assembly Language Code (includes  pseudo ops) (e.g., foo.s for RISC-V) § 

**Output**: Object Code, information tables (true  assembly only) (e.g., foo.o for RISC-V

linking:静态链接：symbol tables；动态链接：库和程序相分离

loader