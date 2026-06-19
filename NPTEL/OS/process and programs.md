🖥️ Operating Systems - Revision Notes

🎯 Big Idea

Program vs Process

📄 Program

- Just a file on disk
- Not running

🏃 Process

- Program that is currently running
- Loaded into RAM

Memory Trick

Program + Execution = Process

---

🧠 Process Memory Layout

+----------------+
| Text           |
+----------------+
| Data           |
+----------------+
| Heap           |
+----------------+
| Stack          |
+----------------+

---

📜 Text Section

Contains:

- Instructions
- Functions
- Executable code

Remember

Text = What to do

---

📦 Data Section

Contains:

- Global variables
- Static variables

Remember

Data = Permanent variables

---

🏗️ Heap

Contains:

- Dynamic memory
- malloc()
- new

Remember

Heap = Extra memory requested while running

---

📚 Stack

Contains:

- Local variables
- Function call information

Remember

Stack = Current work area

---

📋 Process State

Managed by OS.

Contains:

- Registers
- Open files
- Process information

Remember

State = Process status card

---

🔐 User Space vs Kernel Space

+--------------------+
| Kernel Space       |
+--------------------+
| User Space         |
+--------------------+

User Space 👨‍💻

- Applications run here

Kernel Space 👑

- Operating System runs here

Golden Rule

Kernel → Can access User

User → Cannot access Kernel

Why?

🛡️ Protection

Without protection:

User program → OS crash 😵

---

☎️ System Calls

Problem:

User programs cannot directly use OS resources.

Solution:

System Calls

Examples:

open()
read()
write()
close()

Remember

System Call = Asking OS for help

---

⚡ Trap Mechanism

When system call happens:

Program
   ↓
System Call
   ↓
Trap
   ↓
Kernel Mode
   ↓
OS Service
   ↓
Return
   ↓
User Mode

Memory Trick

🚪 Trap = Door to the Kernel

---

🔄 Function Call vs System Call

Normal Function Call

main()
  ↓
foo()

✅ User Space only

❌ No mode switch

---

System Call

write()

✅ Trap occurs

✅ Kernel Mode entered

Remember

Function Call = Same world

System Call = User world → OS world

---

💾 File System Abstraction

Storage can be:

- SSD
- HDD
- USB
- Memory Card

Program does not care.

OS hides everything.

Program simply uses:

open()
read()
write()

Remember

OS hides complexity

Keyword

🎭 Abstraction

---

🏢 Monolithic Kernel

Everything together.

Memory Manager
File System
Drivers
Networking
Scheduler

All inside kernel.

Advantages

⚡ Fast

Direct communication

Disadvantages

😵 Large

😵 Complex

Remember

Monolithic = One Big Family

Examples:

- Linux
- xv6

---

🧩 Microkernel

Small kernel.

Services run separately.

Communication through IPC.

Kernel
  ↓
 IPC
  ↓
Services

Advantages

✅ Modular

✅ Easier maintenance

✅ Better isolation

Disadvantages

🐢 Slower

IPC overhead

Remember

Microkernel = Small Boss + Many Workers

---

🚀 Super Fast Revision

Program + Execution = Process

Text  → Instructions

Data  → Global / Static Variables

Heap  → Dynamic Memory

Stack → Local Variables

State → Process Information

User Space → Applications

Kernel Space → OS

System Call → Ask OS

System Call
→ Trap
→ Kernel Mode
→ Service
→ Return

Monolithic → Fast

Microkernel → Modular

---

🎯 Exam Recall Sheet

Program = Stored

Process = Running

Text = Code

Data = Globals

Heap = Dynamic

Stack = Local

Trap = Enter Kernel

System Call = Ask OS

Monolithic = Fast

Microkernel = Modular

One-Line Summary

🧠

A process runs in User Space, uses System Calls to ask the OS for help, enters Kernel Mode through a Trap, and the OS performs the requested service.