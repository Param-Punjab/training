## Day 2: Booting Process, Kernal, shell and Basic Commands
## Date: [26-06-2025]

### 1. Booting: The System Startup Process
Booting is the initial set of operations that a computer performs when power is switched on, leading to the loading and execution of the operating system, Essentially, it's the process where the computer "wakes up" and prepares itself for user interaction.

### The Booting Process (Simplified):
1. **Power On Self-Test (POST):** The firmware (BIOS/UEFI) perform a series of checks on hardware components (RAM, CPU, peripherals) to ensure they are functioning correctly. 
2. **BIOS/UEFI Initialization:** The firmware initializes hardware components and searches for a bootable device.
3. **Bootloader Loading:** The firmware loads the bootloader (e.g., GRUB for Linux) from the bootable device into memory.
4. **Kernel Loading:** The bootloader loads the operating system kernal into RAM.
5. **Kernel Initialization:** The Kernel initializes core system components, sets up memory management, and loads necessary drivers.
6. **Init System Startup (systemd/SysVint):** The kernel hands over control to the init system, which starts essential services and daemons (background processes), prepares the user environment, and brings the system to a usable state.
7. **Login Prompt/Graphical Desktop:** The system presents either a login prompt (CLI) or a graphical desktop environment (GUI).

### 2. Types of Booting:
- **Cold Booting / Hard Booting:**
	- **Definition:** Starting the computer from a completely powered-off state. This involves pressing the power button.
	- **Process:** A full POST is performed, and all hardware components are re-initialized from scratch.
	- **Examples:** Turning on a computer after it has been shut down; restarting a frozen computer by holding the power button.
- **Worm Booting / Soft Booting:**
	- **Definition:** Restarting a computer without completely cutting off power. This is typically initiated from within the operating system (e.g., "Restart" option).
	- **Process:** This system bypasses the initial POST and re-initializes only essential components, leading to a faster restart.
	- **Examples:** Clicking "Restart" in your OS; pressing Ctrl+Alt+Delete (in some contexts).

### 3. What is the Kernel?
The kernel is the core component of an operating system. It acts as a bridge between the application (user space) and the hardware (hardware space), managing the computer's resources and facilitating communication between software and hardware.
### Key Functions of the kernel:
- **Process Management:** Scheduling and managing process, allocating CPU time, and handling inter-process communication.
- **Memory Management:** Allocating and deallocating memory to processes, managing virtual memory, and optimizing memory usage.
- **Device Management:** Interacting with hardware devices through devices drivers, enabling applications to use peripherals like printers, network cards, and storage devices.
- **System Calls:** Providing a set of interfaces (system calls) through which user applications can request services from the kernel (e.g., reading a file, creating a process).
- **File System Management:** Organizing and managing files on storage devices, including reading, writing, and controlling access.

### 4. Understanding Shells
A shell is a command-line interpreter or a graphical user interface that provides an interface for users to interact with the operating system. In Linux, shells are primarily command-line based. They take commands typed by the user, interpret them, and pass them to the kernel for execution.

### Common Types of shells in Linux:
- **`sh` (Bourne shell):**
	- **Description:** The original Unix shell, known for its simplicity and foundational role. It provides basic scripting capabilities.
	- **Characteristics:** Less interactive features compared to newer shells.
- **`bash`(Bourne-Again SHell):**
	- **Description:** The most common and default shell on many Linux distributions (including Ubuntu). It's an enhanced version of `sh`.
	- **Characteristics:** Includes features like command-line editing, command history, tab completion, job control, and powerful scripting capabilities.
- **`zsh` (Z Shell):**
	- **Description:** A powerful and high customizable shell that builds upon `bash` with many advanced features. Often preferred by power users. 
	- **Characteristics:** Enhanced tab completion, better globbing (pattern matching), spell correction, theme support (Oh My Zsh is popular), and intelligent history search.
- **`fish`(Friendly Interactive SHell):**
	- **Description:** Designed to be a more user-friendly and interactive shell with features like auto-suggestions and syntax highlighting out-of-the-box.
	- **Characteristics:** Intuitive auto-suggestions based on history, syntax highlighting, web-based configuration, and simpler scripting syntax.

### 5. Two Types of interfaces: 
- **GUI (Graphical User Interface):**
	- **Description:** A user interface that allows user to interact with electronic devices through graphical icons and visual indicators, as opposed to text-based interfaces.
	- **Characteristics:** User-friendly, intuitive, relies on mouse clicks and visual elements.
	- **Examples:** Ubuntu's GNOME desktop, Windows desktop, macOS.
- **CLI (Command Line Interface):**
	- **Description:** A text-based interface used to operate software and operating system by typing commands.
	- **Characteristics:** Powerful, efficient for repetitive tasks, precise control, requires memorization of commands.
	- **Examples:** Linux Terminal, Windows Command Prompt, PowerShell.

### 6. Basic Linux Components:
Here's a detailed look at the basic Linux commands covered, along with more advanced usage and related commands:
- **`ls`(List Directory Contents):**
	- **Purpose:** List the contents of a directory.
	- **Basic Usage:** `ls` (lists contents of current directory)
	- **Advanced Usage:** 
		- `ls -l`: Long listing format (permissions, owner, group, size, data, name).
		- `ls -a`: Lists all files, including hidden files (those starting with a `.`).
		- `ls -lh`: Long listing with human-readable file sizes (e.g., 1K, 234M, 2G).
		- `ls -F`: Appends indicators (/, *, @, =) to entries to show their type (directory, executable, symbolic link, socket).
		- `ls -R`: recursively lists subdirectories.
		- `ls /path/to/directory`: List contents of a specific directory.
	- **Related:** `dir` (another command for listing directory contents, less common in Linux).
- **`cd`(Change Directory):**
	- **Purpose:** Change the current working directory.
	- **Basic usage:** `cd documents` (moves into the "Documents" directory).
	- **Advanced Usage:**
		- `cd ..`: Moves up one directory level.
		- `cd ~`: Moves to the user's home directory.
		- `cd -`: Moves to the previous working directory.
		- `cd /`: Moves to the root directory.
		- `cd /home/user/projects`: Moves to an absolute path.
- **`mkdir`(Make Directory):** 
	- **Purpose:** Creates new directories.
	- **Basic usage:** `mkdir my_folder` (creates a folder name "my_folder")
	- **Advanced Usage:**
		- `mkdir -p project/src/data`: Creates parent directories if they don't exist (e.g., creates `project`, then `src`, then `data`).
		- `mkdir folder1 folder2`: Creates multiple directories at once.
	- **Related:** `rmdir` (for removing empty directories).
- **`cat` (Concatenate and Display Files):
	- **Purpose:** Displays the content of files. Can also be used to create files with content directly from the terminal
	- **Basic usage:** `cat myfile.txt` (displays content of `myfile.txt`)
	- **Creating File with `cat`:** `cat > new_file.txt` (type content, then press Ctrl+D to save and exit).
	- **Advanced Usage:**
		- `cat file1.txt file2.txt > combined. txt`: Concatenates `file1.txt` and `file2.txt` into `combined.txt`.
		- `cat -n myfile.txt`: Displays content with line numbers.
		- `cat -s myfile.txt` Squeezes multiple blank lines into a single black line.
	- **Related:** `less`, `more` (for viewing large files page by page), `head`, `tail` (for viewing beginning/end of files).
- **`touch` (change File Timestamps / Create Empty Files):
	- **Purpose:** creates new, empty files if they don't exist, or updates the access and modification timestamps of existing files.
# In Progress
