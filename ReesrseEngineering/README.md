# Reverse Engineering Notes
- [Basic Tools](#basic-tools)
- [Advance Tools](#advance-tools)
- [Docker](#docker)
- [Videos and Articles](#videos-and-articles)
- [Terminologies](#terminologies)
- [Notes](#notes)
  - [File Formats and Protections](#file-formats-and-protections)
  -  
- [Labs](#labs)
- [Videos and Articles](#videos-and-articles)


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
- [Cutter](https://github.com/rizinorg/cutter)
- GDB
- WinGDB
- OllyDbg
- [dogbolt.org](https://dogbolt.org)

## Docker
- kasmweb/remnux
  - Image: https://hub.docker.com/r/kasmweb/remnux-focal-desktop
  - Install: `docker pull kasmweb/remnux-focal-desktop:1.16.0`
  - Start: `docker run -it --rm -p 6901:6901 -e VNC_PW=password kasmweb/remnux-focal-desktop:1.16.0`
  - Open https://localhost:6901/ and allow https
  - User : kasm_user Password: password
  - Then wait some second and click on connect.
  

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


###
    Buffer overflow
    Modify variable's value
    Return to win
    Return to shellcode
    Integer Overflow
    Format string exploit
    Bypassing mitigations
    GOT overwrite
    Return to PLT
    Playing with ROP

## Labs
- TryHackMe
- [Crackmes](https://crackmes.one/)
  
## Videos and Articles
- [Reverse Engineering Like a Hacker](https://youtu.be/-__qkpSk_rg)
- [Exploit Education website](https://exploit.education/)
- [Nightmare course on GitHub](https://guyinatuxedo.github.io/)

  
