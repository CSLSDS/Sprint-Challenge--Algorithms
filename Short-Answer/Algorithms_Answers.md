#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a)
```python
a)  a = 0
    while (a < n * n * n): # O(n^3)  initial
      a = a + n * n        # O(-n^2) modifier will abbreviate the loop
                           # O(n)    final
```
runtime complexity is O(n)

___

b)
```python
b)  sum = 0
    for i in range(n):  # O(n)
      j = 1
      while j < n:      # O(n)
        j *= 2          # modifier will abbreviate the loop
        sum += 1        # reducing to O(log(n))
```
runtime complexity is O(n(log(n))

___

c)
```python
c)  def bunnyEars(bunnies):
      if bunnies == 0: # ends after var decrements to 0 
        return 0

      return 2 + bunnyEars(bunnies-1) # recurses n times; equivalent to for loop
```
runtime complexity is O(n)
___

## Exercise II

Suppose that you have an n-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor f or higher, and doesn't get broken if dropped off a floor less than floor f. Devise a strategy to determine the value of f such that the number of dropped + broken eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode AND give the runtime complexity of your solution.  
  
  ___
  ...  
A brute-force solution is to drop an egg once per floor   
(starting at the ground floor and presuming it didn't break then)
```python
if egg is not broken at floor[0]:
    for egg in range number-of-floors, drop egg
```  
to check if the egg will break or not on that floor,  
and if it does, the safe floor is the one below. 
```python
        if egg is broken:
            safe floor is that floor - 1
```

...which can be computed in O(n) time.

However, because we can presume that the breakpoint of eggs increases and decreases linearly between floors because of the laws of physics, with building floors being a necessarily ordered array, we can use binary searching to **reduce our search time to O(log(n))**, meaning we would start our search at the midpoint of the total number of floors, more rapidly 'searching' for the answer by eliminating irrelevant floors to check, substantially reducing our runtime complexity for increasingly tall buildings.