# 📌 `map()`, `filter()`, and `reduce()` in Python

These are **functional programming tools** in Python. They let you apply functions to iterables (like lists, tuples, sets) in a clean and concise way.

---

## 🔹 1. `map()`

* **Definition**: Applies a given function to **every element** of an iterable.
* **Syntax**:

  ```python
  map(function, iterable)
  ```
* Returns a **map object** (iterator). Usually converted to a list or tuple.

### ✅ Example 1: Squaring numbers

```python
numbers = [1, 2, 3, 4, 5]

def square(x):
    return x ** 2

result = map(square, numbers)
print(list(result))  # [1, 4, 9, 16, 25]
```

### ✅ Example 2: Using `lambda` with map

```python
numbers = [1, 2, 3, 4, 5]
result = map(lambda x: x * 2, numbers)
print(list(result))  # [2, 4, 6, 8, 10]
```

### ✅ Example 3: Multiple iterables

```python
a = [1, 2, 3]
b = [4, 5, 6]

result = map(lambda x, y: x + y, a, b)
print(list(result))  # [5, 7, 9]
```

---

## 🔹 2. `filter()`

* **Definition**: Filters elements of an iterable based on a condition (returns only those for which the function returns `True`).
* **Syntax**:

  ```python
  filter(function, iterable)
  ```

### ✅ Example 1: Even numbers

```python
numbers = [1, 2, 3, 4, 5, 6]

def is_even(x):
    return x % 2 == 0

result = filter(is_even, numbers)
print(list(result))  # [2, 4, 6]
```

### ✅ Example 2: Using `lambda`

```python
numbers = [10, 25, 30, 47, 50]
result = filter(lambda x: x > 25, numbers)
print(list(result))  # [30, 47, 50]
```

---

## 🔹 3. `reduce()`

* **Definition**: Applies a function cumulatively to the items of an iterable.
* It’s like **rolling computation** (reduce the iterable into a single value).
* **Import needed**:

  ```python
  from functools import reduce
  ```
* **Syntax**:

  ```python
  reduce(function, iterable[, initializer])
  ```

### ✅ Example 1: Sum of numbers

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]

def add(x, y):
    return x + y

result = reduce(add, numbers)
print(result)  # 15
```

### ✅ Example 2: Product of numbers

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x * y, numbers)
print(result)  # 120
```

### ✅ Example 3: Maximum value

```python
from functools import reduce

numbers = [10, 20, 5, 8, 100, 3]

result = reduce(lambda a, b: a if a > b else b, numbers)
print(result)  # 100
```

---

## 📊 Summary Table

| Function   | Purpose                            | Example Input           | Example Output |
| ---------- | ---------------------------------- | ----------------------- | -------------- |
| `map()`    | Transform each element             | `[1,2,3]` with `x*2`    | `[2,4,6]`      |
| `filter()` | Select elements based on condition | `[1,2,3,4]` with `even` | `[2,4]`        |
| `reduce()` | Reduce iterable to single value    | `[1,2,3,4]` with sum    | `10`           |

---

## 🚀 Practical Example: Processing Student Scores

```python
from functools import reduce

scores = [45, 67, 89, 34, 76, 90]

# 1. Increase all scores by 5 using map
updated = list(map(lambda x: x + 5, scores))

# 2. Filter only passing students (>= 50)
passed = list(filter(lambda x: x >= 50, updated))

# 3. Find the total marks of all passed students using reduce
total = reduce(lambda x, y: x + y, passed)

print("Updated Scores:", updated)
print("Passed Students:", passed)
print("Total Marks:", total)
```

### Output:

```
Updated Scores: [50, 72, 94, 39, 81, 95]
Passed Students: [50, 72, 94, 81, 95]
Total Marks: 392
```

---

## 📝 Homework

1. Create a list of temperatures in **Celsius**:
`temps_c = [25, 30, 35, 40]`

* Use `map()` to convert them to **Fahrenheit** using the formula
  $(°C × 9/5) + 32 = °F$
* Print the list of converted temperatures.


2. Create a list of city names:
`cities = ["Bengaluru", "Mysuru", "Mandya", "Hubballi", "Ballari", "Hassan"]`

* Use `filter()` to get all city names that **start with the letter 'M'**.
* Print the resulting list.


3. Given a list of student scores:
`scores = [45, 67, 89, 34, 76, 90]`

* Use `reduce()` to find the **highest score** in the list.
* Print the highest score.


4. Given marks of students:
`marks = [35, 50, 66, 20, 88, 75]`

* Use `map()` to **add 10 bonus marks** to each student.
* Use `filter()` to **keep only students who now have 50 or more**.
* Use `reduce()` to **calculate the total marks of passed students**.
* Print the updated marks, passed marks, and total marks.


