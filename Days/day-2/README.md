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
- **`cat` (Concatenate and Display Files):**
	- **Purpose:** Displays the content of files. Can also be used to create files with content directly from the terminal
	- **Basic usage:** `cat myfile.txt` (displays content of `myfile.txt`)
	- **Creating File with `cat`:** `cat > new_file.txt` (type content, then press Ctrl+D to save and exit).
	- **Advanced Usage:**
		- `cat file1.txt file2.txt > combined. txt`: Concatenates `file1.txt` and `file2.txt` into `combined.txt`.
		- `cat -n myfile.txt`: Displays content with line numbers.
		- `cat -s myfile.txt` Squeezes multiple blank lines into a single black line.
	- **Related:** `less`, `more` (for viewing large files page by page), `head`, `tail` (for viewing beginning/end of files).
- **`touch` (change File Timestamps / Create Empty Files):**
	- **Purpose:** creates new, empty files if they don't exist, or updates the access and modification timestamps of existing files.
- **`touch`(Change File Timestamps/ Create Empty Files):**
	- **Purpose:** Creates new, empty files if they don't exist,  or updates the access and modification timestamps of existing files.
	- **Basic Usage:** `touch new_empty_file.txt` (creates an empty file).
	- **Advanced Usage:
		- `touch -o existing_file.txt`: Updates only the access time.
		- `touch -m existing_file.txt`:Updates only the modification time.
		- `touch -t YYYYMMDDHHMM.SS file.txt`: Sets specific timestamps.
	- **Key Distinction with `cot >`:**  `touch` creates an empty file or updates timestamps; `cat >` creates a file and allows you to immediately input content.
- **`pwd` (Print Working Directory):**
	- **Purpose:** Displays the absolute path of the current working directory.
	- **Basic Usage:** `pwd`
	- **Advanced Usage:** `pwd -P` (prints the physical directory, resolving any symbolic links).
- **`whoami` (Who Am I):
	- **Purpose:** Displays the effective username of the current user.
	- **Basic Usage:** `whoami`
	- **Related:** `who` (shows who is logged on), `id` (displays user and group IDs).
- **`date` (Print or Set System Date and Time):**
	- **Purpose:** Displays the current system date and time.
	- **Basic Usage:** `date`
	- **Advanced Usage:** 
		- `date +"%Y-%m-%d %H:%M:%S"`: Format the output.
		- `date -s "2025-06-27 10:00:00"`: Set the system date and time (requires superuser privileges).
		- `date -u`: Displays UTC (Coordinated Universal Time).
	- **Related:** `col` (displays a calendar).
- **`whereis`(Locate the Binary, Source, and Manual Page Files for a Command):**
	- **Purpose:** Locates the binary, source, and manual page files for a specified command.
	- **Basic Usage:** `whereis ls`
	- **Output Example:** `ls: /usr/bin/ls /usr/share/man/man1/ls.1.gz`
	- **Related:** `which` (shows the full path of (shell) commands).
- **`whatis` (Display One-Line Manual Page Descriptions):**
	- **Purpose:** Provides a very brief one-line description from the manual page of a command.
	- **Basic Usage:** `whatis ls`
	- **Output Example:** `ls (1) - list directory contents`
	- **Related:** `man` (access the full manual pages).
- **`uname` (Print System Information):**
	- **Purpose:** Displays system information about the Linux Kernel.
	- **Basic Usage:** `uname` (outputs "Linux" on a Linux system).
	- **Advanced Usage:**
		- `uname -a`: Prints all system information (kernel name, hostname, kernel release, kernel version, machine hardware name, operating system).
		- `uname -r`: Prints the kernel release.
		- `uname -m`: Prints the machine hardware name (e.g., x86_64).
		- `uname -o`: Prints the operating system (e.g., GNU/Linux).
- **`clear` (Clear Terminal Screen):**
	- **Purpose:** Clears the terminal screen, moving the current command prompt to the top.
	- **Basic Usage:** `clear`
	- **Keyboard Shortcut:** Ctrl+L often performs the same action.

---
## Assignments:
These commands are crucial for file management and are frequently used in day-to-day Linux operations.
- **`cp` (Copy Files and Directories):**
	- **Purpose:** Copies files and directories from one location to another.
	- **Basic Usage:** `cp file.txt /path/to/destination/` (copies `file.txt` to the destination).
	- **Advanced Usage:**
		- `cp -r folder/ new_folder/`: Copies a directory and its contents recursively.
		- `cp -i file.txt destination/`: Prompts before overwriting existing files.
		- `cp -u file.txt destination/`: Copies only when the source is newer than the destination or when the destination file is missing.
		- `cp file1.txt file2.txt folder/`: Copies multiple files to a directory.
- **`mv` (Move or Rename Files and Directories):**
	- **Purpose:** Moves files or directories from one location to another, or renames them.
	- **Basic Usage (Move):** `mv file.txt /path/to/new_location/`
	- **Basic Usage (Rename):** `mv old_name.txt new_name.txt`
	- **Advanced Usage:**
		- `mv -i old_file.txt new_file.txt`: Prompts before overwriting existing files.
		- `mv -u source_file.txt destination_file.txt`: Moves only when the source is newer than the destination or when the destination file is missing.
- **`rmdir` (Remove Empty Directories):**
	- **Purpose:** Deletes empty directories.
	- **Basic Usage:** `rmdir empty_folder`
	- **Caution:** `rmdir` will only work if the directory is completely empty.
	- **Related:** `rm -r` (for removing non-empty directories and their contents).
- **`rm` (Remove Files or Directories):**
	- **Purpose:** Deletes files and/or directories. This command is very powerful and should be used with extreme caution as deleted files are generally not recoverable.
	- **Basic Usage:** `rm file_to_delete.txt`
	- **Advanced Usage:**
		- `rm -r folder_to_delete/`: Recursively deletes a directory and its entire contents (use with extreme care!).
		- `rm -f file_to_delete.txt`: Forces deletion without prompting (even if file is write-protected). Use with extreme caution.
		- `rm -i file_to_delete.txt`: Prompts before every deletion (interactive mode).
		- `rm *.txt`: Deletes all files with a `.txt` extension in the current directory.
		- `rm -rf /`: **NEVER RUN THIS COMMAND!** This command recursively and forcefully deletes the entire root directory, effectively destroying your operating system. It's often referred to as the "destroy your system" command.
