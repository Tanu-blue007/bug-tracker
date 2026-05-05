# bug-tracker
AI-powered intelligent bug triage and resolution system
# AI Programs
## A* Algorithm in C++

```cpp
#include <iostream>
using namespace std;
#define MAX 10
int graph[MAX][MAX];
int h[MAX];
int n;

void aStar(int start, int goal) {
    int visited[MAX] = {0};
    int current = start;

    cout << "Path: " << current;

    while(current != goal) {
        visited[current] = 1;

        int minCost = 999, next = -1;

        for(int i = 0; i < n; i++) {
            if(graph[current][i] != 0 && visited[i] == 0) {
                int cost = graph[current][i] + h[i];

                if(cost < minCost) {
                    minCost = cost;
                    next = i;
                }
            }
        }

        if(next == -1) {
            cout << "\nNo path found!";
            return;
        }

        current = next;
        cout << " -> " << current;
    }
}

## Explanation

This program implements a simplified A* algorithm.

Formula used:
f(n) = g(n) + h(n)

* g(n): cost from current node
* h(n): heuristic value

At each step, the node with minimum cost is selected until the goal is reached.
```
#bfs 
```
#include<bits/stdc++.h>
using namespace std;

void bfs(int start, vector<vector<int>>& adj, int n){
     vector<bool> visited(n, false);
     queue<int> q;

     q.push(start);
     visited[start] = true;

     while(!q.empty()){
          int node = q.front();
          q.pop();

          cout << node << " ";

          for(int neighbor : adj[node]){
               if(!visited[neighbor]){
                    visited[neighbor] = true;
                    q.push(neighbor);
               }
          }
     }
}

int main(){
     // int n = 5; // number of nodes
     // vector<vector<int>> adj(n);

     // // Graph edges
     // adj[0] = {1, 2};
     // adj[1] = {0, 3, 4};
     // adj[2] = {0};
     // adj[3] = {1};
     // adj[4] = {1};

     // cout << "BFS Traversal: ";
     // bfs(0, adj, n);

     int n, e;
     cout << "Enter number of nodes: ";
     cin >> n;

     cout << "Enter number of edges: ";
     cin >> e;

     vector<vector<int>> adj(n);

     cout << "Enter edges (u v):\n";
     for (int i = 0; i < e; i++) {
          int u, v;
          cin >> u >> v;
          adj[u].push_back(v);
          adj[v].push_back(u); // remove this line for directed graph
     }

     int start;
     cout << "Enter starting node: ";
     cin >> start;

     cout << "BFS Traversal: ";
     bfs(start, adj, n);
     return 0;

}
```

#dfs
```
#include <iostream>
#include <vector>
using namespace std;

void dfs(int node, vector<vector<int>>& adj, vector<bool>& visited) {
    visited[node] = true;
    cout << node << " ";

    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            dfs(neighbor, adj, visited);
        }
    }
}

int main() {
//     int n = 5;
//     vector<vector<int>> adj(n);

//     // Graph edges
//     adj[0] = {1, 2};
//     adj[1] = {0, 3, 4};
//     adj[2] = {0};
//     adj[3] = {1};
//     adj[4] = {1};

//     vector<bool> visited(n, false);

//     cout << "DFS Traversal: ";
//     dfs(0, adj, visited);
     int n, e;
     cout << "Enter number of nodes: ";
     cin >> n;

     cout << "Enter number of edges: ";
     cin >> e;

     vector<vector<int>> adj(n);
     vector<bool> visited(n, false);

     cout << "Enter edges (u v):\n";
     for (int i = 0; i < e; i++) {
          int u, v;
          cin >> u >> v;
          adj[u].push_back(v);
          adj[v].push_back(u); 
     }

     int start;
     cout << "Enter starting node: ";
     cin >> start;

     cout << "DFS Traversal: ";
     dfs(start, adj, visited);

     return 0;
}

// ------------ dfs using stack -----------------
// #include <iostream>
// #include <vector>
// #include <stack>
// using namespace std;

// void dfs_iterative(int start, vector<vector<int>>& adj) {
//     int n = adj.size();
//     vector<bool> visited(n, false);
//     stack<int> st;

//     st.push(start);

//     while (!st.empty()) {
//         int node = st.top();
//         st.pop();

//         if (!visited[node]) {
//             visited[node] = true;
//             cout << node << " ";

//             // Push neighbors (reverse order for same output as recursive)
//             for (int i = adj[node].size() - 1; i >= 0; i--) {
//                 int neighbor = adj[node][i];
//                 if (!visited[neighbor]) {
//                     st.push(neighbor);
//                 }
//             }
//         }
//     }
// }

// int main() {
//     int n = 5;
//     vector<vector<int>> adj(n);

//     adj[0] = {1, 2};
//     adj[1] = {0, 3, 4};
//     adj[2] = {0};
//     adj[3] = {1};
//     adj[4] = {1};

//     cout << "DFS (Iterative): ";
//     dfs_iterative(0, adj);

//     return 0;
// }
```
```
3. Logic / Truth Table
#include <iostream>
using namespace std;

int main() {
    int A, B;

    cout << "A B | AND OR\n";

    for(A=0;A<=1;A++) {
        for(B=0;B<=1;B++) {
            cout << A << " " << B << " | "
                 << (A&&B) << "   "
                 << (A||B) << endl;
        }
    }
}
```
```4. Prolog Programs
✅ Family Relationship
parent(john, mary).
parent(mary, sam).

grandparent(X, Z) :- parent(X, Y), parent(Y, Z).
✅ Factorial
factorial(0,1).

factorial(N,F):-
    N>0,
    N1 is N-1,
    factorial(N1,F1),
    F is N*F1.

✅ Path Finding
edge(a,b).
edge(b,c).
edge(c,d).

path(X,Y):- edge(X,Y).
path(X,Y):- edge(X,Z), path(Z,Y).
```
