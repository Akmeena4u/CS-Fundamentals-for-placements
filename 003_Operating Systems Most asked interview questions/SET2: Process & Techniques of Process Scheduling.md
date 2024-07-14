

### Explain the difference between programs and processes and Describe 
>  program is compiled code that is ready to execute. this resides in secondary memory
> Process is a program under execution. this resides in main memory

### How Os converts a program into a Process.
> The OS creates a process by converting a program into a process. The steps involved are:
>
> 1. **Program Loading:**
>    - The operating system loads the program's executable file from the storage into the main memory (RAM).
> 2. **Memory Allocation:**
>    - The OS allocates memory space for the process, including space for the program code, static data, runtime stack, and heap.
> 3. **Process Control Block (PCB) Creation:**
>    - The OS creates a Process Control Block (PCB) for the process, which contains metadata such as process ID, process state, CPU registers, memory limits, and priority.
> 4. **Initializing Process State:**
>    - The initial state of the process is set, typically to the "ready" state, indicating that the process is prepared to run but not yet executing.
> 5. **Loading Program Instructions and Static Data:**
>    - The instructions from the program and static data are loaded into the allocated memory space, preparing them for execution.
> 6. **Setting Up Execution Context:**
>    - The OS sets up the initial execution context, including CPU registers, program counter (PC), and stack pointer, to ensure the process can start execution properly.
> 7. **Handling IO Tasks:**
>    - The OS sets up any necessary input/output tasks or resources needed by the process.
> 8. **Adding to Scheduler:**
>    - The process is added to the scheduler's queue of ready processes, waiting for CPU time to execute.
> 9. **Handing Off Control to main() Function:**
>    - The OS hands off control to the process's main() function, initiating the execution of the program.
> 10. **Starting Execution:**
>    - The process scheduler selects the process for execution, and the CPU starts executing its instructions.
> These steps ensure that a program is properly converted into a process and managed by the operating system to perform its intended tasks.



