## 1. Why Bresenham’s Algorithm is Needed

When we draw a line on paper, it’s smooth.
But a computer screen is made of **pixels (small squares)**.

So the problem is:

> **Which pixels should be turned on so the line looks as close as possible to a real straight line?**

Earlier methods:

* **Direct line equation** → slow (floating-point math every step)
* **DDA algorithm** → faster, but still uses floating-point addition and can accumulate errors

👉 **Bresenham’s algorithm solves this efficiently using only integers.**

---

## 2. Basic Idea (Intuition)

Assume:

* We are drawing a line from **left to right**
* The slope is **between 0 and 1** (i.e., the line goes right and slightly up)

At each step:

* We move **one pixel to the right**
* Then we must decide:

  * **Stay at the same height (go right)** → pixel **S**
  * **Go right and up** → pixel **T**

💡 The decision is made by checking **which pixel is closer to the real line**.

---

## 3. Pixel Choice at Each Step

For every new x-position:

```
T  ← upper-right pixel
|
S  ← right pixel
```

We choose:

* **S** if the real line is closer to S
* **T** if the real line is closer to T

To do this **without floating-point math**, Bresenham uses a **decision variable `d`**.

---

## 4. Decision Variable (d) – Simple Meaning

* `d` tells us **whether the real line is above or below the midpoint** between S and T
* Based on `d`, we decide which pixel is closer

Decision rule:

* **If d < 0** → choose **S** (right pixel)
* **If d ≥ 0** → choose **T** (right + up pixel)

---

## 5. Why It’s Fast

Bresenham:

* Uses **only integer addition and subtraction**
* No multiplication
* No floating-point numbers
* No rounding

This makes it:

* **Very fast**
* **Very accurate**
* Ideal for hardware and real-time graphics

---

## 6. Initial Setup

Given endpoints:

```
P1(x1, y1)
P2(x2, y2)
```

Compute:

```
dx = x2 - x1
dy = y2 - y1
```

Initial decision variable:

```
d = 2*dy - dx
```

Other constants:

```
dS = 2*dy           (if we choose S)
dT = 2*(dy - dx)    (if we choose T)
```

---

## 7. Step-by-Step Algorithm (0 < m < 1)

1. Start at `(x1, y1)`
2. Turn on the first pixel
3. Repeat until `x == x2`:

   * Move one step right: `x = x + 1`
   * If `d < 0`:

     * Choose **S** (same y)
     * `d = d + dS`
   * Else:

     * Choose **T** (y = y + 1)
     * `d = d + dT`
   * Turn on the chosen pixel

---

## 8. Pseudocode (Easy Version)

```c
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
        d = d + dS;        // choose S
    } else {
        y = y + 1;         // choose T
        d = d + dT;
    }

    setPixel(x, y);
}
```

---

## 9. What About Other Slopes?

Bresenham handles **all line directions** by symmetry:

| Slope Range     | Trick Used             |
| --------------- | ---------------------- |
| 0 < m < 1       | Use algorithm directly |
| -1 < m < 0      | Mirror horizontally    |
| m > 1           | Swap x and y           |
| m < -1          | Swap + mirror          |
| Vertical line   | Special case           |
| Horizontal line | Special case           |

This avoids writing multiple algorithms.

---

## 10. Key Advantages (Exam-Friendly Points)

* ✔ Uses only **integer arithmetic**
* ✔ No cumulative floating-point error
* ✔ Very **fast**
* ✔ Produces **accurate, visually smooth lines**
* ✔ Widely used in **graphics hardware**

---

## 11. One-Line Summary

> **Bresenham’s line algorithm draws a straight line by choosing, at each step, the pixel closest to the true line using only fast integer calculations.**
