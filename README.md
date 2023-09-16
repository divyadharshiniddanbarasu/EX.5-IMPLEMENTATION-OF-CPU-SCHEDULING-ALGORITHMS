Aim:

To implement the first come first serve scheduling algorithm

Description:

Scheduling Criteria

• CPU utilization: We want to keep the CPU as busy as possible. CPU utilization may
range from 0 to 100 percent. In a real system, it should range from 40 percent (for a
lightly loaded system) to 90 percent (for a heavily used system).

• Throughput: If the CPU is busy executing processes, then work is being done. One
measure of work is the number of processes completed per time unit, called
throughput. For long processes, this rate may be 1 process per hour; for short
transactions, throughput might be 10 processes per second.

• Turnaround time: The interval from the time of submission of a process to the time
of completion is the turnaround time. Turnaround time is the sum of the periods spent
waiting to get into memory, waiting in the ready queue, executing on the CPU, and
doing I/O.

• Waiting time: Waiting time is the sum of the periods spent waiting in the ready
queue.

• Response time: In an interactive system, turnaround time may not be the best criterion.
Another measure is the time from the submission of a request until the first response is
produced. This measure, called response time, is the amount of time it takes to start
responding, but not the time that it takes to output that response.
First-Come, First-Served Scheduling

The process that requests the CPU first is allocated the CPU first. The implementation of the
FCFS policy is easily managed with a FIFO queue. The average waiting time under the FCFS
policy, however, is often quite long.

Example: Process Burst Time
P1 24

P2 3

P3 3

If the processes arrive in the order PI, P2, P3, and are served in FCFS order, we get the result
shown in the following
Gantt chart:
Algorithm:
1. Start the process
2. Get the number of processes to be inserted
3. Get the value for burst time of each process from the user
4. Having allocated the burst time(bt) for individual processes , Start with the first
process from its initial position let other process to be in queue
5. Calculate the waiting time(wt) and turnaround time(tat) as
6. Wt(pi) = wt(pi-1) + tat(pi-1) (i.e. wt of current process = wt of previous process + tat of
previous process)
7. tat(pi) = wt(pi) + bt(pi) (i.e. tat of current process = wt of current process + bt of
current process)
8. Calculate the total and average waiting time and turnaround time
9. Display the values
10. Stop the process
. 

Program:

#include<stdio.h>

int main()

{

int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float

avg_wt,avg_tat;

printf("Enter number of process:");

scanf("%d",&n);

printf("\nEnter Burst Time:\n");

for(i=0;i<n;i++)

{

printf("p % d:",i+1);

scanf("%d",&bt[i]);

p[i]=i+1; //contains process number

}

wt[0]=0; //waiting time for first process will be zero

//calculate waiting time

for(i=1;i<n;i++)

{

wt[i]=0;

for(j=0;j<i;j++)

wt[i]+=bt[j];

total+=wt[i];

}

avg_wt=(float)total/n; //average waiting time

total=0;

printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");

for(i=0;i<n;i++)

{

tat[i]=bt[i]+wt[i]; //calculate turnaround time

total+=tat[i];

printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);

}

avg_tat=(float)total/n; //average turnaround time

printf("\n\nAverage Waiting Time=%f",avg_wt);

printf("\nAverage Turnaround Time=%f\n",avg_tat);

}

'''
Output:

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/2aaa84d2-924d-40ff-830b-9aea906d2a3e)

Result:

Thus, the first come first serve scheduling algorithm is implemented successfully.
