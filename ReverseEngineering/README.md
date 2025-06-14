# Reverse Engineering Notes

## Table of Contents
- [Basic Tools](#basic-tools)
- [Advanced Tools](#advanced-tools)
- [Docker](#docker)
- [Terminologies](#terminologies)
- [Notes](#notes)
  - [File Formats and Protections](#file-formats-and-protections)
  - [Exploitation Techniques](#exploitation-techniques)
- [Labs](#labs)
- [Videos and Articles](#videos-and-articles)

## Basic Tools
- `file`: Identify file type and format.
- `strings`: Extract readable strings from executables.
- `checksec`: Analyze security features of binaries.
- `readelf`: Retrieve metadata from ELF files.
- `objdump`: Disassemble and inspect object files.
- `hexeditor`: Modify binary files at the hex level.
- `ltrace` and `strace`: Trace library and system calls.
- `nm`: List symbols from object files.
- `patchelf`: Modify ELF binaries.
- `capstone`: Disassembly framework.
- `keystone`: Assembly framework.
- `unicorn`: Emulation framework.

## Advanced Tools
- [Ghidra](https://github.com/NationalSecurityAgency/ghidra) / [Radare2](https://github.com/radareorg/radare2) / [Cutter](https://github.com/rizinorg/cutter) / IDA PRO / [radare2 GUI](https://github.com/radareorg/iaito)
- GDB
- WinGDB
- OllyDbg
- [dogbolt.org](https://dogbolt.org)
- [x64dbg](https://x64dbg.com/)
- [angr](https://github.com/angr/angr): Symbolic execution framework.
- [ROPgadget](https://github.com/JonathanSalwan/ROPgadget): Find ROP gadgets.
- [Pwntools](https://github.com/Gallopsled/pwntools): Exploit development framework.
- [Binary Ninja](https://binary.ninja/)

## Docker
- `theflash2k/pwn-dev`

## Terminologies
- Machine Code: Low-level binary instructions executed by the CPU.
- Assembly: Human-readable representation of machine code.
- Executable: A compiled binary file ready to be executed.
- Compiler: Translates source code into machine code.
- Debugger: A tool to analyze and manipulate program execution.
- Disassembler: Converts machine code into assembly.
- Decompiler: Converts binary code back into high-level code.
- Static Analysis: Examining binaries without executing them.
- Dynamic Analysis: Analyzing binaries by executing them in a controlled environment.
- Symbolic Execution: Analyzing programs by following all possible execution paths.
- ROP (Return Oriented Programming): Exploiting return instructions to gain control.
- Heap Overflow: Exploiting memory mismanagement in heap.
- Stack Overflow: Overwriting return addresses in stack memory.
- Format String Vulnerability: Exploiting uncontrolled format string inputs.
- Code Obfuscation: Techniques to make binary analysis harder.
- Reversing Malware: Analyzing malicious binaries to understand behavior.
- Encryption & Encoding: Methods to obscure data within binaries.
- Packed Executables: Binaries modified to hide code until execution.
- Hooking: Intercepting function calls or system events for analysis or modification.
- Debug Symbols: Additional information in binaries to aid debugging.
- Syscalls: Direct interactions with the operating system's kernel.

## Notes
### File Formats and Protections
- PE Sections:
  - .text: Code.
  - .data: Initialized variables.
  - .rdata: Read-only data.
- ELF Sections:
  - .text: Code.
  - .bss: Uninitialized data.
  - .plt and .got: Dynamic linking.
- Understanding Protections:
  - ASLR (Address Space Layout Randomization): Randomizes memory locations.
    - Bypass: Use information leaks.
  - DEP (Data Execution Prevention): Prevents execution of non-code memory.
    - Bypass: Use return-oriented programming (ROP).
  - Obfuscation: Hides program logic.
    - Bypass: Deobfuscate by analyzing patterns.

### Exploitation Techniques
- Stack-based Buffer Overflow: Overwriting return addresses to hijack execution.
- Heap-based Exploitation: Manipulating dynamic memory allocation for control.
- Integer Overflow: Exploiting arithmetic errors to bypass security checks.
- Format String Exploits: Leaking memory or modifying execution flow via uncontrolled format strings.
- Return to Libc: Calling existing library functions to execute arbitrary code.
- ROP (Return Oriented Programming): Chaining gadgets to execute arbitrary instructions.
- JOP (Jump Oriented Programming): Similar to ROP but using jump instructions.
- GOT Overwrite: Modifying function pointers in the Global Offset Table to redirect execution.
- PLT Hijacking: Exploiting the Procedure Linkage Table to control execution flow.
- Code Injection: Injecting shellcode into a process and executing it.
- Sandbox Evasion: Bypassing restricted execution environments.
- Symbol Resolution Exploits: Manipulating dynamic linking to execute unintended code.

## Labs
- TryHackMe
- [Crackmes](https://crackmes.one/)

## Videos and Articles
- [Reverse Engineering Like a Hacker](https://youtu.be/-__qkpSk_rg)
- [Exploit Education website](https://exploit.education/)
- [Nightmare course on GitHub](https://guyinatuxedo.github.io/)
