## 1. What is scan conversion (rasterization)?

In computer graphics:

* **Geometric primitives** (point, line, circle, polygon) are defined in **continuous space**

  * Coordinates are **real numbers** (e.g., 1.7, 2.35)
* **Images** are made of **pixels**

  * Pixel coordinates are **integers** (0,1,2,…)

👉 **Scan conversion (rasterization)** is the process of:

> Converting continuous geometric descriptions into a set of discrete pixels.

---

## 2. Why scan conversion is needed

Examples:

* A **line** → infinite points mathematically, but only pixels can be drawn
* A **circle** → smooth curve mathematically, but pixels are square blocks

So the system must:
✔ Decide **which pixels best approximate** the shape
✔ Do it **efficiently and accurately**

---

## 3. Scan-converting a point (basic idea)

A mathematical point:
[
(x, y) \quad \text{where } x,y \in \mathbb{R}
]

Must be mapped to a pixel:
[
(x', y') \quad \text{where } x',y' \in \mathbb{Z}
]

This is done by **rounding or flooring** the coordinates.

---

## 4. Method 1: Floor method (pixel corner alignment)

### Formula

[
x' = \lfloor x \rfloor,\quad y' = \lfloor y \rfloor
]

* `Floor(x)` = largest integer ≤ x
* Continuous origin is at the **lower-left corner of pixel (0,0)**

---

### Interpretation

All points inside this region:
[
x' \le x < x' + 1,\quad y' \le y < y' + 1
]
map to pixel ((x', y'))

---

### Examples

| Point (x, y) | Floor(x) | Floor(y) | Pixel |
| ------------ | -------- | -------- | ----- |
| (1.7, 0.8)   | 1        | 0        | (1,0) |
| (2.2, 1.3)   | 2        | 1        | (2,1) |
| (2.8, 1.9)   | 2        | 1        | (2,1) |

✔ Multiple points can map to **the same pixel**

---

### Key idea

* Pixel represents the **unit square**
* Point is assigned to the square it falls into

---

## 5. Method 2: Rounding method (pixel center alignment)

### Formula

[
x' = \lfloor x + 0.5 \rfloor,\quad y' = \lfloor y + 0.5 \rfloor
]

This is equivalent to **rounding to the nearest integer**.

---

### Interpretation

* Continuous coordinate origin is placed at the **center of pixel (0,0)**
* A point maps to the **nearest pixel center**

Points in:
[
x' - 0.5 < x < x' + 0.5,\quad y' - 0.5 < y < y' + 0.5
]
map to pixel ((x', y'))

---

### Examples

| Point (x, y) | x+0.5 | y+0.5 | Pixel |
| ------------ | ----- | ----- | ----- |
| (1.7, 0.8)   | 2.2   | 1.3   | (2,1) |
| (2.2, 1.3)   | 2.7   | 1.8   | (2,1) |
| (2.8, 1.9)   | 3.3   | 2.4   | (3,2) |

✔ Different from the floor method

---

## 6. Why two methods exist

| Method | Pixel reference | Used when                         |
| ------ | --------------- | --------------------------------- |
| Floor  | Pixel corner    | Simple grid logic                 |
| Round  | Pixel center    | More symmetric, visually accurate |

👉 Most modern graphics systems prefer **round-to-nearest (center-based)** mapping.

---

## 7. Why this matters in graphics

* Errors at point level affect:

  * Lines
  * Circles
  * Polygons
* Small rounding differences cause:

  * Jagged edges
  * Bias toward one direction

This is why later chapters introduce:
✔ Line algorithms (Bresenham)
✔ Anti-aliasing
✔ Smoothing techniques

---

## 8. One-line exam summary ⭐

> **Scan conversion maps continuous geometric primitives to discrete pixel locations. A point (x,y) is converted to pixel (⌊x⌋,⌊y⌋) or (⌊x+0.5⌋,⌊y+0.5⌋) depending on whether pixel corners or centers are used as references.**
