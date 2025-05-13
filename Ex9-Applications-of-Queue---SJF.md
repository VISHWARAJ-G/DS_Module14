# Ex9 Applications of Queue - SJF
## DATE: 13-03-2025
## AIM:
To incorporate the code to calculate the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
## Algorithm
1. Start
2. Input number of processes and their burst times
3. Sort burst times in ascending order along with process IDs
4. Calculate waiting time for each process 
5. Compute total and average waiting time
6. End

## Program:
```
/*
Program to find the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
Developed by: Vishwaraj G.
RegisterNumber: 212223220125 
*/
#include <stdio.h>

void sortByBurstTime(int pid[], int bt[], int n) {
    int temp;
    for(int i=0; i<n-1; i++) {
        for(int j=0; j<n-i-1; j++) {
            if(bt[j] > bt[j+1]) {
                temp = bt[j];
                bt[j] = bt[j+1];
                bt[j+1] = temp;

                temp = pid[j];
                pid[j] = pid[j+1];
                pid[j+1] = temp;
            }
        }
    }
}

int main() {
    int n;
    printf("Enter number of processes: ");
    scanf("%d", &n);

    int pid[n], bt[n], wt[n];
    float total_wt = 0, avg_wt;

    for(int i = 0; i < n; i++) {
        pid[i] = i + 1;
        printf("Enter Burst Time for Process %d: ", pid[i]);
        scanf("%d", &bt[i]);
    }

    sortByBurstTime(pid, bt, n);

    wt[0] = 0;

    for(int i = 1; i < n; i++) {
        wt[i] = wt[i-1] + bt[i-1];
        total_wt += wt[i];
    }

    avg_wt = total_wt / n;

    printf("\nProcess\tBurst Time\tWaiting Time\n");
    for(int i = 0; i < n; i++) {
        printf("P%d\t%d\t\t%d\n", pid[i], bt[i], wt[i]);
    }

    printf("\nTotal Waiting Time: %.2f", total_wt);
    printf("\nAverage Waiting Time: %.2f\n", avg_wt);

    return 0;
}


```

## Output:
![image](https://github.com/user-attachments/assets/63a77366-77a1-4a1f-924d-c73e2484de2f)

## Result:
Thus, the code to calculate the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm is implemented successfully.
