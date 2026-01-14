
![[Pasted image 20260113104345.png]]


Here is the step-by-step proof by induction for the problem in the image.

### **The Goal**

We want to prove that:

$$\sum_{k=1}^{n} k(k+1) = \frac{n(n+1)(n+2)}{3}$$

---

### **Step 1: The Base Case ($n=1$)**

First, we check if the formula works for the first domino ($n=1$).

- Left Hand Side (The Sum):
    
    We sum from $k=1$ to $1$:
    
    $$1(1+1) = 1(2) = \mathbf{2}$$
    
- Right Hand Side (The Formula):
    
    Substitute $n=1$ into the fraction:
    
    $$\frac{1(1+1)(1+2)}{3} = \frac{1(2)(3)}{3} = \frac{6}{3} = \mathbf{2}$$
    

Since $2 = 2$, the base case holds.

---

### **Step 2: The Inductive Hypothesis**

We assume the formula is true for some number $n$.

Assume:

$$\sum_{k=1}^{n} k(k+1) = \frac{n(n+1)(n+2)}{3}$$

---

### **Step 3: The Inductive Step**

We need to prove that if it is true for $n$, it must be true for **$n+1$**.

The Goal to Prove:

$$\sum_{k=1}^{n+1} k(k+1) = \frac{(n+1)(n+2)(n+3)}{3}$$

(Note: I just replaced every $n$ in the original formula with $n+1$).

The Proof:

Let's write out the sum for $n+1$ terms. This is just the sum of the first $n$ terms (which we know) plus the new $(n+1)^{th}$ term.

$$\text{Sum}_{n+1} = \left[ \sum_{k=1}^{n} k(k+1) \right] + \underbrace{(n+1)((n+1)+1)}_{\text{New Term}}$$

1. Substitute the Inductive Hypothesis for the part in brackets:
    
    $$= \left[ \frac{n(n+1)(n+2)}{3} \right] + (n+1)(n+2)$$
    
2. Make the algebra easier by factoring.
    
    Notice that both parts share common terms: $(n+1)$ and $(n+2)$. instead of expanding everything into a messy cubic equation, let's factor those out immediately.
    
    $$= (n+1)(n+2) \left[ \frac{n}{3} + 1 \right]$$
    
3. Combine the fraction inside the brackets.
    
    $$\left[ \frac{n}{3} + 1 \right] = \left[ \frac{n}{3} + \frac{3}{3} \right] = \frac{n+3}{3}$$
    
4. Put it all back together.
    
    $$= (n+1)(n+2) \left[ \frac{n+3}{3} \right]$$
    
    $$= \frac{(n+1)(n+2)(n+3)}{3}$$
    

Conclusion:

This matches our goal exactly. Therefore, by mathematical induction, the formula is true for all natural numbers $n$.