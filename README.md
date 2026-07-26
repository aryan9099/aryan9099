"""
Problem: Climbing Stairs
Link: https://leetcode.com/problems/climbing-stairs/
Difficulty: Easy

You're climbing a staircase with `n` steps. Each time you can climb 1 or 2
steps. In how many distinct ways can you reach the top?

Approach:
This is a Fibonacci-style recurrence: ways(n) = ways(n-1) + ways(n-2),
because the last move to reach step n was either a 1-step from n-1
or a 2-step from n-2. Solved bottom-up to avoid recursion overhead.

Time Complexity: O(n)
Space Complexity: O(1) — only two variables tracked at a time
"""

def climb_stairs(n: int) -> int:
    if n <= 2:
        return n

    prev, curr = 1, 2
    for _ in range(3, n + 1):
        prev, curr = curr, prev + curr
    return curr


if __name__ == "__main__":
    assert climb_stairs(2) == 2
    assert climb_stairs(3) == 3
    assert climb_stairs(5) == 8
    print("All test cases passed!")
