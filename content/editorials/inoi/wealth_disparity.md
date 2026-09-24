---
draft: false
title: "Wealth Disparity"
editorial:
  platform: "INOI"
  name: "Wealth Disparity"
---

{{< problem "inoi-wealth-disparity" >}}

# Solution to Wealth Disparity

## Prerequisites

You should be comfortable with trees and dynamic programming (DP).

## Understanding the problem

We have been given that there are $N$ employees in a company.
All of them have been given an integer amount of wealth.
Everyone except the head of the company has one manager.
This forms a rooted tree, where the root is the head (Mr Hojo).
$A$ is a subordinate of $B$ if $A$ appears in the subtree rooted at $B$.
We need to find employees $i$ and $j$,
so that the difference between the wealth of $i$ and $j$ is maximum.
As input, we receive an integer $N$.
This is followed by a line containing the wealth of each employee.
We call this array $a$.
The next line provides the managers of each employee.
We call this array $P$.

## Main idea

Consider the subtree rooted at a fixed vertex $i$.
We need to find $j$ such that $a[i] - a[j]$ is maximum.
Now if $a[i]$ is fixed, only $a[j]$ varies.
We need to find the minimum possible $a[j]$ for each $i$,
in order to maximize $a[i] - a[j]$.
Let $dp[i]$ be the minimum wealth of any employee in the subtree rooted at $i$.
We maintain these values for each vertex $i$.

To get such a candidate, we use dynamic programming (DP).
Each candidate represents the minimum wealth possible in each subtree.
Now the minimum wealth of a vertex could only come from either itself,
or from one of the subtrees of its children.
In particular, $dp[v]$ is the minimum of $a[v]$ and the
$dp$ values of all of its children.

Hence, while running a depth first search (DFS) algorithm,
we can compute the values while traversing upwards.
During the DFS, we first visit all the children of a vertex
and compute their $dp$ values. We use these values to compute
the $dp$ value of the current vertex.
We now have an array of length $N$ which has the candidates for each vertex.
Then we only need to find the maximum value of $a[i] - dp[i]$ over all $i$.
The time complexity of this algorithm is $\mathcal{O}(n)$.
The space complexity of this algorithm is also $\mathcal{O}(n)$.

## Worked example

Consider the following input:
```text
6
50 20 30 10 40 15
-1 1 1 2 2 3
```

The given input is described by the following image:

<svg xmlns="http://www.w3.org/2000/svg" width="838" height="251" viewBox="0 0 838 251">
  <defs>
    font: 17px monospace;
  </defs>
