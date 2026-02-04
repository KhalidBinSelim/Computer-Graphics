# Bresenham’s Circle Algorithm (Simple & Clear)

## 1. Why Bresenham’s Circle Algorithm Is Needed

To draw a circle efficiently, we must **avoid**:

* ❌ Trigonometric functions (sin, cos)
* ❌ Square root and power functions
* ❌ Floating-point arithmetic

Just like line drawing, we want:

* ✔ Integer-only calculations
* ✔ Fast execution
* ✔ Accurate pixels

👉 **Bresenham’s circle algorithm** achieves this using:
**integer addition, subtraction, and shifts (×2)** only.

---

## 2. Key Observations (Very Important)

### (a) Eight-way symmetry

A circle is symmetric in **8 directions**.
So if we compute **one point**, we can plot **7 more** by reflection.

👉 Therefore:

* We only compute points from **90° to 45°** (one octant)
* All other points come from symmetry

---

### (b) Direction of movement (90° → 45°)

Starting point:
[
(0, r)
]

While moving from 90° to 45°:

* (x) **always increases** (+x)
* (y) **either stays same or decreases** (−y)

So at every step, there are **only two choices**.

---

## 3. Pixel Choices at Each Step (Core Idea ⭐)

From the current pixel ((x_i, y_i)), the next pixel is either:

```
T : (x+1, y)       → move right
S : (x+1, y−1)     → move right & down
```

👉 The problem becomes:

> Which pixel is **closer to the true circle**?

We decide this using a **decision variable d**.

---

## 4. Decision Variable (Intuition Only – No Heavy Math)

The decision variable **d** tells us:

> Is the midpoint between T and S **inside or outside** the true circle?

Decision rule:

* **If d < 0** → midpoint is inside → choose **T**
* **If d ≥ 0** → midpoint is outside → choose **S**

That’s it.
No distance, no square root, no floating point.

---

## 5. Initial Values

Start at the **top of the circle**:

```
x = 0
y = r
```

Initial decision variable:
[
d = 3 - 2r
]

This value comes from the circle equation but is **precomputed once**.

---

## 6. How d Is Updated (Very Easy Rules)

### If T is chosen (d < 0):

* y stays the same
* Update:
  [
  d = d + 4x + 6
  ]

### If S is chosen (d ≥ 0):

* y decreases by 1
* Update:
  [
  d = d + 4(x - y) + 10
  ]

In both cases:

* **x always increases by 1**

---

## 7. Complete Algorithm (Exam-Perfect Version)

```c
int x = 0;
int y = r;
int d = 3 - 2*r;

while (x <= y) {
    setPixel(x, y);      // plus 7 symmetric points

    if (d < 0) {
        d = d + 4*x + 6;
    } else {
        d = d + 4*(x - y) + 10;
        y--;
    }
    x++;
}
```

📌 Note:

* Loop runs only for **one octant**
* Each `setPixel(x,y)` actually plots **8 symmetric points**

---

## 8. Why Bresenham’s Circle Algorithm Is Efficient

✔ Uses only integers
✔ No square root
✔ No sin/cos
✔ No floating-point error
✔ Very fast
✔ Ideal for hardware implementation

---

## 9. Key Exam Points (Must Remember ⭐)

* Uses **eight-way symmetry**
* Computes points only from **90° to 45°**
* At each step, chooses between **(x+1, y)** and **(x+1, y−1)**
* Uses a **decision variable**
* Integer-only incremental algorithm

---

## 10. One-Line Exam Summary ⭐

> **Bresenham’s circle algorithm efficiently scan-converts a circle by selecting at each step the pixel closest to the true circle using only integer arithmetic and eight-way symmetry.**
