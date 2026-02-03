
## Bresenham’s Line Algorithm (Simple & Exam-Oriented Explanation)


## 1. Why Bresenham’s Algorithm Is Needed

* A **real line** on paper is smooth
* A **computer screen** is made of **pixels (squares)**

👉 So the main problem is:

> **Which pixels should be turned on so the line looks closest to a straight line?**

Earlier methods had issues:

* **Direct line equation** → slow (floating-point math every step)
* **DDA** → faster, but still uses floating-point numbers
  → rounding errors accumulate

👉 **Bresenham’s algorithm** solves this by using **only integers**.

---

## 2. Basic Idea (Strong Intuition ⭐)

Assume:

* We draw the line **from left to right**
* Slope is **between 0 and 1** (line goes right and slightly up)

At each step:

* We **must move one pixel to the right**
* Now we must decide between **two pixels**:

```
T  (right + up)
|
S  (right)
```

👉 The question is:
**Which pixel is closer to the real line?**

Bresenham answers this using a **decision variable**.

---

## 3. Pixel Choice at Each Step

For every new x-position:

* **S** → move right (same y)
* **T** → move right and up (y + 1)

We choose the pixel that is **closer to the true line**
without using floating-point math.

---

## 4. Decision Variable (d) – Simple Meaning

The decision variable **d** tells us:

> Is the real line **above or below** the midpoint between S and T?

Decision rule:

* **If d < 0** → choose **S** (right pixel)
* **If d ≥ 0** → choose **T** (right + up pixel)

That’s it.
No slope calculation, no rounding.

---

## 5. Why Bresenham Is Fast 🚀

Bresenham:

* ✔ Uses **only integer addition & subtraction**
* ✔ No multiplication
* ✔ No floating-point numbers
* ✔ No rounding

So it is:

* **Very fast**
* **Very accurate**
* **Perfect for hardware & real-time graphics**

---

## 6. Initial Setup

Given endpoints:
[
P_1(x_1, y_1),\quad P_2(x_2, y_2)
]

Compute:
[
dx = x_2 - x_1,\quad dy = y_2 - y_1
]

Initial decision variable:
[
d = 2dy - dx
]

Constants:

* ( d_S = 2dy )  (when choosing S)
* ( d_T = 2(dy - dx) )  (when choosing T)

---

## 7. Step-by-Step Algorithm (For (0 < m < 1))

1. Start at ((x_1, y_1))
2. Turn on the first pixel
3. Repeat until (x = x_2):

* Move right: ( x = x + 1 )

**If ( d < 0 ):**

* Choose **S**
* ( d = d + d_S )

**Else:**

* Choose **T**
* ( y = y + 1 )
* ( d = d + d_T )

4. Turn on the selected pixel

---

## 8. Pseudocode (Exam-Perfect)

```text
x = x1;
y = y1;
dx = x2 - x1;
dy = y2 - y1;

d  = 2*dy - dx;
dS = 2*dy;
dT = 2*(dy - dx);

setPixel(x, y);

while (x < x2) {
    x = x + 1;

    if (d < 0) {
        d = d + dS;      // choose S
    } else {
        y = y + 1;       // choose T
        d = d + dT;
    }

    setPixel(x, y);
}
```

---

## 9. What About Other Slopes? (EXAM TABLE ⭐)

| Slope Range     | Technique           |
| --------------- | ------------------- |
| (0 < m < 1)     | Use directly        |
| (-1 < m < 0)    | Mirror horizontally |
| (m > 1)         | Swap x and y        |
| (m < -1)        | Swap + mirror       |
| Vertical line   | Special case        |
| Horizontal line | Special case        |

👉 This avoids writing multiple algorithms.

---

## 10. Key Advantages (Write These in Exams ✔)

* ✔ Uses only integer arithmetic
* ✔ No cumulative floating-point error
* ✔ Very fast
* ✔ Accurate and visually smooth
* ✔ Widely used in graphics hardware

---

## 11. One-Line Exam Summary ⭐

> **Bresenham’s line algorithm draws a straight line by selecting, at each step, the pixel closest to the true line using fast integer-only calculations.**