<path d="M384.70329681081563,74.46129924661533 C380.79911216720853,65.1767575719027 264.08663029599495,114.25479452874191 267.99081493960205,123.53933620345454" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="butt" />
<path d="M384.70329681081563,74.46129924661533 C388.2353250946857,66.07800354969045 504.7222894488424,115.15598763558751 501.1902611649723,123.53928333251238" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="butt" />
<path d="M267.99081493960205,123.53933620345454 C267.99081493960205,123.53933620345454 154.40031089723772,172.56638510419688 154.40031089723772,172.56638510419688" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="butt" />
<path d="M267.99081493960205,123.53933620345454 C264.40737248773917,131.39208796665037 372.08442561927603,180.52830606174703 375.6678680711389,172.6755542985512" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="butt" />
<path d="M501.1902611649723,123.53928333251238 C501.1902611649723,123.53928333251238 614.4941907925735,172.555668834522 614.4941907925735,172.555668834522" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="butt" />
<path d="M404.70329681081563,74.46129924661533 A20,20 0 1 1 364.70329681081563,74.46129924661533 A20,20 0 1 1 404.70329681081563,74.46129924661533 Z" fill="#71caf8" stroke="none" />
<path d="M404.70329681081563,74.46129924661533 A20,20 0 1 1 364.70329681081563,74.46129924661533 A20,20 0 1 1 404.70329681081563,74.46129924661533" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
<text x="384.70329681081563" y="75.46129924661533" style="font: 17px JB; fill: hsl(0, 0%, 10%); text-anchor: middle; dominant-baseline: middle;">1</text>
<path d="M287.99081493960205,123.53933620345454 A20,20 0 1 1 247.99081493960205,123.53933620345454 A20,20 0 1 1 287.99081493960205,123.53933620345454 Z" fill="#71caf8" stroke="none" />
<path d="M287.99081493960205,123.53933620345454 A20,20 0 1 1 247.99081493960205,123.53933620345454 A20,20 0 1 1 287.99081493960205,123.53933620345454" fill="none" stroke="hsl(0, 0%, 10%)" stroke-width="2" stroke-linecap="round" />
<text x="267.99081493960205" y="124.53933620345454" style="font: 17px JB; fill: hsl(0, 0%, 10%); text-anchor: middle; dominant-baseline: middle;">2</text>
<path d="M521.1902611649723,123.53928333251238 A20,20 0 1 1 481.1902611649723,123.53928333251238 A20,20 0 1 1 521.1902611649723,123.53928333251238 Z" fill="#71caf8" stroke="none" />
<path d="M521.1902611649723,123.53928333251238 A20,20 0 1 1 481.1902611649723,123.53928333251238 A20,20 0 1 1 521.1902611649723,123.53928333251238" fill="none" stroke="hsl(0, 0%, 10%)" stroke-width="2" stroke-linecap="round" />
<text x="501.1902611649723" y="124.53928333251238" style="font: 17px JB; fill: hsl(0, 0%, 10%); text-anchor: middle; dominant-baseline: middle;">3</text>
<path d="M174.40031089723772,172.56638510419688 A20,20 0 1 1 134.40031089723772,172.56638510419688 A20,20 0 1 1 174.40031089723772,172.56638510419688 Z" fill="#71caf8" stroke="none" />
<path d="M174.40031089723772,172.56638510419688 A20,20 0 1 1 134.40031089723772,172.56638510419688 A20,20 0 1 1 174.40031089723772,172.56638510419688" fill="none" stroke="hsl(0, 0%, 10%)" stroke-width="2" stroke-linecap="round" />
<text x="154.40031089723772" y="173.56638510419688" style="font: 17px JB; fill: hsl(0, 0%, 10%); text-anchor: middle; dominant-baseline: middle;">4</text>
<path d="M395.6678680711389,172.6755542985512 A20,20 0 1 1 355.6678680711389,172.6755542985512 A20,20 0 1 1 395.6678680711389,172.6755542985512 Z" fill="#71caf8" stroke="none" />
<path d="M395.6678680711389,172.6755542985512 A20,20 0 1 1 355.6678680711389,172.6755542985512 A20,20 0 1 1 395.6678680711389,172.6755542985512" fill="none" stroke="hsl(0, 0%, 10%)" stroke-width="2" stroke-linecap="round" />
<text x="375.6678680711389" y="173.6755542985512" style="font: 17px JB; fill: hsl(0, 0%, 10%); text-anchor: middle; dominant-baseline: middle;">5</text>
<path d="M634.4941907925735,172.555668834522 A20,20 0 1 1 594.4941907925735,172.555668834522 A20,20 0 1 1 634.4941907925735,172.555668834522 Z" fill="#71caf8" stroke="none" />
<path d="M634.4941907925735,172.555668834522 A20,20 0 1 1 594.4941907925735,172.555668834522 A20,20 0 1 1 634.4941907925735,172.555668834522" fill="none" stroke="hsl(0, 0%, 10%)" stroke-width="2" stroke-linecap="round" />
<text x="614.4941907925735" y="173.555668834522" style="font: 17px JB; fill: hsl(0, 0%, 10%); text-anchor: middle; dominant-baseline: middle;">6</text>
<path d="M405.20329681081563,31.961299246615326 L399.19898582513986,46.456988260939546 L384.70329681081563,52.461299246615326 L370.2076077964914,46.45698826093955 L364.20329681081563,31.96129924661533 L370.2076077964914,17.465610232291105 L384.70329681081563,11.461299246615326 L399.19898582513986,17.465610232291098 L405.20329681081563,31.961299246615322 Z" fill="none" stroke="hsl(10, 2%, 70%)" stroke-width="2" stroke-linecap="round" stroke-dasharray="1,4" />
<text x="384.70329681081563" y="31.961299246615326" style="font: 15px JB; fill: hsl(30, 80%, 50%); text-anchor: middle; dominant-baseline: middle;">50</text>
<path d="M288.49081493960205,81.03933620345454 L282.4865039539263,95.53502521777877 L267.99081493960205,101.53933620345454 L253.49512592527782,95.53502521777877 L247.49081493960205,81.03933620345454 L253.49512592527782,66.54364718913031 L267.99081493960205,60.53933620345454 L282.4865039539263,66.54364718913031 L288.49081493960205,81.03933620345454 Z" fill="none" stroke="hsl(10, 2%, 70%)" stroke-width="2" stroke-linecap="round" stroke-dasharray="1,4" />
<text x="267.99081493960205" y="81.03933620345454" style="font: 15px JB; fill: hsl(30, 80%, 50%); text-anchor: middle; dominant-baseline: middle;">20</text>
<path d="M521.6902611649723,81.03928333251238 L515.6859501792965,95.53497234683661 L501.1902611649723,101.53928333251238 L486.69457215064807,95.53497234683661 L480.6902611649723,81.03928333251238 L486.69457215064807,66.54359431818816 L501.1902611649723,60.53928333251238 L515.6859501792965,66.54359431818816 L521.6902611649723,81.03928333251238 Z" fill="none" stroke="hsl(10, 2%, 70%)" stroke-width="2" stroke-linecap="round" stroke-dasharray="1,4" />
<text x="501.1902611649723" y="81.03928333251238" style="font: 15px JB; fill: hsl(30, 80%, 50%); text-anchor: middle; dominant-baseline: middle;">30</text>
<path d="M174.90031089723772,130.06638510419688 L168.89599991156194,144.5620741185211 L154.40031089723772,150.56638510419688 L139.9046218829135,144.5620741185211 L133.90031089723772,130.06638510419688 L139.9046218829135,115.57069608987265 L154.40031089723772,109.56638510419688 L168.89599991156194,115.57069608987265 L174.90031089723772,130.06638510419688 Z" fill="none" stroke="hsl(10, 2%, 70%)" stroke-width="2" stroke-linecap="round" stroke-dasharray="1,4" />
<text x="154.40031089723772" y="130.06638510419688" style="font: 15px JB; fill: hsl(30, 80%, 50%); text-anchor: middle; dominant-baseline: middle;">10</text>
<path d="M396.1678680711389,130.1755542985512 L390.16355708546314,144.67124331287542 L375.6678680711389,150.6755542985512 L361.1721790568147,144.67124331287542 L355.1678680711389,130.1755542985512 L361.1721790568147,115.67986528422696 L375.6678680711389,109.67555429855119 L390.16355708546314,115.67986528422696 L396.1678680711389,130.1755542985512 Z" fill="none" stroke="hsl(10, 2%, 70%)" stroke-width="2" stroke-linecap="round" stroke-dasharray="1,4" />
<text x="375.6678680711389" y="130.1755542985512" style="font: 15px JB; fill: hsl(30, 80%, 50%); text-anchor: middle; dominant-baseline: middle;">40</text>
<path d="M634.9941907925735,130.055668834522 L628.9898798068976,144.55135784884624 L614.4941907925735,150.555668834522 L599.9985017782493,144.55135784884624 L593.9941907925735,130.055668834522 L599.9985017782492,115.55997982019778 L614.4941907925735,109.55566883452201 L628.9898798068976,115.55997982019778 L634.9941907925735,130.055668834522 Z" fill="none" stroke="hsl(10, 2%, 70%)" stroke-width="2" stroke-linecap="round" stroke-dasharray="1,4" />
<text x="614.4941907925735" y="130.055668834522" style="font: 15px JB; fill: hsl(30, 80%, 50%); text-anchor: middle; dominant-baseline: middle;">15</text>
</svg>

