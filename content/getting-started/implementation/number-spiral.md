---
draft: false
title: "Number Spiral"
editorial:
  platform: "CSES"
  category: "Introductory Problems"
  name: "Number Spiral"
weight: 1
---
*Editorial written by Sri Vidya Sundar.*

{{< problem "cses-number-spiral" >}}

## Abridged problem statement
Given a grid with numbers filled in the form of an outward spiral, find the number that is present in the cell $(x,y)$.

## Observation
Consider a square from the top left corner to a cell $(a,a)$. This square contains all the numbers from $1$ to $a^2$. For example a square starting at cell $(1,1)$ and ending at cell $(3,3)$ has values from $1$ to $9$.

<div style="position:relative; margin:0 auto; width:300px; height:300px; font-family:sans-serif; text-align:center; color:black; background:white;">
  <div style="display:grid; grid-template-columns:repeat(5, 1fr); grid-template-rows:repeat(5, 1fr); gap:6px; width:300px; height:300px; box-sizing:border-box; padding:6px; margin:0;">
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">1</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">2</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">9</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">10</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">25</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">4</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">3</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">8</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">11</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">24</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">5</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">6</div>
    <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">7</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">12</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">23</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">16</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">15</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">14</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">13</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">22</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">17</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">18</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">19</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">20</div>
    <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;">21</div>
  </div>
</div>

## Solution
Now let us divide the grid into squares starting at the top left corner of the grid. 
Now I pick a cell $(x,y)$ outside a square of dimensions $a \times a$. I know the value on cell $(x,y)$ has to be greater than $a^2$. This is because all the numbers from $1$ to $a^2$ are already already completely contained inside that square. 
So how do we use this to solve this problem?
Consider the largest square that does not contain the cell $(x,y)$. What should be the dimensions of this square? If $x \geq y$ this square must have dimensions $(x-1) \times (x-1)$. If $y \geq x$ this square must have dimensions $(y-1) \times (y-1)$. 
Once this square has been filled, all numbers up to $(\max(x,y)-1)^2$ have already been used. The spiral uses Method 1 when the side length of the previously completed square (the blue square) is odd, and Method 2 when it is even.

<div style="display:flex; flex-direction:column; align-items:center; margin:0 auto; width:fit-content; font-family:sans-serif;">
  <div style="position:relative; width:300px; height:300px; text-align:center; color:black; background:white;">
    <div style="display:grid; grid-template-columns:repeat(5, 1fr); grid-template-rows:repeat(5, 1fr); gap:6px; width:300px; height:300px; box-sizing:border-box; padding:6px; margin:0;">
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">1</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">2</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">9</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">10</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">25</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">4</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">3</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">8</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">11</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">24</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">5</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">6</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">7</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">12</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">23</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">16</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">15</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">14</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">13</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">22</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">17</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">18</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">19</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">20</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">21</span></div>
    </div>
    <!-- SVG given z-index: 1 so it sits over the grid backgrounds but under the z-index: 2 text -->
    <svg style="position:absolute; top:0; left:0; width:300px; height:300px; pointer-events:none; z-index:1;" viewBox="0 0 300 300">
      <defs>
        <marker id="arrowhead" markerWidth="6" markerHeight="6" refX="2" refY="3" orient="auto">
          <path d="M 0 0 L 6 3 L 0 6 Z" fill="#1565C0" />
        </marker>
      </defs>
      <path d="M 209 32 L 209 209 L 32 209" fill="none" stroke="#1565C0" stroke-width="4.5" marker-end="url(#arrowhead)" stroke-linejoin="round"/>
    </svg>
  </div>
  
  <div style="margin-top:12px; font-weight:bold; font-size:1.1rem; color:#333;">
    Method 1
  </div>
</div>




<div style="display:flex; flex-direction:column; align-items:center; margin:0 auto; width:fit-content; font-family:sans-serif;">
  <div style="position:relative; width:300px; height:300px; text-align:center; color:black; background:white;">
    <div style="display:grid; grid-template-columns:repeat(5, 1fr); grid-template-rows:repeat(5, 1fr); gap:6px; width:300px; height:300px; box-sizing:border-box; padding:6px; margin:0;">
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">1</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">2</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">9</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">10</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">25</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">4</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">3</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">8</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">11</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">24</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">5</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">6</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">7</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">12</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">23</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">16</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">15</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">14</span></div>
      <div style="background-color:#2196F3; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">13</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">22</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">17</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">18</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">19</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">20</span></div>
      <div style="background-color:#E0E0E0; display:flex; align-items:center; justify-content:center; font-weight:bold; font-size:1.2rem;"><span style="position:relative; z-index:2;">21</span></div>
    </div>
    <!-- SVG given z-index: 1 so it sits under the text but over the cell background colors -->
    <svg style="position:absolute; top:0; left:0; width:300px; height:300px; pointer-events:none; z-index:1;" viewBox="0 0 300 300">
      <defs>
        <marker id="arrowhead" markerWidth="6" markerHeight="6" refX="2" refY="3" orient="auto">
          <path d="M 0 0 L 6 3 L 0 6 Z" fill="#1565C0" />
        </marker>
      </defs>
      <!-- Arrow path adjusted to perfectly intersect the center coordinates (X:268, Y:268) of the 5th column and 5th row -->
      <path d="M 32 268 L 268 268 L 268 32" fill="none" stroke="#1565C0" stroke-width="4.5" marker-end="url(#arrowhead)" stroke-linejoin="round"/>
    </svg>
  </div>
  
  <div style="margin-top:12px; font-weight:bold; font-size:1.1rem; color:#333;">
    Method 2
  </div>
</div>


The numbers are filled in method 1 if the dimensions of the blue filled square is odd and method 2 if the dimensions of the blue filled square are even.
For simplicity, we will be dealing with $x \geq y$ here. You can easily derive the result for the other case as well. 

We first fill the square of dimensions $(x-1)\times(x-1)$, which contains the numbers $1$ through $(x-1)^2$. We continue counting from $(x-1)^2$ and move forward by $y$ cells 
If the cells were filled using method 2, we start by filling the square of dimensions $(x-1)^2$. After this we continue to fill $x + (x - y) = 2x - y$ additional cells. 

## Code
``` cpp
#include <bits/stdc++.h>
using namespace std;

int32_t main(){
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);
    long long t;
    cin >> t;
    while(t--){
        long long x, y;
        cin >> x >> y;
        if(x > y){
            if(x%2 == 1){
                cout << ((x-1)*(x-1) + y);
            }
            else{
                cout << ((x-1)*(x-1) + 2*x - y);
            }
        }
        else{
            if(y%2 == 0){
                cout << ((y-1)*(y-1) + x);
            }
            else{
                cout << ((y-1)*(y-1) + 2*y - x);
            }
        }
        cout<<"\n";
    }
} 
```
