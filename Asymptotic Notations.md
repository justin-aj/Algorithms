

## Think About It Like Speed Limits

Imagine you're trying to describe how fast your car goes.

**Upper bound (Big-O)** is like saying "my car goes _at most_ 150 mph." It might go slower sometimes, but it will never go faster than that. You're putting a ceiling on it.

**Lower bound (Big-Ω)** is like saying "my car goes _at least_ 30 mph." It might go faster sometimes, but it will never go slower than that. You're putting a floor on it.

**Tight bound (Big-Θ)** is like saying "my car goes between 60 and 70 mph pretty much all the time." You're pinning it down from both sides.

## Applied to Algorithms

When we say an algorithm is O(n²), we're saying "no matter what input you give it, it will _never_ take more than roughly n² steps." That's the ceiling. The worst it can possibly be.

When we say an algorithm is Ω(n), we're saying "no matter what shortcuts exist, it will _always_ take at least roughly n steps." That's the floor. The best it can possibly be.

When we say an algorithm is Θ(n log n), we're saying "it pretty much always takes around n log n steps, give or take." It doesn't get much better or much worse than that.

## A Concrete Example

Take insertion sort (the algorithm where you pick up each card and slide it into the right spot in your hand).

If the list is already sorted, you just glance at each item once and confirm it's in place. That's n steps. Best case.

If the list is completely backwards, every new item has to shuffle all the way to the front. That ends up being roughly n² steps. Worst case.

So we'd say insertion sort has a lower bound of Ω(n) and an upper bound of O(n²). The best it can do is n, the worst it can do is n².