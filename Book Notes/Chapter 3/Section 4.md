# 3.3 Scan-Converting a Circle (Simple Explanation)

---

## 1. Why Circle Scan Conversion Is Special

A **circle is perfectly symmetric**.

👉 That means:

* If you find **one point** on a circle,
* You can find **many other points** without doing extra calculations.

This symmetry is the **key idea** behind efficient circle drawing.

---

## 2. Eight-Way Symmetry of a Circle ⭐ (VERY IMPORTANT)

A circle is symmetric in **8 directions**:

* Left ↔ Right
* Up ↔ Down
* Diagonals

So instead of calculating **all points**, we calculate points in **one small part** of the circle and **reflect them**.

👉 This is called **eight-way symmetry**.

---

## 3. Eight Symmetric Points from One Point

If one point on the circle is:

[
P_1 = (x, y)
]

Then the **7 other symmetric points** are:

| Point | Coordinates |
| ----- | ----------- |
| P₁    | ( x,  y)    |
| P₂    | ( y,  x)    |
| P₃    | (−y,  x)    |
| P₄    | (−x,  y)    |
| P₅    | (−x, −y)    |
| P₆    | (−y, −x)    |
| P₇    | ( y, −x)    |
| P₈    | ( x, −y)    |

👉 **One calculation → 8 pixels drawn**

📌 **Exam line to remember**:

> Circle algorithms use eight-way symmetry to reduce computation by plotting eight pixels for each calculated point.

---

## 4. Why Only One Sector Is Calculated

Because of symmetry, we only calculate points for **one octant** (from 0° to 45°).

Then we reflect those points to get the full circle.

✔ Faster
✔ Efficient
✔ Less computation

---

## 5. Mathematical Definition of a Circle (Method 1)

### Equation of a Circle (Centered at Origin)

[
x^2 + y^2 = r^2
]

Rewritten as:
[
y = \sqrt{r^2 - x^2}
]

Where:

* ( r ) = radius
* ( (x, y) ) = point on the circle

### How It Works

* Step x from **0 to ( \frac{r}{\sqrt{2}} )** (45° point)
* For each x, compute y using square root

### Why This Is BAD ❌

* Squaring numbers
* Subtraction
* Square root calculation
* Very slow

👉 **Not suitable for real-time graphics**

---

## 6. Mathematical Definition of a Circle (Method 2)

### Trigonometric Form

[
x = r \cos \theta
]
[
y = r \sin \theta
]

Where:

* ( \theta ) = angle
* ( r ) = radius

### How It Works

* Step ( \theta ) from 0° to 45°
* Compute sin and cos for each step

### Why This Is ALSO BAD ❌

* sin() and cos() are **very expensive**
* Slower than polynomial method

👉 Even worse for hardware graphics

---

## 7. Conclusion from Both Methods

| Method        | Problem          |
| ------------- | ---------------- |
| Polynomial    | Uses square root |
| Trigonometric | Uses sin & cos   |
| Result        | Too slow         |

👉 **We need a faster, integer-based method**

This leads to the **Midpoint Circle Algorithm / Bresenham Circle Algorithm** (next topic).

---

## 8. Key Exam Points (Write These ✔)

* A circle has **eight-way symmetry**
* One calculated point gives **7 more points**
* Only one octant (0°–45°) is computed
* Polynomial and trigonometric methods are **inefficient**
* Fast circle algorithms avoid:

  * square root
  * sin/cos
  * floating-point math

---

## 9. One-Line Exam Summary ⭐

> **Scan-converting a circle uses eight-way symmetry to efficiently plot pixels by calculating points in one octant and reflecting them to form the full circle.**
