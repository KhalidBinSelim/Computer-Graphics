# Midpoint Circle Algorithm 

## 1. Core Idea (Why “Midpoint”?)

Instead of computing distances or angles, we use a **simple test function** to decide:

> Is a point **inside**, **on**, or **outside** the circle?

This lets us choose the **closest pixel** using **integer arithmetic**.

---

## 2. Circle Test Function

For a circle of radius **r** centered at the origin:

[
f(x, y) = x^2 + y^2 - r^2
]

Meaning:

| Value of f(x, y) | Point Position     |
| ---------------- | ------------------ |
| (f(x,y) < 0)     | Inside the circle  |
| (f(x,y) = 0)     | On the circle      |
| (f(x,y) > 0)     | Outside the circle |

👉 This function replaces distance calculation.

---

## 3. Two Pixel Choices (Same as Bresenham)

While generating points from **90° to 45°**:

From current pixel ((x_i, y_i)), next pixel is either:

```
T : (x+1, y)        → right
S : (x+1, y−1)      → right & down
```

Which one is closer to the true circle?

---

## 4. Midpoint Decision Parameter ⭐

We test the **midpoint between T and S**:

[
\text{Midpoint} = (x_i + 1,; y_i - \tfrac{1}{2})
]

Decision parameter:
[
p_i = f(x_i + 1,; y_i - \tfrac{1}{2})
]

### Decision Rule

* **If (p_i < 0)** → midpoint is **inside** → choose **T**
* **If (p_i \ge 0)** → midpoint is **outside/on** → choose **S**

👉 No floating-point computation is actually required in implementation.

---

## 5. Initial Value of Decision Parameter

Starting point:
[
(x_0, y_0) = (0, r)
]

Initial decision parameter:
[
p_0 = 1 - r
]

📌 Even though the exact value differs slightly, **the sign is correct**, which is all we need.

---

## 6. Incremental Update Rules (Easy to Remember)

### If **T** is chosen ((p < 0)):

* y remains the same
  [
  p = p + 2x + 3
  ]

### If **S** is chosen ((p \ge 0)):

* y decreases by 1
  [
  p = p + 2(x - y) + 5
  ]

In both cases:

* x always increases by 1

---

## 7. Complete Algorithm (Exam-Perfect)

```c
int x = 0;
int y = r;
int p = 1 - r;

while (x <= y) {
    setPixel(x, y);   // plus 7 symmetric points

    if (p < 0) {
        p = p + 2*x + 3;
    } else {
        p = p + 2*(x - y) + 5;
        y--;
    }
    x++;
}
```

---

## 8. Relation to Bresenham’s Circle Algorithm

| Midpoint Circle               | Bresenham Circle   |
| ----------------------------- | ------------------ |
| Concept-based (midpoint test) | Distance-based     |
| Easier to understand          | Slightly faster    |
| Integer arithmetic            | Integer arithmetic |
| Same pixel output             | Same pixel output  |

👉 **In practice, both produce identical circles.**

---

## 9. Arbitrarily Centered Circles (Very Easy ⭐)

So far, we assumed the circle is centered at **(0,0)**.

For a circle centered at ((x_c, y_c)):

Just shift every pixel:
[
(x, y) \rightarrow (x + x_c,; y + y_c)
]

### Code Change Only:

```c
setPixel(x + xc, y + yc);
```

That’s it.

---

## 10. Key Exam Points ✔

* Uses **midpoint test function**
* Decision parameter determines pixel choice
* Only **one octant** is computed
* Uses **eight-way symmetry**
* Integer-only incremental algorithm
* Easily extended to **arbitrary center**

---

## 11. One-Line Exam Summary ⭐

> **The midpoint circle algorithm scan-converts a circle by testing the midpoint between candidate pixels using a decision parameter and integer arithmetic.**

