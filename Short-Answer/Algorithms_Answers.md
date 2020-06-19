#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a) Time Complexity: O(2n) => O(n)

The time complexity in this algorithm will grow when n increases.

The single value a being set will always be constant time. The while loop will be linear time, because as n increases,
the longer it will take for a to become equal or greater than it to break out of the loop. Finally, the expression updating a's value will be constant time.

```python
def algo_a(n):
    a = 0 # O(1)
    while (a < n * n * n): # O(n)
      a = a + n * n # O(1)
      print(a) 

    return a

# total complexity: O(1) + O(n + 1) => O(1) + O(n) => O(n)
```

b) Time Complexity: O(n^2)

The time complexity of this algorithm is linear, or O(n^2), because there is nested loops. If n is increased, the amount of iterations the first for loop will have to run increases. Increasing n will also increase the amount of iterations the while loop runs, because j is always reset back to 1 at the start of the for loop, making it slower for j to become equal to or greater than n for the while loop.

```python
def sum_numbers(n):
    sum = 0  # O(1)
    for i in range(n):  # O(n) in range of 0 - 5
        j = 1  # O(1)
        while j < n:
            j *= 2 # O(1)
            sum += 1 # O(1)

    return sum

# pass 5 in as n for example:
# 1st iteration => i = 0, j = 1, j(1) < n(5), j *= 2 = 2, sum = 1
    # j = 4, sum = 2
    # j = 8, sum = 3
# 2nd iteration => i = 1, j = 1, j(1) < n(5), j *= 2 = 2, sum = 4
    # j = 4, sum = 5
    # j = 8, sum = 6
# 3rd iteration => i = 2, j = 1, j(1) < n(5), j *= 2 = 2, sum = 7
    # j = 4, sum = 8
    # j = 8, sum = 9
# 4th iteration => i = 3, j = 1, j(1) < n(5), j *= 2 = 2, sum = 10
    # j = 4, sum = 11
    # j = 8, sum = 12
# 5th iteration => i = 4, j = 1, j(1) < n(5), j *= 2 = 2, sum = 13
    # j = 4, sum = 14
    # j = 8, sum = 15
# exit both loops
```

c) Time Complexity: O(n)

This is a recrusive algorithm. Increasing the amount of bunnies will increase the amount of recursive calls that need to be made, resulting in more branches and more depth in our algorithm.

Our base case to exit recursion (comparison to see if bunnies is equal to 0) is constant time. The return statement adds 2 (for the amount of bunny ears per bunny head) to the recursive call of bunnyEars, with the amount of bunnies decreased by 1.

```python
def bunnyEars(bunnies): # O(n)
      if bunnies == 0: # O(1)
        return 0

      return 2 + bunnyEars(bunnies-1) # 2 + O(n) => O(n)
```

## Exercise II

Summary: In order to minimize the amount of dropped and broken eggs, it would be best to approach this problem in a binary search tree like way.

Depending on the height of the building, the first floor that I would drop an egg from would be the midpoint, or floor in the middle of the building.

If the egg still broke at this height, then I would halve the remaining floors beneath me, move down to that new midpoint, and drop another egg. 

This process would continue until I found a floor where the egg did not break from being dropped. 

On the other hand, if after the first initial drop from the initial midpoint resulted in a non broken egg, and assuming we are to find the exact floor (f) before eggs will break, I would implement my halving strategy, going the other direction, upward towards the roof of the building. 

At the new midpoint, I would drop another egg and see if it broke, and repeat the same process.

```python
    # get the middle floor height by finding the midpoint / middle of the building (len(building // 2))
    # did the egg break at this floor?

        # YES
            # find the new midpoint / middle between the ground floor and the current middle floor (midpoint // 2)
            # did the egg break at this floor?

            # YES
                # find the new midpoint / middle between the ground floor and the current middle floor (midpoint // 2)
                # did the egg break at this floor?

                #REPEAT

            # NO
                # we found a floor that eggs won't break

        # NO
            # we found a floor that eggs won't break
            # at this point, if one of the requirements is to find the exact floor (f) that allows for eggs to be dropped
            # without breaking, and the next floor above would be the first floor (f) that breaks eggs, I would
            # repeat my same strategy going upwards in the other direction
```


