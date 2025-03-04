# Explanation of FCFS Scheduling Code in C

## Overview
This document provides a line-by-line explanation of the **First Come First Serve (FCFS) Scheduling** code written in C. The program calculates **Waiting Time (WT)** and **Turnaround Time (TAT)** for a set of processes based on their burst times.

## Code Explanation
### **1. Header File Inclusion**
```c
#include <stdio.h>
```
- Includes the standard input-output library to use functions like `printf()` and `scanf()`.

### **2. Main Function**
```c
int main()
```
- The program execution starts from the `main()` function.

### **3. Variable Declarations**
```c
int bt[20], wt[20], tat[20], i, n;
float wtavg, tatavg;
```
- `bt[20]`: Stores Burst Time (BT) for processes.
- `wt[20]`: Stores Waiting Time (WT) for processes.
- `tat[20]`: Stores Turnaround Time (TAT) for processes.
- `i, n`: `i` is used for loops, `n` stores the number of processes.
- `wtavg, tatavg`: Stores average WT and TAT.

### **4. Taking User Input for Number of Processes**
```c
printf("\nEnter the number of processes -- ");
scanf("%d", &n);
```
- Prompts the user to enter the number of processes.

### **5. Taking Burst Time Input**
```c
for (i = 0; i < n; i++)
{
    printf("\nEnter Burst Time for Process %d -- ", i);
    scanf("%d", &bt[i]);
}
```
- Loops through `n` processes.
- Accepts burst time input for each process.

### **6. Initializing WT and TAT for the First Process**
```c
wt[0] = wtavg = 0;
tat[0] = tatavg = bt[0];
```
- The first process has **0 waiting time**.
- Its turnaround time is equal to its burst time.

### **7. Calculating WT and TAT for Remaining Processes**
```c
for (i = 1; i < n; i++)
{
    wt[i] = wt[i - 1] + bt[i - 1];
    tat[i] = tat[i - 1] + bt[i];
    wtavg = wtavg + wt[i];
    tatavg = tatavg + tat[i];
}
```
- **Waiting Time Formula:**
  ```c
  wt[i] = wt[i - 1] + bt[i - 1];
  ```
  - The waiting time of the current process is the waiting time of the previous process plus the previous process's burst time.
- **Turnaround Time Formula:**
  ```c
  tat[i] = tat[i - 1] + bt[i];
  ```
  - The turnaround time of the current process is the turnaround time of the previous process plus its burst time.
- The total WT and TAT are summed to calculate averages.

### **8. Displaying Process Details**
```c
printf("\t PROCESS \tBURST TIME \t WAITING TIME\t TURNAROUND TIME\n");
for (i = 0; i < n; i++)
    printf("\n\t P%d \t\t%d \t\t%d \t\t %d", i, bt[i], wt[i], tat[i]);
```
- Prints the Process ID, Burst Time, Waiting Time, and Turnaround Time.

### **9. Calculating and Displaying Averages**
```c
printf("\nAverage Waiting Time -- %f", wtavg / n);
printf("\nAverage Turnaround Time %f", tatavg / n);
```
- Computes and prints the **Average Waiting Time** and **Average Turnaround Time**.

## Example Execution
### **Input:**
```
Enter the number of processes -- 3
Enter Burst Time for Process 0 -- 5
Enter Burst Time for Process 1 -- 3
Enter Burst Time for Process 2 -- 8
```
### **Output:**
```
PROCESS    BURST TIME    WAITING TIME    TURNAROUND TIME
   P0         5              0                5
   P1         3              5                8
   P2         8              8               16

Average Waiting Time -- 4.333333
Average Turnaround Time 9.666667
```

## Summary
- The **first process always has 0 waiting time**.
- **FCFS is non-preemptive**, meaning once a process starts execution, it runs until completion.
- The order of execution depends on the input burst times.

## Author
- [CodeWithTanim](https://github.com/CodeWithTanim)
- [Arif](https://github.com/Md-Arif-Ul-Islam)
- [Kaliya-Network](https://github.com/Kaliya-Network/)