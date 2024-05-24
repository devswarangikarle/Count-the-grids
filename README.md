# Count-the-grids

Given a value N. In how many ways you can construct a grid of size N x 4 using tiles of size 1 x 4?
NOTE: The answer can be very large.
Input
There is a single line of input that takes an integer as input representing N.

Constraints:
1 ≤ N ≤ 80
Output
Print an integer representing the number of ways you can construct a grid of size N x 4 using tiles of size 1 x 4.
NOTE: The answer can be very large.

def count_ways_to_construct_grid(n):
    if n == 0:
        return 1
    
    # Initialize dp array
    dp = [0] * (n + 1)
    
    # Base cases
    dp[0] = 1  # Empty grid
    if n >= 1:
        dp[1] = 1
    if n >= 2:
        dp[2] = 1
    if n >= 3:
        dp[3] = 1
    if n >= 4:
        dp[4] = 2  # either four vertical tiles or one horizontal tile
    
    # Fill the dp array using the recurrence relation
    for i in range(5, n + 1):
        dp[i] = dp[i-1] + dp[i-4]
    
    return dp[n]

# Example usage
n = int(input().strip())
print(count_ways_to_construct_grid(n))
