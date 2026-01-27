# Core Components of Linux (Simple & Practical Notes)

Linux may look complex at first, but at its core it is a well-structured system where every part has a clear role. These notes explain the main components of Linux in a simple and practical way.

---

## 1. Kernel – The Heart of Linux

The kernel is the core of the Linux operating system. It is always running and controls everything in the system.

### What the kernel does:
- Manages CPU scheduling
- Controls memory (RAM)
- Handles processes
- Communicates with hardware using device drivers
- Prevents conflicts between running programs

Linux uses a **monolithic kernel**, which means most services run inside the kernel for better performance.

**Example:**  
When you open a file, the kernel finds the data on disk, loads it into memory, and sends it to the application.

---

## 2. User Space – Where Applications Run

User space is where normal programs execute.

It includes:
- Applications (vim, docker, chrome)
- Shells (bash, zsh)
- System utilities (ls, ps, top)
- System libraries (glibc)

Programs in user space cannot directly access hardware. They must request the kernel.

**Why this matters:**  
If an application crashes, the kernel remains safe and the system continues running.

---

## 3. System Libraries – The Middle Layer

System libraries help applications interact with the kernel without knowing its internal details.

### Key points:
- Provide reusable functions
- Reduce developer effort
- Improve portability across Linux systems

The most important system library is **glibc**.

**Example flow:**


