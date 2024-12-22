# Reverse Engineering Notes
- [Labs](#labs)
- [Basic Tools](#basic-tools)
- [Advance Tools](#advance-tools)
- [Videos and Articles](#videos-and-articles)
- [Terminologies](#terminologies)
- [Notes](#notes)
  - [File Formats and Protections](#file-formats-and-protections)
  - 
- [Videos and Articles](#videos-and-articles)

## Labs
- [Crackmes](https://crackmes.one/)
- [TryHackMe](https://tryhackme.com/)

## Basic Tools
- `file`: to know file type and format.
- `strings`: to print all strings enside executables.
- `checksec`: checking file details
- `readelf`: This linux specific tools helps to get info.
- `objdump`: This linux specific tools helps to get info from objects.
- `hexeditor`: reading hex file and modifying string with it.
- `ltrace` and `strace`: record library call while running any excutable.
  
## Advance Tools
- [Ghidra](https://github.com/NationalSecurityAgency/ghidra)
- [Radare2](https://github.com/radareorg/radare2)
- GDB
- WinGDB
- OllyDbg
- [dogbolt.org](https://dogbolt.org)

## Docker
1. Link: https://hub.docker.com/r/kasmweb/remnux-focal-desktop
  ```bash
  docker pull kasmweb/remnux-focal-desktop
  ```

## Terminologies
- Machine Code:
- Assembly:
- Executable:
- Compiler:

## Notes
### File Formats and Protections
- #### PE Sections:
  - .text: Code.
  - .data: Initialized variables.
  - .rdata: Read-only data.
- #### ELF Sections:
  - .text: Code.
  - .bss: Uninitialized data.
  - .plt and .got: Dynamic linking.
- #### Understanding Protections
  - ASLR (Address Space Layout Randomization): Randomizes memory locations.
    - Solution: Use information leaks to bypass.
  - DEP (Data Execution Prevention): Prevents execution of non-code memory.
    - Solution: Use return-oriented programming (ROP).
  - Obfuscation: Hides program logic.
    - Solution: Deobfuscate by analyzing patterns.

## Videos and Articles
- [Reverse Engineering Like a Hacker](https://youtu.be/-__qkpSk_rg)

  
