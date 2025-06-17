# Projects related to DOM
Here's a very short C program to implement Breadth-First Search (BFS):

#include <stdio.h>
#include <stdlib.h>

#define V 5
int adj[V][V] = {{0, 1, 0, 1, 0}, {1, 0, 1, 0, 1}, {0, 1, 0, 1, 0}, {1, 0, 1, 0, 1}, {0, 1, 0, 1, 0}};
int queue[V], front = 0, rear = 0, visited[V] = {0};

void bfs(int start) {
    visited[start] = 1;
    queue[rear++] = start;
    
    while (front != rear) {
        int node = queue[front++];
        printf("%d ", node);

        for (int i = 0; i < V; i++) {
            if (adj[node][i] && !visited[i]) {
                visited[i] = 1;
                queue[rear++] = i;
            }
        }
    }
}

int main() {
    bfs(0); // Start BFS from node 0
    return 0;
}

Output:

0 1 3 2 4

The 0/1 Knapsack Problem cannot be correctly solved using a greedy approach in general — greedy only works for the fractional knapsack. But if you still want a very short C code for a greedy-style approximate solution to 0/1 knapsack, here’s one:

⚠️ Note:

This does not always give the optimal solution (only correct for fractional knapsack).


---

✅ Very Short C Program (Greedy Approximation for 0/1 Knapsack)

#include <stdio.h>

int main() {
    int w[] = {10, 20, 30}, v[] = {60, 100, 120}, n = 3, W = 50, i, j;
    float r[3], temp; int total = 0;

    for (i = 0; i < n; i++) r[i] = (float)v[i]/w[i];
    for (i = 0; i < n-1; i++)
        for (j = i+1; j < n; j++)
            if (r[i] < r[j]) {
                temp = r[i]; r[i] = r[j]; r[j] = temp;
                temp = v[i]; v[i] = v[j]; v[j] = temp;
                temp = w[i]; w[i] = w[j]; w[j] = temp;
            }

    for (i = 0; i < n && W >= w[i]; i++) {
        W -= w[i];
        total += v[i];
    }

    printf("Approx Max Value: %d\n", total);
    return 0;
}


---

✅ Output:

Approx Max Value: 160

✅ For exact solution of 0/1 knapsack, use Dynamic Programming. Let me know if you want that too in a short format.




