# Problem Solving

## Approach
##### Step 1: Understand the problem
1. Can you restate the problem in your own words?
2. Inputs?
3. Ideal outputs?
4. Can the input determine the output?
5. How should I label the data?

##### Step 2: Explore concrete examples
1. Simple examples (ex. sum(1, 5) should equal 6)
2. Complex examples
4. Edge cases (high, low, empty, invalid, etc)

##### Step 3: Break it down
- Break down steps into comments, communicate what your thinking

##### Step 4: Solve/Simplify
- If you can't solve, solve a simpler portion and then incorporate the difficuly after

##### Step 5: Look back and refactor
- Can you check the result?
- Derive the result differently?
- Understand at a glance?
- Can you use for another problem?
- Improve the performance?
- How have others solved it? 


## Patterns
#### Frequency Counter
- Sets frequencies of the values and compares
- Use: prevents nested for loops O(n^2)
- Ex. comparing anagrams, if they match (same # characters)

#### Multiple Pointers
- Two pointer moving towards a front, middle, or end

#### Sliding Window
- Using a window into an array and shifting it (remove first, add new last), instead of recalculating with new first to last subset
- Good for subsets

#### Divide & Conquer
- Dividing data and repeating with subsets (log n)
