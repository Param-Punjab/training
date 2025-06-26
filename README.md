# tranning
A comprehensive day-by-day documentation of my tranning. Covers foundational concepts, booting mechanisms, shell, environments, command-line mastery, and more - with detailed notes, assignments, and practical command usage. Ideal for beginners and intermediate learners of Linux.

# TRCS2001 Training Repository

![Linux OS Banner](https://via.placeholder.com/1200x400/333333/FFFFFF?text=Linux+Operating+System+Fundamentals)

This repository documents my daily progress through the TRCS2001 Linux and Operating Systems training course. Each day's learning is documented with detailed explanations, command references, and practical examples.

## Table of Contents
- [Day 1: Operating Systems Fundamentals](#day-1-operating-systems-fundamentals)
- [Day 2: Linux Boot Process & Command Line Fundamentals](#day-2-linux-boot-process--command-line-fundamentals)
- [Shell Comparison Guide](#shell-comparison-guide)
- [Essential Linux Commands Reference](#essential-linux-commands-reference)
- [Assignment Solutions](#assignment-solutions)
- [Advanced Concepts](#advanced-concepts)
- [Resources](#resources)

---

## Day 1: Operating Systems Fundamentals

### What is an Operating System?
An Operating System (OS) is system software that manages computer hardware and software resources while providing common services for computer programs. The OS acts as an intermediary between users and computer hardware, performing essential functions:

1. **Process Management**: Creation, scheduling, and termination of processes
2. **Memory Management**: Allocation and deallocation of memory space
3. **File System Management**: Creation, deletion, and organization of files
4. **Device Management**: Communication with hardware devices
5. **Security**: User authentication and access control
6. **Networking**: Handling network communications
7. **User Interface**: Providing CLI or GUI for user interaction

### Linux Operating System
Linux is a family of open-source Unix-like operating systems based on the Linux kernel. Key characteristics:
- **Open Source**: Source code freely available for modification and distribution
- **Modular Design**: Components can be added or removed as needed
- **Multi-user & Multitasking**: Supports multiple users and processes simultaneously
- **Security**: Robust permission system and security features
- **Distributions**: Various flavors (Ubuntu, Fedora, Debian, etc.) with different configurations

### Accessing Linux Environments
#### 1. Virtual Box (Virtualization)
- Creates isolated virtual machines (VMs) on your current OS
- Benefits: Safe experimentation, snapshot capability, host-guest file sharing
- Setup Process:
  ```bash
  # Typical VirtualBox installation on Ubuntu
  sudo apt update
  sudo apt install virtualbox virtualbox-ext-pack
