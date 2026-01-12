
Induction is a proof technique in math. It lets you prove that something is true for **all** positive integers (1, 2, 3, 4, ... forever) without checking each one individually.

## The Domino Analogy

Imagine an infinite line of dominoes. You want to prove they'll all fall. You need two things:

**First:** Knock over the first domino.

**Second:** Show that _if_ any domino falls, it will knock over the next one.

If both of those are true, you know every single domino will fall. The first one falls, which knocks over the second, which knocks over the third, and so on forever.

That's induction.

## The Two Steps in Math Terms

**Base case:** Prove the statement is true for n = 1 (knock over the first domino).

**Inductive step:** Assume the statement is true for some arbitrary n = k. Then prove it must also be true for n = k + 1 (show that one domino falling causes the next to fall).

If you do both, you've proven it for all positive integers.

## A Simple Example

Let's prove that 1 + 2 + 3 + ... + n = n(n+1)/2.

**Base case (n = 1):** The left side is just 1. The right side is 1(1+1)/2 = 1. They match. The first domino falls.

**Inductive step:** Assume it works for some number k. So we're assuming 1 + 2 + 3 + ... + k = k(k+1)/2 is true.

Now we need to show it works for k + 1. That means showing 1 + 2 + 3 + ... + k + (k+1) = (k+1)(k+2)/2.

Take the left side. We already assumed that 1 + 2 + ... + k equals k(k+1)/2. So the left side becomes k(k+1)/2 + (k+1).

Factor out (k+1) and you get (k+1)(k/2 + 1) = (k+1)(k+2)/2.

That's exactly what we needed. Done.

## Why It Works

The base case gets you started. The inductive step creates a chain reaction. True for 1 means true for 2. True for 2 means true for 3. And so on, forever.
