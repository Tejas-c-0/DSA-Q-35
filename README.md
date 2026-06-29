# 🚀 LeetCode 150 — Evaluate Reverse Polish Notation

<p align="center">
  <img src="https://img.shields.io/badge/Language-Python-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Difficulty-Medium-orange?style=for-the-badge">
  <img src="https://img.shields.io/badge/Pattern-Stack-success?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Solved-brightgreen?style=for-the-badge">
</p>

---

# 🖼️ Problem Overview

> Evaluate the value of an arithmetic expression written in **Reverse Polish Notation (RPN)**.

Supported operators:

- ➕ Addition
- ➖ Subtraction
- ✖ Multiplication
- ➗ Division

Each operand may be an integer or another expression.

---

# 🧠 Pattern Used

```text
Stack
```

---

# 💡 Intuition

Instead of evaluating from left to right like normal mathematics, Reverse Polish Notation evaluates expressions using a **Stack**.

### Rules

✅ Number → Push into the stack

✅ Operator → Pop two numbers, perform the operation, and push the result back.

---

# 🏗️ Visual Dry Run

Input

```text
["2","1","+","3","*"]
```

### Step 1

```
Read: 2

Stack
┌───┐
│ 2 │
└───┘
```

---

### Step 2

```
Read: 1

Stack
┌───┐
│ 1 │
├───┤
│ 2 │
└───┘
```

---

### Step 3

Read **+**

```
Pop 1
Pop 2

2 + 1 = 3
```

Push back

```
┌───┐
│ 3 │
└───┘
```

---

### Step 4

Read **3**

```
┌───┐
│ 3 │
├───┤
│ 3 │
└───┘
```

---

### Step 5

Read *

```
3 × 3 = 9
```

Final Stack

```
┌───┐
│ 9 │
└───┘
```

Answer

```text
9
```

---

# ⚙️ Algorithm

```
Create an empty stack

For every token

    If number
        Push into stack

    Else

        Pop num2
        Pop num1

        Perform operation

        Push answer back

Return top of stack
```

---

# 💻 Python Solution

```python
class Solution(object):
    def evalRPN(self, tokens):
        stack = []

        for token in tokens:

            if token not in "+-*/":
                stack.append(int(token))

            else:
                num2 = stack.pop()
                num1 = stack.pop()

                if token == "+":
                    stack.append(num1 + num2)

                elif token == "-":
                    stack.append(num1 - num2)

                elif token == "*":
                    stack.append(num1 * num2)

                else:
                    stack.append(int(float(num1) / num2))

        return stack[-1]
```

---

# 📊 Complexity Analysis

| Operation | Complexity |
|-----------|-----------:|
| Traversing Tokens | O(n) |
| Stack Operations | O(1) |
| Overall Time | **O(n)** |
| Space | **O(n)** |

---

# 🎯 Key Learning

- ✅ Stack follows **LIFO (Last In, First Out)**.
- ✅ Operators always use the last two operands.
- ✅ Operand order matters for subtraction and division.
- ✅ Reverse Polish Notation is widely used in expression evaluation.

---

# 🛠️ Technologies

- Python 🐍
- Stack
- Algorithms
- Data Structures

---

## ⭐ If you found this solution helpful, consider starring the repository!
