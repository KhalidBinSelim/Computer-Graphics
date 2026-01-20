# 3.2 Scan-Converting a Line (Simple Explanation)

## 1. What does “scan-converting a line” mean?

In mathematics, a line is **continuous** and has infinitely many points.

But on a screen:

* We only have **pixels**
* Pixels have **integer coordinates**

👉 **Scan-converting a line** means:

> Selecting the best sequence of pixels that visually represent a straight line between two points.

---

## 2. How is a line defined?

A line segment is defined by:

* Two endpoints
  [
  P_1(x_1, y_1),\quad P_2(x_2, y_2)
  ]
* Line equation:
  [
  y = mx + b
  ]
  where:
* (m =) slope
* (b =) y-intercept

The equation tells us **all the points** lying between the two endpoints.

---

## 3. Important note (VERY EXAM-IMPORTANT)

The equation (y = mx + b) **does NOT work for vertical lines**
(because slope is infinite).

👉 Therefore:

* **Horizontal lines**
* **Vertical lines**
* **Diagonal lines (|m| = 1)**

are often handled as **special cases** for:

* Simpler logic
* Faster execution

---

## 4. Method 1: Direct use of the line equation

### Step-by-step idea:

1. Scan-convert endpoints:
   [
   (x_1, y_1) \rightarrow (x'_1, y'_1),\quad (x_2, y_2) \rightarrow (x'_2, y'_2)
   ]

2. Compute slope and intercept:
   [
   m = \frac{y'_2 - y'_1}{x'_2 - x'_1},\quad b = y'_1 - mx'_1
   ]

3. Decide which axis to step through:

   * If (|m| < 1) → step through **x**
   * If (|m| > 1) → step through **y**

4. For each step:

   * Compute the other coordinate using the equation
   * Scan-convert the point to the nearest pixel

---

### ❌ Problems with this method

* Requires **floating-point multiplication**
* Slow
* Repeats expensive calculations
* Not suitable for real-time graphics

👉 Hence, a faster method is needed.

---

## 5. DDA Algorithm (Digital Differential Analyzer)

### Core idea (VERY SIMPLE):

> Instead of recomputing the line equation every time, **use the previous point to compute the next point**.

This is called an **incremental algorithm**.

---

## 6. Mathematical foundation of DDA

Slope definition:
[
m = \frac{\Delta y}{\Delta x}
]

Rearranged:
[
\Delta y = m \cdot \Delta x
]

This means:

* If x increases by 1 → y increases by **m**
* If y increases by 1 → x increases by **1/m**

---

## 7. DDA when |m| < 1 (gentle slope)

### Situation:

* Line is more **horizontal**
* x changes faster than y

### Steps:

1. Start at:
   [
   x = x'_1,\quad y = y'_1
   ]

2. Set:
   [
   \Delta x = 1
   ]

3. Update:
   [
   y_{i+1} = y_i + m
   ]

4. For each step:

   * Plot pixel at ((round(x), round(y)))
   * Increase x by 1
   * Update y incrementally

5. Stop when x reaches (x'_2)

---

### Intuition:

* Move **1 pixel right**
* Move **m pixels up/down**

---

## 8. DDA when |m| > 1 (steep slope)

### Situation:

* Line is more **vertical**
* y changes faster than x

### Steps:

1. Start at:
   [
   x = x'_1,\quad y = y'_1
   ]

2. Set:
   [
   \Delta y = 1
   ]

3. Update:
   [
   x_{i+1} = x_i + \frac{1}{m}
   ]

4. For each step:

   * Plot pixel at ((round(x), round(y)))
   * Increase y by 1
   * Update x incrementally

5. Stop when y reaches (y'_2)

---

### Intuition:

* Move **1 pixel up**
* Move **1/m pixels sideways**

---

## 9. Why DDA is faster than direct method

✅ No multiplication per step
✅ Uses simple additions
❌ Still uses floating-point numbers
❌ Floating-point rounding error accumulates

---

## 10. Major drawback of DDA (exam point)

Because DDA uses floating-point arithmetic:

* Small rounding errors add up
* Long lines may **drift away** from the true line

👉 This leads to the development of:

> **Bresenham’s line algorithm** (integer-only, faster, more accurate)

---

## 11. One-page exam summary

You can safely write this:

* Scan-conversion converts a continuous line into pixels
* Direct method uses line equation but is slow
* DDA is an incremental method
* If |m| < 1 → increment x, compute y = y + m
* If |m| > 1 → increment y, compute x = x + 1/m
* DDA is faster but suffers from floating-point error accumulation

---

## 12. One-line intuition (remember this!)

> **DDA draws a line by taking one small step at a time and using the previous point to find the next one.**
