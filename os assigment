#include <stdio.h>
#include <string.h>

int main() {
    int n, i;
    int completed = 0, time = 0;
    float total_wt = 0, total_tat = 0;

    printf("Enter number of processes:\n");
    scanf("%d", &n);

    char pid[n][10];
    int at[n], bt[n], pr[n];
    int wt[n], tat[n], ct[n];
    int done[n];

    for(i = 0; i < n; i++)
        done[i] = 0;

    printf("Enter PID AT BT PR:\n");
    for(i = 0; i < n; i++) {
        scanf("%s %d %d %d", pid[i], &at[i], &bt[i], &pr[i]);
    }

    while(completed < n) {
        int idx = -1;
        int highest_pr = 9999;

        for(i = 0; i < n; i++) {
            if(at[i] <= time && done[i] == 0) {
                if(pr[i] < highest_pr) {
                    highest_pr = pr[i];
                    idx = i;
                }
            }
        }

        if(idx != -1) {
            time += bt[idx];
            ct[idx] = time;

            tat[idx] = ct[idx] - at[idx];
            wt[idx] = tat[idx] - bt[idx];

            total_wt += wt[idx];
            total_tat += tat[idx];

            done[idx] = 1;
            completed++;
        } 
        else {
            time++;
        }
    }

    printf("\nWaiting Time:\n");
    for(i = 0; i < n; i++) {
        printf("%s %d\n", pid[i], wt[i]);
    }

    printf("\nTurnaround Time:\n");
    for(i = 0; i < n; i++) {
        printf("%s %d\n", pid[i], tat[i]);
    }

    printf("\nAverage Waiting Time: %.2f\n", total_wt/n);
    printf("Average Turnaround Time: %.2f\n", total_tat/n);

    return 0;
}
