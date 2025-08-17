# Libasm-Linux

### This project rewrites in x86_64 ASM (in Intel syntax) six functions:
- Three from the C standard library (strlen, strcpy, strcmp)
- Two POSIX system calls (write, read) 
- One POSIX string function (strdup)

CPU (Central Processor Unit) process instructions in our source code (well, only after they have been 'translated' -compiled- to machine code -binary-). Different CPU`s process different types of instruction sets (ARM instruction set, X86, X64...). But CPU´s only understand 0's and 1's (binary code)!!!! ASM is the readable representation of the binary language that the processor understands. There's one assembly language per instruction set. x86_64 ASM is assembly language adapted to processors with X64 instruction set. 64-bit ASM is meant for CPU architectures with 64 bit registers (so we can address much more than 4Gb in RAM!!!!!). System V AMD64 ABI, which is the standard calling convention for 64-bit Linux and macOS systems, is used.

#### Registers in x86_64

| 64-bit | 32-bit | 16-bit | 8-bit |
|--------|--------|--------|-------|
| rax    | eax    | ax     | al    |
| rbx    | ebx    | bx     | bl    |
| rcx    | ecx    | cx     | cl    |
| rdx    | edx    | dx     | dl    |
| rsi    | esi    | si     | sil   |
| rdi    | edi    | di     | dil   |
| rsp    | esp    | sp     | spl   |
| rbp    | ebp    | bp     | bpl   |
| r8–r15 | r8d–r15d | r8w–r15w | r8b–r15b |

#### Function Calls in x86_64
(Calling Convention = System V AMD64 ABI, which is the standard calling convention for 64-bit Linux and macOS systems.)

Arguments to functions are passed in registers (not on the stack):

| Argument # | Register |
|------------|----------|
| 1st        | rdi      |
| 2nd        | rsi      |
| 3rd        | rdx      |
| 4th        | rcx      |
| 5th        | r8       |
| 6th        | r9       |

**Return values go in rax.**

## Usage
1. "make" command generates the libasm.a library (containing ft_strlen, ft_strcpy, ft_strcmp, ft_write, ft_read, ft_strdup functions). Note that you must have gcc and nasm installed (sudo apt install gcc && sudo apt install nasm)
2. "make test" command links and compiles the libasm.a library with a file (main.c) that tests the libasm.a library. Tests are executed comparing my assembly implementation against its official counterpart. Tests output is shown in the terminal.
