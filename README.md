# CPU Scheduler

## Introduction

A CPU scheduler is a software that schedules processes for execution with the following objectives:
- Maximize CPU utilization
- Maximize throughput
- Minimize waiting time
- Minimize turnaround time
- Minimize response time
- Ensure fairness
- Balance priorities

In this project, we have implemented four standard algorithms and one innovative algorithm.

## Algorithms

### 1. First Come First Serve (FCFS)

#### Definition
FCFS (First-Come, First-Served) is the simplest CPU scheduling algorithm where the process that arrives first gets executed first.

#### Characteristics
- **Non-preemptive**: Once a process starts, it runs to completion without interruption.
- **Queue Structure**: Processes are managed in a FIFO (First-In, First-Out) queue.
- **Performance**: Can lead to the "convoy effect," causing high average waiting times.
- **Context Switches**: Minimal, as each process runs to completion.
- **Use Case**: Suitable for batch systems where execution times are known and processes can wait.

#### Example
Consider three processes with burst times:
- P1: 24 ms
- P2: 3 ms
- P3: 3 ms

Average waiting time = (0 + 24 + 27) / 3 = 17 ms

### 2. Shortest Job First (SJF)

#### Definition
SJF (Shortest Job First) selects the process with the shortest execution time to execute next.

#### Characteristics
- **Non-preemptive**: Runs to completion without interruption.
- **Optimality**: Minimizes average waiting time.
- **Queue Structure**: Managed based on burst times.
- **Performance**: Lower average waiting time but can cause "starvation" for longer processes.
- **Use Case**: Suitable where burst times can be estimated accurately.

#### Example
Consider four processes with burst times:
- P1: 6 ms
- P2: 8 ms
- P3: 7 ms
- P4: 3 ms

Average waiting time = (0 + 3 + 9 + 16) / 4 = 7 ms

### 3. Round Robin (RR)

#### Definition
Round Robin (RR) assigns a fixed time slice or quantum to each process in a cyclic order.

#### Characteristics
- **Preemptive**: Each process is interrupted when its time slice expires.
- **Time Quantum**: Crucial parameter; too short leads to excessive context switching, too long behaves like FCFS.
- **Queue Structure**: Managed in a circular queue.
- **Fairness**: Each process gets an equal share of CPU time.
- **Performance**: Good response time but higher average waiting time.
- **Context Switches**: Frequent if the time quantum is too short.
- **Use Case**: Suitable for time-sharing systems where responsiveness is critical.

#### Example
Consider three processes with burst times and a time quantum of 4 ms:
- P1: 6 ms
- P2: 8 ms
- P3: 7 ms

Average waiting time:
- P1: (0 + 8) - 4 = 4 ms
- P2: (4 + 8 + 4) - 8 = 8 ms
- P3: (8 + 7) - 12 = 3 ms
Total average waiting time = (4 + 8 + 3) / 3 = 5 ms

### 4. Shortest Job First (SJF)

#### Definition
SRJF (Shortest Remaining Job First) selects the process with the shortest execution time to execute next.

#### Characteristics
- **Preemptive**: A new process with a shorter burst time can preempt the current process.
- **Optimality**: Minimizes average waiting time.
- **Queue Structure**: Managed based on burst times.
- **Performance**: Lower average waiting time but can cause "starvation" for longer processes.
- **Context Switches**: Whenever new process comes it take place..
- **Use Case**: Suitable where burst times can be estimated accurately.

#### Example
Consider four processes with burst times:
- P1: 6 ms
- P2: 8 ms
- P3: 7 ms
- P4: 3 ms

Average waiting time = (0 + 3 + 9 + 16) / 4 = 7 ms

### 5. Innovative Algorithm

#### Definition
This innovative algorithm aims to reduce waiting and turnaround times significantly compared to other scheduling algorithms, including simple Round Robin.

#### Approach
- Executes the shortest job first.
- Uses a dynamic "Smart time quantum" based on the median burst time of all processes.

#### Stages
1. **Arrange**: Processes in increasing order of burst time.
2. **Calculate**: Median burst time; set as the Smart time quantum.
3. **Execute**: Allocate CPU based on the Smart time quantum until completion.

#### Advantages
- **Reduced Waiting Time**: Prioritizes shorter jobs and dynamically adjusts the time quantum.
- **Improved Turnaround Time**: Efficient handling of processes.
- **Eliminates Discrepancies**: Dynamic time quantum addresses issues with static time quanta.

#### Example
Consider four processes with burst times:
- P1: 6 ms
- P2: 8 ms
- P3: 7 ms
- P4: 3 ms

**Stage 1**: Arrange in order: P4, P1, P3, P2  
**Stage 2**: Calculate median = (6 + 7) / 2 = 6.5 (rounded to 6 ms)  
**Stage 3**: Allocate CPU as per the algorithm:

This innovative CPU scheduling algorithm ensures efficient process management, resulting in better overall performance metrics.

## Running the Scheduler

The code is in C++ and can be run through the terminal.

## Resources

- [YouTube Playlist on CPU Scheduling](https://www.youtube.com/playlist?list=PLBlnK6fEyqRitWSE_AyyySWfhRgyA-rHk)
- [Documentation](https://ravipatel1309.github.io/CPUScheduler/docs.html)
- [Linux Kernel Development (PDF)](https://www.doc-developpement-durable.org/file/Projets-informatiques/cours-&-manuels-informatiques/Linux/Linux%20Kernel%20Development,%203rd%20Edition.pdf)
- [Research on Improved Round Robin Scheduling Algorithm](https://www.researchgate.net/publication/49619229_An_Improved_Round_Robin_Schedduling_Algorithm_for_CPU_Scheduling)

