# 📘 Chapter 7: Lists and Tuples
### *Starting Out with Python — Textbook Companion & Practice Guide*

---

## 📚 Table of Contents

1. [Sequences](#1-sequences)
2. [Introduction to Lists](#2-introduction-to-lists)
3. [Indexing](#3-indexing)
4. [The `len()` Function](#4-the-len-function)
5. [Lists Are Mutable](#5-lists-are-mutable)
6. [Concatenating Lists](#6-concatenating-lists)
7. [List Slicing](#7-list-slicing)
8. [The `in` Operator](#8-the-in-operator)
9. [List Methods & Built-in Functions](#9-list-methods--built-in-functions)
10. [Copying Lists](#10-copying-lists)
11. [Processing Lists](#11-processing-lists)
12. [List Comprehensions](#12-list-comprehensions)
13. [Two-Dimensional Lists](#13-two-dimensional-lists)
14. [Tuples](#14-tuples)
15. [Practice Assignments](#15-practice-assignments)

---

## 1. Sequences

A **sequence** is an object that contains multiple items of data stored one after another in order. Python provides several types of sequences, the two most common being **lists** and **tuples**.

The key distinction between them:

| Type  | Mutable? | Description |
|-------|----------|-------------|
| List  | ✅ Yes   | Items can be added, removed, or changed |
| Tuple | ❌ No    | Once created, items cannot be changed |

> 💡 **Think of it this way:** A list is like a whiteboard — you can erase and rewrite. A tuple is like a printed receipt — it's permanent.

**Quick Check:**

<details>
<summary>What is the difference between a mutable and immutable sequence?</summary>

A **mutable** sequence can be changed after it is created — you can add, remove, or modify its elements. A **list** is mutable.

An **immutable** sequence cannot be changed after creation. A **tuple** is immutable — once you define it, its values are locked.

```python
# Mutable — this works fine
my_list = [1, 2, 3]
my_list[0] = 99      # ✅ Allowed

# Immutable — this raises an error
my_tuple = (1, 2, 3)
my_tuple[0] = 99     # ❌ TypeError: 'tuple' object does not support item assignment
```

</details>

---

## 2. Introduction to Lists

A **list** is an object that holds multiple data items called **elements**. Lists are created using square brackets `[]` with items separated by commas.

### Syntax

```python
list_name = [item1, item2, item3]
```

### Examples

```python
# A list of numbers
even_numbers = [2, 4, 6, 8, 10]

# A list of names
names = ['Molly', 'Steven', 'Will', 'Alicia', 'Adriana']

# A list with mixed data types
info = ['Alicia', 27, 1550.87]

# Printing an entire list
print(even_numbers)   # Output: [2, 4, 6, 8, 10]
```

> 💡 Python lists can hold items of **different data types** — numbers, strings, and even other lists — all in the same list.

### The Repetition Operator

The `*` operator can make multiple copies of a list and join them together:

```python
zeros = [0] * 5
print(zeros)   # Output: [0, 0, 0, 0, 0]
```

### Iterating Over a List

```python
fruits = ['apple', 'banana', 'cherry']
for fruit in fruits:
    print(fruit)
```

**Quick Check:**

<details>
<summary>How do you create a list in Python?</summary>

Use square brackets `[]` with items separated by commas and assign it to a variable:

```python
numbers = [10, 20, 30, 40, 50]
names   = ['Alice', 'Bob', 'Charlie']
empty   = []   # An empty list
```

You can also use the `list()` function to convert other sequences into a list:

```python
my_tuple = (1, 2, 3)
my_list  = list(my_tuple)   # [1, 2, 3]
```

</details>

<details>
<summary>Can a Python list hold mixed data types?</summary>

Yes! Unlike some other languages, Python lists can hold items of **any type** — all mixed together in the same list:

```python
info = ['Alicia', 27, 1550.87, True]
#        string   int  float   bool
print(info)  # Output: ['Alicia', 27, 1550.87, True]
```

Each element keeps its own data type. You can even put lists inside lists (called nested lists).

</details>

---

## 3. Indexing

An **index** is a number specifying the position of an element in a list. Indexing allows you to access individual elements.

### Rules

- The **first** element is always at index `0`
- The **second** element is at index `1`
- The **nth** element is at index `n - 1`
- **Negative indexes** count from the end of the list

```
Index:   0       1       2       3       4
List:  [ 10,    20,     30,     40,     50  ]
Index:  -5      -4      -3      -2      -1
```

### Examples

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[0])    # Output: 10  (first element)
print(numbers[2])    # Output: 30  (third element)
print(numbers[-1])   # Output: 50  (last element)
print(numbers[-2])   # Output: 40  (second to last)
```

> ⚠️ **IndexError:** If you try to access an index that doesn't exist, Python raises an `IndexError`. Always make sure your index is within range!

**Quick Check:**

<details>
<summary>What does index 0 mean in Python?</summary>

Index `0` refers to the **first element** in a list. Python (like most programming languages) starts counting positions from `0`, not `1`. This is called **zero-based indexing**.

```python
colors = ['red', 'green', 'blue']
#          [0]     [1]      [2]

print(colors[0])  # Output: red
print(colors[1])  # Output: green
print(colors[2])  # Output: blue
```

So a list with 5 items has valid indexes `0` through `4`.

</details>

<details>
<summary>How do negative indexes work in Python lists?</summary>

Negative indexes let you count from the **end** of the list instead of the beginning:

- `-1` → last element
- `-2` → second to last element
- `-n` → nth element from the end

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[-1])  # Output: 50  (last)
print(numbers[-2])  # Output: 40  (second to last)
print(numbers[-5])  # Output: 10  (same as index 0)
```

This is especially useful when you want the last element but don't know the length of the list.

</details>

---

## 4. The `len()` Function

The `len()` function returns the **total number of elements** in a list (its length).

```python
my_list = [5, 10, 15, 20]
size = len(my_list)
print(size)   # Output: 4
```

Since the list has 4 elements, the last valid index is `len(my_list) - 1` = `3`.

### Using `len()` in Loops

```python
numbers = [10, 20, 30, 40, 50]
for i in range(len(numbers)):
    print(numbers[i])
```

> 💡 Using `range(len(list))` is a common pattern when you need the **index** as well as the value inside your loop.

**Quick Check:**

<details>
<summary>What does the len() function return for a list?</summary>

`len()` returns an **integer** representing the total number of elements in the list.

```python
fruits = ['apple', 'banana', 'cherry']
print(len(fruits))   # Output: 3

empty = []
print(len(empty))    # Output: 0
```

Since indexes start at `0`, the last valid index is always `len(list) - 1`. Accessing `list[len(list)]` would cause an `IndexError`.

</details>

---

## 5. Lists Are Mutable

Because lists are **mutable**, you can change the value of any element using its index:

```python
numbers = [10, 20, 30, 40, 50]
numbers[1] = 99
print(numbers)   # Output: [10, 99, 30, 40, 50]
```

You can also use the `del` statement to **remove** an element at a specific index:

```python
numbers = [10, 20, 30, 40]
del numbers[2]
print(numbers)   # Output: [10, 20, 40]
```

> ⚠️ Always use a valid index when modifying a list to avoid raising an `IndexError`.

**Quick Check:**

<details>
<summary>How do you change an element in a Python list?</summary>

Use the element's index on the left side of an assignment statement:

```python
grades = [88, 92, 75, 95]
grades[2] = 85         # Change index 2 from 75 to 85
print(grades)          # Output: [88, 92, 85, 95]
```

You can also delete an element entirely using `del`:

```python
grades = [88, 92, 75, 95]
del grades[1]          # Remove the element at index 1
print(grades)          # Output: [88, 75, 95]
```

Remember: tuples do **not** support this — only lists are mutable.

</details>

---

## 6. Concatenating Lists

You can join two lists together using the `+` operator:

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined = list1 + list2
print(combined)   # Output: [1, 2, 3, 4, 5, 6]
```

You can also use the `+=` augmented assignment operator:

```python
list1 = [1, 2, 3]
list1 += [4, 5, 6]
print(list1)   # Output: [1, 2, 3, 4, 5, 6]
```

> ⚠️ You **cannot** concatenate a list with a non-list type (like an integer). `[1, 2] + 3` will raise a `TypeError`.

---

## 7. List Slicing

A **slice** is a portion of a list. Slicing creates a new list containing copies of the selected elements.

### Syntax

```python
list[start : end]
```

- `start` — the index to begin at (inclusive)
- `end` — the index to stop at (**exclusive** — this element is NOT included)

### Examples

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[1:4])   # Output: [20, 30, 40]
print(numbers[:3])    # Output: [10, 20, 30]   (start defaults to 0)
print(numbers[2:])    # Output: [30, 40, 50]   (end defaults to len)
print(numbers[:])     # Output: [10, 20, 30, 40, 50]  (entire list)
```

### Step Values

You can also include a **step value** to skip elements:

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers[::2])   # Output: [0, 2, 4, 6, 8]  (every other element)
```

**Quick Check:**

<details>
<summary>How does list slicing work in Python?</summary>

Slicing extracts a **portion** of a list using the format `list[start:end]`. The `start` index is included, but the `end` index is **not** included (it stops just before it).

```python
letters = ['a', 'b', 'c', 'd', 'e']
#            0    1    2    3    4

print(letters[1:4])  # Output: ['b', 'c', 'd']  (indexes 1, 2, 3 — NOT 4)
print(letters[:2])   # Output: ['a', 'b']        (from start up to index 2)
print(letters[3:])   # Output: ['d', 'e']        (from index 3 to the end)
```

Slicing creates a **new list** — the original list is not modified. A useful trick: `list[:]` creates a full copy of the list.

</details>

---

## 8. The `in` Operator

Use the `in` operator to check whether an item exists in a list. It returns `True` or `False`.

```python
fruits = ['apple', 'banana', 'cherry']

print('banana' in fruits)    # Output: True
print('grape' in fruits)     # Output: False
print('grape' not in fruits) # Output: True
```

This is very useful in conditional statements:

```python
if 'apple' in fruits:
    print('We have apples!')
```

**Quick Check:**

<details>
<summary>How do you check if an item is in a list in Python?</summary>

Use the `in` operator. It evaluates to `True` if the item is found, and `False` if it is not:

```python
colors = ['red', 'green', 'blue']

print('green' in colors)      # Output: True
print('yellow' in colors)     # Output: False
print('yellow' not in colors) # Output: True
```

You can use this directly in an `if` statement:

```python
if 'red' in colors:
    print('Red is in the list!')
```

</details>

---

## 9. List Methods & Built-in Functions

Python lists come with built-in **methods** — actions you can perform on a list.

### Common Methods

| Method | Description | Example |
|--------|-------------|---------|
| `append(item)` | Adds `item` to the **end** of the list | `my_list.append(99)` |
| `insert(index, item)` | Inserts `item` at the specified `index` | `my_list.insert(1, 99)` |
| `remove(item)` | Removes the **first occurrence** of `item` | `my_list.remove(99)` |
| `sort()` | Sorts elements in **ascending** order | `my_list.sort()` |
| `reverse()` | Reverses the order of elements | `my_list.reverse()` |
| `index(item)` | Returns the index of the **first occurrence** of `item` | `my_list.index(99)` |

### Example Walkthrough

```python
nums = [3, 1, 4]

nums.append(9)        # [3, 1, 4, 9]
nums.insert(1, 7)     # [3, 7, 1, 4, 9]
nums.sort()           # [1, 3, 4, 7, 9]
nums.reverse()        # [9, 7, 4, 3, 1]
nums.remove(4)        # [9, 7, 3, 1]

print(nums)           # Output: [9, 7, 3, 1]
```

### Built-in Functions

```python
numbers = [5, 2, 8, 1, 9]

print(min(numbers))   # Output: 1
print(max(numbers))   # Output: 9
print(len(numbers))   # Output: 5
```

> 💡 Methods are called **on** the list using dot notation: `my_list.sort()`. Built-in functions are called **with** the list as an argument: `len(my_list)`.

**Quick Check:**

<details>
<summary>What is the difference between append() and insert()?</summary>

- **`append(item)`** always adds the item to the **end** of the list. It takes one argument.
- **`insert(index, item)`** adds the item at a **specific position**. It takes two arguments: the index and the item.

```python
my_list = [10, 20, 30]

my_list.append(99)      # Adds 99 to the end
print(my_list)          # Output: [10, 20, 30, 99]

my_list.insert(1, 55)   # Inserts 55 at index 1
print(my_list)          # Output: [10, 55, 20, 30, 99]
```

When you use `insert()`, existing elements at and after that index shift one position to the right.

</details>

<details>
<summary>How do you sort a list in Python?</summary>

Call the `.sort()` method directly on the list. It sorts in **ascending order** (lowest to highest) by default and modifies the list in place:

```python
numbers = [5, 2, 9, 1, 7]
numbers.sort()
print(numbers)   # Output: [1, 2, 5, 7, 9]
```

To sort in **descending order**, use the `reverse=True` argument:

```python
numbers.sort(reverse=True)
print(numbers)   # Output: [9, 7, 5, 2, 1]
```

Note: `.sort()` changes the original list. If you want a sorted copy without changing the original, use the built-in `sorted()` function instead.

</details>

---

## 10. Copying Lists

⚠️ You **cannot** copy a list simply by assigning it to a new variable. Doing so makes both variables point to the **same** list in memory:

```python
list1 = [1, 2, 3, 4]
list2 = list1         # ❌ This does NOT make a copy!
list2[0] = 99
print(list1)          # Output: [99, 2, 3, 4]  — list1 was also changed!
```

### Correct Ways to Copy a List

**Method 1 — Concatenation with empty list:**
```python
list1 = [1, 2, 3, 4]
list2 = [] + list1    # ✅ Creates a true copy
```

**Method 2 — Loop:**
```python
list1 = [1, 2, 3, 4]
list2 = []
for item in list1:
    list2.append(item)  # ✅ Creates a true copy
```

**Method 3 — Slicing (bonus):**
```python
list2 = list1[:]        # ✅ Also creates a true copy
```

---

## 11. Processing Lists

Lists are commonly used to store collections of numbers that need to be calculated on.

### Calculating a Total and Average

```python
scores = [88, 92, 75, 95, 83]

total = 0
for score in scores:
    total += score

average = total / len(scores)

print('Total:', total)       # Output: Total: 433
print('Average:', average)   # Output: Average: 86.6
```

> 💡 This pattern — starting an **accumulator variable** at 0 and adding each element inside a loop — is one of the most common patterns in programming.

**Quick Check:**

<details>
<summary>How do you calculate the total and average of a list using a loop?</summary>

Use an **accumulator variable** (`total`) that starts at `0` and adds each element inside the loop. Then divide by `len()` for the average:

```python
numbers = [10, 20, 30, 40, 50]

total = 0
for num in numbers:
    total += num          # Same as: total = total + num

average = total / len(numbers)

print('Total:', total)      # Output: Total: 150
print('Average:', average)  # Output: Average: 30.0
```

**Shortcut:** Python has a built-in `sum()` function so you can also write:
```python
average = sum(numbers) / len(numbers)
```

</details>

---

## 12. List Comprehensions

A **list comprehension** is a concise, one-line way to create a new list by iterating over an existing one.

### Traditional Loop vs. List Comprehension

```python
# Traditional loop
list1 = [1, 2, 3, 4]
list2 = []
for item in list1:
    list2.append(item)

# List comprehension — same result!
list2 = [item for item in list1]
```

### Transforming Elements

```python
# Square each number
list1 = [1, 2, 3, 4]
list2 = [item**2 for item in list1]
print(list2)   # Output: [1, 4, 9, 16]

# Get the length of each string
names = ['Winken', 'Blinken', 'Nod']
lengths = [len(name) for name in names]
print(lengths) # Output: [6, 7, 3]
```

### Filtering with `if`

```python
# Keep only numbers less than 10
list1 = [1, 12, 2, 20, 3, 15, 4]
list2 = [item for item in list1 if item < 10]
print(list2)   # Output: [1, 2, 3, 4]
```

**Quick Check:**

<details>
<summary>What is a list comprehension in Python?</summary>

A **list comprehension** is a compact way to build a new list using a single line of code. The basic structure is:

```
[expression for variable in iterable]
```

For example:

```python
# Long way (for loop)
squares = []
for n in range(1, 6):
    squares.append(n ** 2)

# Short way (list comprehension) — same result
squares = [n ** 2 for n in range(1, 6)]

print(squares)  # Output: [1, 4, 9, 16, 25]
```

You can also add a condition to filter what gets included:

```python
evens = [n for n in range(10) if n % 2 == 0]
print(evens)  # Output: [0, 2, 4, 6, 8]
```

</details>

---

## 13. Two-Dimensional Lists

A **two-dimensional list** (also called a **nested list**) is a list that contains other lists as its elements. It's useful for representing grids, tables, and matrices.

```python
# A 3x3 grid of numbers
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

### Accessing Elements

Use **two indexes** — the first for the row, the second for the column:

```python
print(matrix[0][0])   # Output: 1  (row 0, column 0)
print(matrix[1][2])   # Output: 6  (row 1, column 2)
print(matrix[2][1])   # Output: 8  (row 2, column 1)
```

### Iterating with Nested Loops

```python
for row in matrix:
    for value in row:
        print(value, end=' ')
    print()
# Output:
# 1 2 3
# 4 5 6
# 7 8 9
```

**Quick Check:**

<details>
<summary>How do two-dimensional lists work in Python?</summary>

A 2D list is a **list of lists**. Think of it like a grid with rows and columns. You access elements using two indexes: `list[row][column]`.

```python
grid = [
    ['A', 'B', 'C'],   # row 0
    ['D', 'E', 'F'],   # row 1
    ['G', 'H', 'I']    # row 2
]

print(grid[0][0])  # Output: A  (row 0, col 0)
print(grid[1][1])  # Output: E  (row 1, col 1)
print(grid[2][2])  # Output: I  (row 2, col 2)
```

To process all values, use **nested loops** — one loop for rows, one for columns:

```python
for row in grid:
    for item in row:
        print(item, end=' ')
    print()
```

</details>

---

## 14. Tuples

A **tuple** is an immutable sequence — once created, it **cannot be changed**. Tuples use parentheses `()` instead of brackets `[]`.

### Creating a Tuple

```python
my_tuple = (10, 20, 30, 40, 50)
print(my_tuple[0])   # Output: 10
print(my_tuple[-1])  # Output: 50
```

### What Tuples Support ✅

- Subscript indexing (`my_tuple[0]`)
- The `in` operator
- `len()`, `min()`, `max()`
- Slicing (`my_tuple[1:3]`)
- Concatenation with `+`

### What Tuples Do NOT Support ❌

```
append()   insert()   remove()   reverse()   sort()
```

These methods **modify** the list — since tuples are immutable, they don't have them.

### Converting Between Lists and Tuples

```python
my_list = [1, 2, 3]
my_tuple = tuple(my_list)   # Convert list → tuple
print(my_tuple)              # Output: (1, 2, 3)

back_to_list = list(my_tuple)  # Convert tuple → list
print(back_to_list)             # Output: [1, 2, 3]
```

### Why Use Tuples?

1. **Faster** to process than lists
2. **Safer** — data cannot be accidentally changed
3. Some Python operations **require** tuples

**Quick Check:**

<details>
<summary>What is the difference between a list and a tuple in Python?</summary>

The main difference is **mutability**:

| Feature | List `[]` | Tuple `()` |
|---------|-----------|------------|
| Mutable (changeable)? | ✅ Yes | ❌ No |
| Can use `append()`, `sort()`, etc.? | ✅ Yes | ❌ No |
| Supports indexing and slicing? | ✅ Yes | ✅ Yes |
| Faster to process? | ❌ Slower | ✅ Faster |

```python
my_list  = [1, 2, 3]   # Can be changed
my_tuple = (1, 2, 3)   # Cannot be changed

my_list[0] = 99    # ✅ Works fine
my_tuple[0] = 99   # ❌ TypeError!
```

</details>

<details>
<summary>When should you use a tuple instead of a list?</summary>

Use a **tuple** when:
- The data should **not change** (e.g., days of the week, coordinates, RGB color values)
- You want to protect data from accidental modification
- You need a small performance boost (tuples are faster than lists)
- A Python function requires a tuple as input

```python
# Good use of a tuple — days won't change
days = ('Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun')

# Good use of a list — scores change throughout the semester
scores = [88, 92, 75]
scores.append(95)
```

As a rule of thumb: if your data is **fixed**, use a tuple. If your data will **grow or change**, use a list.

</details>

---

## 15. Practice Assignments

The following exercises are to be completed in class. Read each section carefully and follow all TODO instructions in the comments.

---

### 🔹 Practice 1 — Creating and Accessing a List

**Concepts covered:** List creation, indexing, negative indexing

```python
# TODO:
# 1. Create a list named numbers with the values: 10, 20, 30, 40, 50
# 2. Print the entire list
# 3. Print the first element (index 0)
# 4. Print the last element using a negative index
```

> 💡 **Hint:** Recall that the first index is `0` and the last is `-1`.

**Quick Check:**

<details>
<summary>How do you access the last element of a list using a negative index?</summary>

Use index `-1` to access the last element — no matter how long the list is:

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[0])    # Output: 10  — first element
print(numbers[-1])   # Output: 50  — last element
```

This is better than using `numbers[4]` because `-1` always works even if the list length changes.

**Expected output for this practice:**
```
[10, 20, 30, 40, 50]
10
50
```

</details>

---

### 🔹 Practice 2 — Looping Through a List

**Concepts covered:** `for` loops, `len()`

```python
# TODO:
# 1. Create a list named fruits with at least 3 items
# 2. Use a for loop to print each item in the list
# 3. Print the length of the list using len()
```

> 💡 **Hint:** Use `for item in my_list:` to loop through each element.

**Quick Check:**

<details>
<summary>How do you loop through a list and print its length in Python?</summary>

Use a `for` loop to iterate through each item, then call `len()` to get the count:

```python
fruits = ['apple', 'banana', 'cherry']

for fruit in fruits:
    print(fruit)

print(len(fruits))
```

**Expected output:**
```
apple
banana
cherry
3
```

The `for` loop automatically moves through each element one at a time. `len()` counts how many elements exist in the list.

</details>

---

### 🔹 Practice 3 — List Operations

**Concepts covered:** `append()`, `insert()`, `sort()`, `reverse()`

```python
# TODO:
# 1. Create a list named nums with values: 3, 1, 4
# 2. Use append() to add a new number
# 3. Use insert() to add a number at index 1
# 4. Sort the list
# 5. Reverse the list
# 6. Print the final list
```

> 💡 **Hint:** Order matters! Each step modifies the list before the next step runs.

**Quick Check:**

<details>
<summary>What does sort() do — and what happens when you call reverse() after it?</summary>

`.sort()` rearranges elements into **ascending order** (smallest to largest). `.reverse()` then flips the entire order, giving you **descending order**.

```python
nums = [3, 1, 4]
nums.append(2)     # [3, 1, 4, 2]
nums.insert(1, 9)  # [3, 9, 1, 4, 2]
nums.sort()        # [1, 2, 3, 4, 9]
nums.reverse()     # [9, 4, 3, 2, 1]
print(nums)        # Output: [9, 4, 3, 2, 1]
```

Note: the exact result depends on what number you chose to `append()` and `insert()`. The key idea is that each method changes the list permanently before the next line runs.

</details>

<details>
<summary>How does insert() work — and what happens to the other elements?</summary>

`insert(index, item)` places the new item **at** the given index. Every element that was at that position or after it **shifts one spot to the right**.

```python
nums = [10, 20, 30]
nums.insert(1, 99)
print(nums)   # Output: [10, 99, 20, 30]
#                               ↑
#                    inserted here; 20 and 30 shifted right
```

</details>

---

### 🔹 Practice 4 — Processing a List

**Concepts covered:** Accumulator pattern, total, average

```python
# TODO:
# 1. Create a list of 5 numbers
# 2. Use a loop to calculate the total of the list
# 3. Calculate the average
# 4. Print the total and average
```

> 💡 **Hint:** Start a `total = 0` variable before the loop. Average = total ÷ number of items.

**Quick Check:**

<details>
<summary>How do you calculate the total and average of a list using a loop?</summary>

Use an **accumulator variable** (`total`) that starts at `0` and adds each element inside the loop. Then divide by `len()` for the average:

```python
numbers = [10, 20, 30, 40, 50]

total = 0
for num in numbers:
    total += num          # Same as: total = total + num

average = total / len(numbers)

print('Total:', total)      # Output: Total: 150
print('Average:', average)  # Output: Average: 30.0
```

The accumulator pattern is one of the most important patterns in programming — you'll use it constantly!

</details>

---

### 🔹 Practice 5 — Debug the List Program

**Concepts covered:** Debugging, `append()` syntax, indexing syntax

The program below has **3 errors**. Find and fix them so it runs correctly.

```python
# Buggy Code:
numbers = [1, 2, 3]
numbers.append[4]          # Bug 1
for i in range(len(numbers)):
    print(numbers(i))      # Bug 2 & Bug 3
```

> 💡 **Hints to think about:**
> - Methods are called with `()` parentheses, not `[]` brackets
> - List indexing uses `[]` brackets, not `()` parentheses

**Quick Check:**

<details>
<summary>What are the 3 bugs and what does the fixed code look like?</summary>

Here's a breakdown of each bug:

| # | Buggy Code | Problem | Fix |
|---|-----------|---------|-----|
| 1 | `numbers.append[4]` | `append` is a method — methods need `()` not `[]` | `numbers.append(4)` |
| 2 | `print(numbers(i))` | `numbers` is a list — lists use `[]` for indexing, not `()` | `print(numbers[i])` |
| 3 | *(same line)* | Using `()` after a list name tells Python to **call** it like a function, which raises a `TypeError` | Same fix: use `[]` |

**Fixed Code:**
```python
numbers = [1, 2, 3]
numbers.append(4)              # ✅ parentheses for method call
for i in range(len(numbers)):
    print(numbers[i])          # ✅ brackets for list indexing
```

**Expected Output:**
```
1
2
3
4
```

</details>

<details>
<summary>What is the difference between parentheses () and brackets [] in Python?</summary>

They serve very different purposes:

| Symbol | Used For | Examples |
|--------|----------|---------|
| `()` | Calling functions and methods | `print()`, `len()`, `my_list.append()` |
| `[]` | Creating lists and accessing elements by index | `[1, 2, 3]`, `my_list[0]` |

Mixing them up is one of the most common beginner errors:

```python
my_list = [10, 20, 30]

my_list.append(40)   # ✅ method call uses ()
my_list.append[40]   # ❌ TypeError — can't subscript a method

print(my_list[0])    # ✅ index access uses []
print(my_list(0))    # ❌ TypeError — list is not callable with ()
```

</details>

---

## 📝 Key Terms Summary

| Term | Definition |
|------|------------|
| **Sequence** | An ordered collection of items |
| **List** | A mutable sequence created with `[]` |
| **Tuple** | An immutable sequence created with `()` |
| **Element** | A single item in a list or tuple |
| **Index** | The position number of an element (starts at 0) |
| **Mutable** | Can be changed after creation |
| **Immutable** | Cannot be changed after creation |
| **Slice** | A portion of a list using `[start:end]` |
| **List comprehension** | A concise one-line expression to build a list |
| **Accumulator** | A variable that collects a running total in a loop |
| **Nested list** | A list that contains other lists (2D list) |

---

*Chapter 7 — Starting Out with Python, Fifth Edition by Tony Gaddis*
