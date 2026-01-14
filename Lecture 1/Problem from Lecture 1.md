
![[Pasted image 20260112132421.png]]

Based on the recurrence relation provided in the image, here is the step-by-step derivation to find the closed form for $W(n)$.

### 1. Understand the Definitions

From the image, we have:

- **Recurrence:** $W(n) = 1 + W(\lceil n/3 \rceil)$
    
- **Base Case:** $W(1) = 0$
    
- **Assumption:** $n = 3^m$ (This means $n$ is a power of 3).
    

### 2. Simplify based on the Assumption

Because we are assuming $n = 3^m$, dividing $n$ by 3 will always result in an integer. Therefore, we can drop the ceiling function $\lceil \dots \rceil$ for this specific case.

The recurrence becomes:

$$W(3^m) = 1 + W(3^m / 3)$$

$$W(3^m) = 1 + W(3^{m-1})$$

### 3. Solve by Substitution (Unrolling)

Let's expand the recurrence to find a pattern:

- Step 1:
    
    $$W(3^m) = 1 + W(3^{m-1})$$
    
- Step 2: Substitute $W(3^{m-1})$ with $[1 + W(3^{m-2})]$:
    
    $$W(3^m) = 1 + [1 + W(3^{m-2})] = 2 + W(3^{m-2})$$
    
- Step 3: Substitute $W(3^{m-2})$:
    
    $$W(3^m) = 2 + [1 + W(3^{m-3})] = 3 + W(3^{m-3})$$
    
- Step k: After repeating this $k$ times, the pattern is:
    
    $$W(3^m) = k + W(3^{m-k})$$
    

### 4. Apply the Base Case

We know the base case is $W(1) = 0$. Since $1 = 3^0$, we need the term inside the function, $3^{m-k}$, to equal $3^0$.

This means:

$$m - k = 0 \Rightarrow k = m$$

Substitute $k = m$ into our pattern equation:

$$W(3^m) = m + W(3^{m-m})$$

$$W(3^m) = m + W(3^0)$$

$$W(3^m) = m + W(1)$$

Since $W(1) = 0$:

$$W(3^m) = m$$

### 5. Convert back to terms of $n$

The question asks for a closed form for $W(n)$, not $W(3^m)$. We need to express $m$ in terms of $n$.

From our assumption:

$$n = 3^m$$

Take the logarithm (base 3) of both sides:

$$\log_3(n) = m$$

Substitute this back into our result for $W(n)$:

$$W(n) = \log_3(n)$$

Final Answer:

The closed form for $W(n)$ is $\log_3(n)$.