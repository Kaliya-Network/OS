# First Come First Serve (FCFS) CPU Scheduling Algorithm

## 🎯 AIM
To write a C program to simulate the CPU scheduling algorithm **First Come First Serve (FCFS)**.

## 📜 DESCRIPTION
To calculate the **average waiting time** using the FCFS algorithm:
- The waiting time of the first process is set to **zero**.
- The waiting time of the second process is the **burst time** of the first process.
- The waiting time of the third process is the **sum** of the burst times of the first and second processes, and so on.
- After calculating all the waiting times, the **average waiting time** is computed as the average of all waiting times.
- FCFS follows the principle: **"First come, first served"**—the process that arrives first is executed first.

## 📌 ALGORITHM
1. **Start the process**.
2. Accept the **number of processes** in the ready queue.
3. For each process in the ready queue, assign the **process name** and **burst time**.
4. Set the waiting time of the **first process** as `0` and its **turnaround time** as its burst time.
5. For each process in the ready queue, calculate:
   - **Waiting time**: `WT(n) = WT(n-1) + Burst Time(n-1)`
   - **Turnaround time**: `TAT(n) = WT(n) + Burst Time(n)`
6. Compute:
   - **Average Waiting Time** = `Total Waiting Time / Number of processes`
   - **Average Turnaround Time** = `Total Turnaround Time / Number of processes`
7. **Stop the process**.

## 🖥️ C PROGRAM IMPLEMENTATION
```c
#include <stdio.h>

int main() {
    int bt[20], wt[20], tat[20], i, n;
    float wtavg, tatavg;
    
    printf("\nEnter the number of processes -- ");
    scanf("%d", &n);
    
    for (i = 0; i < n; i++) {
        printf("\nEnter Burst Time for Process %d -- ", i);
        scanf("%d", &bt[i]);
    }
    
    wt[0] = wtavg = 0;
    tat[0] = tatavg = bt[0];
    
    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
        tat[i] = tat[i - 1] + bt[i];
        wtavg += wt[i];
        tatavg += tat[i];
    }
    
    printf("\n\tPROCESS\tBURST TIME\tWAITING TIME\tTURNAROUND TIME\n");
    for (i = 0; i < n; i++)
        printf("\n\tP%d\t\t%d\t\t%d\t\t%d", i, bt[i], wt[i], tat[i]);
    
    printf("\n\nAverage Waiting Time -- %f", wtavg / n);
    printf("\nAverage Turnaround Time -- %f\n", tatavg / n);
    
    return 0;
}
```

## 📥 INPUT
```
Enter the number of processes -- 3
Enter Burst Time for Process 0 -- 24
Enter Burst Time for Process 1 -- 3
Enter Burst Time for Process 2 -- 3
```

## 📤 OUTPUT
| PROCESS | BURST TIME | WAITING TIME | TURNAROUND TIME |
|---------|------------|--------------|-----------------|
| P0      | 24         | 0            | 24              |
| P1      | 3          | 24           | 27              |
| P2      | 3          | 27           | 30              |

- **Average Waiting Time**: `17.000000`
- **Average Turnaround Time**: `27.000000`

---
📌 **Note:** This program simulates FCFS CPU Scheduling, demonstrating the calculation of waiting and turnaround times effectively.