In the dfs traversal we first visit $1$, then $2$ and $4$.
The wealth of the employee $4$ is $10$.
$4$ has no children, and so $dp[4] = a[4] = 10$ by definition.
We now go to vertex $5$. Like vertex $4$, $dp[5] = a[5] = 40$.
We can now compute $dp[2]$.
$$dp[2] = \min(a[2], dp[4], dp[5]) = \min(20, 10, 40) = 10$$
Now we backtrack to vertex $1$ in the dfs process.
We then go down to vertex $3$ and then $6$.
As $6$ has no children, $dp[6] = a[6] = 15$.
Now $dp[3] = \min(a[3], dp[6]) = \min(30, 15) = 15$.
Finally we compute $dp[1]$.
$$dp[1] = \min(a[1], dp[2], dp[3]) = \min(50, 10, 15) = 10$$
Hence $dp[1]$ is the minimum possible wealth of any employee, just as expected.
We now summarize the values computed in a table.

| Vertex number | a  | dp | a - dp |
|---------------|----|----|--------|
| 1             | 50 | 10 | 40     |
| 2             | 20 | 10 | 10     |
| 3             | 30 | 15 | 15     |
| 4             | 10 | 10 | 0      |
| 5             | 40 | 40 | 0      |
| 6             | 15 | 15 | 0      |

Now we need to just find the maximum possible value of $a[i] - dp[i]$
for all values of $i$. From the above table, we see that the answer is $40$.

## Implementation

This is my implementation of this problem:

```cpp title="solution.cpp"
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> adj;
vector<int> a, dp;

void dfs(int v) {
  dp[v] = a[v];

  for (int u : adj[v]) {
    dfs(u);
    dp[v] = min(dp[v], dp[u]);
  }
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);

  int n;
  cin >> n;

  a.resize(n + 1);
  for (int i = 1; i <= n; i++) {
    cin >> a[i];
  }

  adj.resize(n + 1);
  int root = 0;

  for (int i = 1; i <= n; i++) {
    int p;
    cin >> p;

    if (p == -1) {
      root = i;
    } else {
      adj[p].push_back(i);
    }
  }

  dp.resize(n + 1);

  dfs(root);

  int ans = 0;
  for (int i = 1; i <= n; i++) {
    ans = max(ans, a[i] - dp[i]);
  }

  cout << ans << '\n';

  return 0;
}
```
