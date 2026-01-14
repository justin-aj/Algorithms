![[Pasted image 20260112150022.png]]
Here is the step-by-step mathematical derivation for the optimal solution.

### 1. The Goal

We want to find the minimum number of drops, let's call it **$W$** (Worst-case drops), required to test a range of **$N$** floors (where $N = 1,000,000$).

To optimize, we must ensure that **no matter when the first tank breaks, the total number of drops used is exactly the same.** This "equalizes the pain" across all scenarios so there is no "bad luck" outcome.

### 2. The Setup

Let $k$ be the floor number we jump to for each test with the first tank.

- **Drop 1:** We drop Tank 1 at floor $x_1$.
    
    - _If it breaks:_ We have used **1** drop. We have **$W-1$** drops left. We must use Tank 2 to test the floors $1$ to $x_1-1$ linearly. To guarantee we can do this, the range must be no larger than our remaining drops.
        
    - So, the size of the first jump can be at most **$W$**. (1 drop for the big jump + $W-1$ drops for the linear search).
        
    - **Therefore, $x_1 = W$**.
        
- **Drop 2:** Suppose Tank 1 survives. We jump up by $x_2$ floors.
    
    - _If it breaks:_ We have used **2** drops (the first one + this one). We have **$W-2$** drops left.
        
    - This means the range we skipped over ($x_2 - 1$) can hold at most $W-2$ floors.
        
    - **Therefore, $x_2 = W-1$**.
        
- **Drop 3:** Suppose Tank 1 survives. We jump up by $x_3$ floors.
    
    - _If it breaks:_ We have used **3** drops. We have **$W-3$** drops left.
        
    - **Therefore, $x_3 = W-2$**.
        

### 3. The Pattern and Summation

You can see the pattern: Every time we take a successful step with Tank 1, we "spend" one of our allowed drops, so we must reduce the _next_ step size by 1 to keep the worst-case total constant.

The maximum height $N$ we can test is the sum of all these decreasing step sizes:

$$N = W + (W-1) + (W-2) + \dots + 1$$

This is the sum of the first $W$ integers (an arithmetic series). The formula for this sum is:

$$N = \frac{W(W+1)}{2}$$

### 4. Solving for $W$

We know $N = 1,000,000$. We need to find the smallest integer $W$ that satisfies:

$$\frac{W(W+1)}{2} \geq 1,000,000$$

Multiply by 2:

$$W(W+1) \geq 2,000,000$$

$$W^2 + W - 2,000,000 \geq 0$$

We can use the quadratic formula to solve for $W$:

$$W = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$

Where $a=1, b=1, c=-2,000,000$.

$$W = \frac{-1 + \sqrt{1^2 - 4(1)(-2,000,000)}}{2}$$

$$W = \frac{-1 + \sqrt{1 + 8,000,000}}{2}$$

$$W \approx \frac{-1 + \sqrt{8,000,001}}{2}$$

$$W \approx \frac{-1 + 2828.43}{2}$$

$$W \approx \frac{2827.43}{2}$$

$$W \approx 1413.71$$

Since we cannot do a fractional drop, we round up to the next whole number:

$$W = 1414$$

### 5. Why this is better than $\sqrt{N}$

The slide you uploaded suggests increments of $\sqrt{N}$. Let's compare:

- **Slide Method ($\sqrt{N}$):**
    
    - Jump size is fixed at $\sqrt{1,000,000} = 1,000$.
        
    - Worst case: The tank breaks at the very top (999,999).
        
    - You drop Tank 1 roughly **1,000** times to get there.
        
    - Then you drop Tank 2 roughly **999** times to find the exact lb.
        
    - **Total Tests:** $1,000 + 999 = 1,999$.
        
- **Optimal Method (Decreasing Steps):**
    
    - **Total Tests:** **1,414**.
        

By doing the math and decreasing the step size, you save nearly **600 very expensive tests**.

### Summary of the Optimal Plan

1. **Drop 1:** Test at **1,414** lbs.
    
2. **Drop 2:** Add 1,413. Test at **2,827** lbs.
    
3. **Drop 3:** Add 1,412. Test at **4,239** lbs.
    
4. Continue decreasing the step by 1 each time.
