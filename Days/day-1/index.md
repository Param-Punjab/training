## Day 1: Introduction to Operating Systems & Linux Fundamentals

## Date: [25-06-2025]

### 1. What is an Operating System (OS)?
![Error 404](files/operating-system.jpeg)
An Operating System (OS) is the most important software that runs on a computer. It manages computer hardware and software resources and provides common services for computer programs. You can think of it like a team leader, making sure all parts of the computer work well together.

### Key Responsibilities of an OS:
- **Process Management:** Allocating resources (CPU time, memory) to different running programs (processes) and managing their execution.
- **Memory Management:** Managing primary memory (RAM) and allocating it to processes, ensuring efficient use and preventing conflicts.
- **File Management:** Organizing and managing files and directories on storage devices, including creation, deletion, access control, and organization.
- **Device Management:** Controlling and coordinating input/output (I/O) devices like keyboards, mice, printers, and networking cards.
- **Security:** Protecting system resources and user data from unauthorised access through mechanisms like user authentication and access control lists.
- **User Interface (UI):** Providing a way for users to interact with the computer, either through a Graphical User Interface (GUI) or a Command Line Interface (CLI).
### 2. What is Linux Operating System?
Linux is a family of open-source Unix-like operating systems bassed on the Linux Kernel. It is known for its stability, security, flexibility, and powerful command-line tools. Unlike proprietary operating systems like Windows or macOS, Linux is developed and distributed under GNU General Public License, meaning its source code is freely available for anyone to use, modify, and distribute.
### Key Characteristics of Linux:
- **Open Source:** Free to use, modify, and distribute.
- **Multi-user:** Supports multiple users simultaneously.
- **Multi-tasking:** Can run multiple programs concurrently.
- **Secure:** Robust security features build-in.
- **Stable:** Known for its reliability and up-time.
- **Customizable:** Highly configurable and adaptable to various needs.
- **Community-driven:** Supported by a vast global community of developers and users.
### 3. Different Methods to Use Linux (Ubuntu OS):
Ubuntu is one of the most popular and user-friendly Linux distributions. Here are common ways to experience it:
- **Virtual Machine(e.g., VirtualBox):**
	- **Concept:** A virtual machine is a software-bassed emulation of a computer system. It allows you to run multiple operating systems simultaneously on a single physical machine.
	- **Advantages:** Safe, isolated environment; easy to install and remove; no risk to your existing operating system; ideal for testing and learning.
	- **Disadvantages:** Performance can be slightly lower than a native installation; requires sufficient RAM and CPU resources from the host machine.
	- **Setup:** Involves installing a hypervisor (like VirtualBox or VMware Workstation/Fusion) on your host OS and then installing Ubuntu within the virtual environment.
- **Dual Boot:** 
	- **Concept:** Installing two or more operating systems on the same physical hard drive, allowing you to choose which OS to boot into at startup.
	- **Advantages:** Full hardware performance for both operating systems; ideal for dedicated use of Linux.
	- **Disadvantages:** Requires partitioning your hard drive; more complex to set up; potential for data loss if not done carefully; you can only use one OS at a time.
	- **Setup:** Involves shrinking your existing OS partition and creating new partitions for Linux during installation.
- **Live USB/DVD:**
	- **Concept:** Running an operating system directly from a USB drive or DVD without installing it on your hard drive.
	- **Advantages:** No installation required; excellent for testing Linux before committing to an installation; useful for system recovery.
	- **Disadvantages:** Changes are not persistent (unless explicitly configured); slower performance than an installed OS.
- **Windows Subsystem for Linux (WSL):**
	- **Concept:** A compatibility layer for running Linux binary executables natively on Windows 10 and Windows 11. It provides a full-featured Linux environment integrated with Windows.
	- **Advantages:** Seamless integration with Windows; no dual-booting required; easy to install and use for development and command-line tasks.
	- **Disadvantages:** Not  a full Linux Kernel; some hardware interactions are limited compared to a native installation.
- **Cloud Instance (e.g., AWS EC2, Google Cloud Compute Engine):**
	- **Concept:** Renting virtual servers in the cloud that use Linux.
	- **Advantages:** Scalability, accessibility from anywhere, managed infrastructure, ideal for development and deployment.
	- **Disadvantages:** Cost implications, requires internet access.
