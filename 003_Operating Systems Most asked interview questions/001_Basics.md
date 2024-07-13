

### Explain about Computer and its components 
> - A computer is an electronic device that can perform a variety of tasks by executing programmed instructions. These tasks can include calculations, data processing, and  
> automated reasoning.
> - Computers are composed of hardware and software components, where the hardware refers to the physical parts, and the software includessystem software( operating system (OS))  and application software that runs on it.
> Application software performs specific tasks for the user.
> System software operates and controls the computer system and provides a platform to run application software.
>
>  - ![image](https://github.com/user-attachments/assets/1f664c92-843c-417f-bd81-9cac50091729)

### Describe the relationship between all computer components.
>The components of a computer system work together in an interconnected and interdependent manner. This collaboration ensures the smooth operation and functionality of the computer. Here's an overview of how these components relate to each other:
> The user interacts with application programs, which in turn rely on the operating system to interact with the computer hardware. The operating system serves as an intermediary, managing resources and providing a stable environment for applications to run.
>
> - ![image](https://github.com/user-attachments/assets/376bf0ea-dde3-4441-8456-a332c0e063c5)


### Explain the Operating system, its goals & Functions.
> An operating system is a system software that manages all the resources of a computer system, both hardware and software and provides an environment in which the user can execute their programs in a convenient and efficient manner by hiding the underlying complexity of the hardware and acting as a resource manager.
> **OS Goals**
> The primary goals of an operating system are maximum CPU utilization, less process starvation, and higher priority job execution.
> **OS Functions**
> An operating system performs several functions:
> - Access to the computer hardware.
> - Acts as an interface between the user and the computer hardware.
> - Manages resources (memory, devices, files, security, processes, etc.) through arbitration.
> - Hides the underlying complexity of the hardware through abstraction.
> - Facilitates the execution of application programs by providing isolation and protection.

### What are some potential issues if there were no operating system?
> 1. Bulky and complex applications, as hardware interaction code must be included in the application's code base.
> 2. Resource exploitation by a single application.
> 3. No memory protection.

### What are the types of operating systems mentioned?
>
> - ![image](https://github.com/user-attachments/assets/56648d3c-327b-4443-9689-da20fadfd775)
>
> **Single process OS**
> - A single-process operating system allows only one process to execute at a time from the ready queue. This is the oldest type of operating system.
>
> **Batch processing OS**
>- In a batch-processing operating system, the user prepares their job using punch cards and submits it to the computer operator. The operator collects jobs from different  
   users and sorts them into batches based on similar needs. These batches are then submitted to the processor one by one, with all jobs in a batch being executed together.  
   However, this system has several disadvantages. It does not allow for setting priorities if a job has higher importance, which can lead to starvation if a batch takes too 
   long to complete. Additionally, the CPU may become idle during I/O operations.
> - ![image](https://github.com/user-attachments/assets/e27d73a9-7f67-4b6c-b4f0-5fe8af2b8ac9)
>
> **Multiprogramming OS**
>A multiprogramming operating system increases CPU utilization by keeping multiple jobs (code and data) in memory, ensuring that the CPU always has a job to execute if another job gets busy with I/O operations. This system involves a single CPU and utilizes context switching for processes, where the switch occurs when the current process goes into the wait state. As a result, the CPU's idle time is significantly reduced.
>
> **Multitasking OS**
>Multitasking is a logical extension of multiprogramming that involves a single CPU with the capability to run more than one task simultaneously. It utilizes context-switching and time-sharing techniques to manage multiple tasks, leading to increased responsiveness and further reduced CPU idle time.
>
>**Multiprograming OS**
>A multiprogramming operating system offers several advantages, including the use of more than one CPU in a single computer, which increases reliability as other CPUs can continue working if one fails. This setup results in better throughput and reduces process starvation, as multiple CPUs can handle additional processes if one CPU is busy with a particular task.


### Describe a distributed operating system.

> A distributed operating system manages many resources, including multiple CPUs, memory, GPUs, etc. It features:
> - Loosely connected autonomous, interconnected computer nodes
> - A collection of independent, networked, communicating, and physically separate computational nodes

### What is a real-time operating system and where is it used?

> A real-time operating system (RTOS) ensures error-free computations within tight time boundaries. It is used in scenarios like air traffic control systems and robots.