### What is the architecture of a process?
> The architecture of a process includes several key components and structures that define how a process is managed and executed by the operating system:
>
> - **Process Control Block (PCB):** A data structure maintained by the OS containing important information about the process. The PCB includes following process attributes:
>   - Process ID (PID) - A unique identifier assigned to each process by the operating system.
>   - Process state - Indicates the current state of the process, such as new, ready, running, waiting, or terminated.
>   - Program counter (PC) - Contains the address of the next instruction to be executed.
>   - CPU registers - Include various registers used by the process for execution, such as the accumulator, index registers, and stack pointers.
>   - Memory management information - Details about the memory allocated to the process, including the base and limit registers, page tables, or segment tables.
>   - Accounting information - Includes information such as the amount of CPU used, time limits, job or process numbers, and so on.
>   - I/O status information- Includes a list of I/O devices allocated to the process and a list of open files.
>   - Priority - Indicates the priority level of the process, which can affect the scheduling of the process.
>   - User and group IDs -Identify the user and group to which the process belongs, providing the basis for permissions and access control.
>
> - **Heap Segment:** Used for dynamic memory allocation during process execution. The heap grows upwards as memory is dynamically allocated using functions like `malloc` in C or `new` in C++.
> - **Stack Segment:** Used for managing function calls and local variables. The stack grows downwards as functions are called and stack frames are created
> - **Memory Map:** A structure that maps the addresses used by the process to the physical memory addresses. This includes:
>
> - **Process States:** The possible states of a process during its lifecycle, including:
>   - New: The process is being created.
>   - Ready: The process is ready to run and waiting for CPU time.
>   - Running: The process is currently being executed by the CPU.
>   - Waiting (Blocked): The process is waiting for an event, such as I/O completion.
>   - Terminated: The process has finished execution.
>   - ![image](https://github.com/user-attachments/assets/d83db1d9-fc60-4677-bb5a-f8544788890e)
>
>
> - **I/O System:** Manages the input and output operations of the process, including file descriptors and I/O devices.
> - **Inter-Process Communication (IPC):** Mechanisms that allow processes to communicate and synchronize with each other. IPC methods include:
>   - Signals
>   - Message queues
>   - Shared memory
>   - Pipes
>   - Sockets
>
> The architecture of a process provides a framework for the operating system to manage, execute, and control processes efficiently, ensuring proper resource allocation and process interaction.

### What is the purpose of registers in the PCB?
> **Registers in the PCB store the current values of process-specific registers when a process's time slice expires. This information is used to swap out the process and later read from the PCB to write back to the CPU registers when the process is scheduled to run again. This ensures the process can resume execution from where it left off.


### Explain about Process Queues:**
> Process queues are data structures used by the operating system to manage processes based on their current state and scheduling requirements. The main types of process queues are:
> 
> - **Job Queue:**
>   - Processes in the Job Queue are in the new state. When a process is initially created, it enters the new state and is placed in the Job Queue.
>   - This queue helps the OS keep track of all processes that exist in the system, whether they are active or not.
>   - These processes are present in secondary memory. The Job Scheduler, also known as the Long Term Scheduler (LTS), picks processes from this pool and loads them into memory for execution.
>   - The LTS controls the degree of multi-programming by managing the number of processes loaded into the main memory. It decides which processes in the Job Queue should be moved to the Ready Queue for execution.
> 
> - **Ready Queue:**
>   - A Ready Queue contains processes in the ready state. These processes are present in main memory.
>   - The CPU Scheduler, also known as the Short Term Scheduler (STS), picks processes from the Ready Queue and dispatches them to the CP
>   - The STS is responsible for selecting which ready process should execute next, optimizing CPU utilization, and managing process transitions between the ready and running states.
>
> - **Device (I/O) Queues:**
>   - Each I/O device has its own queue, containing processes waiting for I/O operations to complete.
>   - When a process requests an I/O operation, it is placed in the corresponding device queue until the I/O operation is completed.
> 
> - **Wait Queue (Blocked Queue):**
>   - Contains processes that are waiting for a specific event to occur, such as the completion of an I/O operation or the availability of a resource.
>   - These processes cannot proceed until the event they are waiting for happens.

### What is a Dispatcher?
> A Dispatcher is a module of the OS that gives control of the CPU to a process selected by the Short Term Scheduler (STS).



### What is Swapping?
> - Swapping is a mechanism in which a process can be swapped temporarily out of main memory (or moved) to secondary storage (disk) and make that memory available to other processes. At some later time, the system swaps back the process from secondary storage to main memory.
> - By temporarily moving processes to secondary storage, the system can better manage memory allocation and ensure that active processes have sufficient memory to execute.
> - ![image](https://github.com/user-attachments/assets/3e2832a6-1247-4844-893a-225dbb5113f0)


### What role does the Medium Term Scheduler (MTS) play in Swapping?
> In a time-sharing system, the Medium Term Scheduler (MTS) is responsible for swapping processes in and out of memory.
> The MTS removes processes from memory to reduce the degree of multi-programming and reintroduces them into memory later, allowing their execution to continue where it left off.


### What is Context-Switching?
> Context-switching is the process of switching the CPU from one process to another, which requires performing a state save of the current process and a state restore of a different process.
> This process involves the kernel saving the context of the old process in its Process Control Block (PCB) and loading the saved context of the new process scheduled to run.
> Context-switching is considered pure overhead because the system does no useful work while switching.
> The time and resources spent saving and restoring process states do not contribute to the execution of user-level processes.

###  What is an Orphan Process?
> An Orphan Process is a process whose parent process has been terminated and it is still running.
> Orphan Processes are adopted by the init process, which is the first process of the operating system.

### What is a Zombie Process?
> A Zombie Process is a process whose execution is completed but it still has an entry in the process table.
> Zombie processes typically occur for child processes when the parent process still needs to read its child's exit status.
> Zombie Processes are eliminated from the process table once the parent process reads the exit status of the child process using the wait system call. This process is known as reaping the zombie process.

### Why do Zombie Processes occur?
> Zombie Processes occur because the parent process may call wait() on the child process for a longer time duration, and the child process terminates much earlier.**  
> The entry in the process table can only be removed after the parent process reads the exit status of the child process, so the child process remains a zombie until this occurs.

---


### What is CPU Scheduling in Operating Systems ?
> CPU scheduling is a key function of the operating system that determines which process should run on the CPU at any given time. It aims to maximize CPU utilization and system responsiveness by efficiently managing the execution of multiple processes.
>The goals of CPU scheduling include maximizing CPU utilization, minimizing turnaround time (TAT), minimizing wait time, minimizing response time, and maximizing the throughput of the system

### What are the Types of Scheduling?
> **Non-Preemptive Scheduling** Non-Preemptive Scheduling allows a process to keep the CPU until it voluntarily releases it by terminating or switching to a waiting state. This can lead to starvation of short burst time processes and lower CPU utilization.
> **Preemptive Scheduling** Preemptive Scheduling involves taking the CPU away from a process after a time quantum expires or when it switches to a wait-state, reducing starvation and increasing CPU utilization.**

### Define all Cpu Scheduling Metrics in OS?
> **Throughput** Throughput refers to the number of processes completed per unit of time, indicating the system's efficiency in handling processes.
> **Arrival Time (AT)** Arrival Time is the time when a process arrives at the ready queue, while Burst Time (BT) is the time required by the process for its execution.
> **Turnaround Time (TAT)** Turnaround Time is the total time taken from the arrival of a process in the ready state to its completion. It is calculated as Completion Time (CT) minus Arrival Time (AT).
> **Wait Time (WT)** Wait Time  is the total time a process spends waiting in the ready queue for CPU execution, calculated as TAT minus Burst Time (BT).  
> **Response Time** Response Time is the time duration between a process entering the ready queue and receiving CPU execution for the first time.**




### Explain all Scheduling Algorithms:?
> There are various scheduling algorithms used by operating systems, each with its own characteristics and suitability for different scenarios:
> 
> **First-Come, First-Served (FCFS):**
> - FCFS is one of the simplest scheduling algorithms used by operating systems to manage process execution on the CPU. It follows the principle that the process that arrives first is served first
> - it is Non-preemptive means Once a process starts executing, it continues until it completes or blocks for I/O.
> - **CONS: Convoy effect** The convoy effect occurs in scheduling algorithms like FCFS when a long-running CPU-bound process holds up the CPU, causing short processes that arrive later to wait extensively. This results in a convoy-like formation, where short processes (akin to smaller vehicles) are stuck behind a long process (akin to a large vehicle).
> 
>---
> - **Shortest Job Next (SJN) / Shortest Job First (SJF):**
> - SJF is a CPU scheduling algorithm that selects the process with the smallest next CPU burst time to execute first. It aims to minimize the average waiting time for processes and optimize system throughput by prioritizing shorter jobs over longer ones.
>   
> - **SJF Non-Primptive** In non-preemptive SJF scheduling, once a process starts executing, it continues until it finishes or blocks for I/O.
> - **Implementation:** Processes are sorted in the ready queue based on their burst time (time required to complete execution). The shortest job among the ready processes is chosen for execution.
> - **Pros:** Minimizes average waiting time by prioritizing shorter jobs over longer ones.
> - **Cons:** May lead to starvation for longer processes if shorter processes frequently arrive.
> 
> -**SJF Primptive**  allows the scheduler to preempt a currently running process if a new process with a shorter burst time (remaining time to complete) arrives.
> -**Implementation:** The scheduler compares the burst times of the currently running process and the incoming process. If the new process has a shorter burst time, it preemptively switches execution to the new process.
> **Pros:** Less starvation
> **Cons** No Convoy effect
>
> ---
> - **Priority Scheduling:** Priority scheduling is a CPU scheduling algorithm where each process is assigned a priority. The scheduler selects the process with the highest priority for execution. If multiple processes have the same priority, other scheduling algorithms (like FCFS within priorities) may be used to decide the order.
> - **Preemptive and Non-preemptive:** Can be implemented in both preemptive (where a higher-priority process can interrupt a lower-priority process) and non-preemptive (where once a process starts, it runs to completion) forms.
> - Primptive scheduling May cause indefinite waiting (Starvation) for lower priority jobs. (Possibility is they won’t get executed ever). (True for both preemptive and non-preemptive versions)
> -Solution: Ageing is the solution.- Gradually increase priority of process that wait so long. E.g., increase priority by 1 every 15 minutes.
>
>---
> - **Round Robin (RR):** Round Robin (RR) is a CPU scheduling algorithm where each process is assigned a fixed time quantum or time slice. The scheduler cyclically assigns CPU time to each process in the ready queue for a predefined quantum. If a process does not finish execution within one time quantum, it is preempted and placed back in the ready queue to await its turn again.
> - ![image](https://github.com/user-attachments/assets/f858a1fe-5c8d-47af-bbdc-09f1c63c4e5b)
>
> ---
> - **Multilevel Queue Scheduling:** Multilevel Queue Scheduling is a CPU scheduling algorithm that partitions the ready queue into several separate queues, each with its own scheduling algorithm.
> - Processes are permanently assigned to one queue based on criteria such as process type, priority, or other characteristics.
> - System process: Created by OS (Highest priority) Interactive process (Foreground process): Needs user input (I/O). Batch process (Background process): Runs silently, no user input required
> - Each queue has its own scheduling algorithm. E.g., SP -> RR, IP -> RR & BP -> FCFS.
> 
> - **Multilevel Feedback Queue Scheduling:** Allows the process to move between queues. The idea is to separate processes according to the characteristics of their BT. If a process uses too much CPU time, it will be moved to lower priority queue. This scheme leaves I/O bound and interactive processes in the higher-priority queue.
> - In addition, a process that waits too much in a lower-priority queue may be moved to a higher priority queue. This form of ageing prevents starvation. 
>
> ![image](https://github.com/user-attachments/assets/0562045a-d773-4ba5-a87b-f03a29d43c03)

