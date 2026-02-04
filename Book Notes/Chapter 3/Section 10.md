
# 3.5 SCAN-CONVERTING ARCS AND SECTORS



## A. Scan-Converting Arcs

### What is an Arc?

An **arc** is a **portion of a circle**, defined between two angles or two points.



<img width="829" height="738" alt="image" src="https://github.com/user-attachments/assets/8710c3e8-1c1c-4282-93c7-be586378356a" />


## Why Bresenham’s Circle Algorithm Is BAD for Arcs ❌

Although arcs are part of circles, **Bresenham’s algorithm is not suitable** because:

* It generates points using **8-way symmetry**
* Each reflected point must be **tested** to check if it lies between arc endpoints
* Endpoints may be **missed**
* Can cause **infinite loops**
* Must test **every point** on the circle

📌 **Conclusion:** Bresenham is efficient for full circles, **not arcs**.

---

## B. Scan-Converting Sectors

### What is a Sector?

A **sector** consists of:

* An **arc**
* Two **radius lines** from the center to the arc endpoints

---

<img width="855" height="664" alt="image" src="https://github.com/user-attachments/assets/dc47e5fd-d3e4-4a5e-b7dc-24bc2d629d3c" />


### Steps to Draw Rectangle

Use **line scan-conversion** for four edges:

1. ((x_1,y_1) → (x_1,y_2))
2. ((x_1,y_2) → (x_2,y_2))
3. ((x_2,y_2) → (x_2,y_1))
4. ((x_2,y_1) → (x_1,y_1))

✔ Simple
✔ Efficient

---

# 3.7 REGION FILLING

---

## What Is Region Filling?

Region filling means **coloring all pixels inside a closed area**.

---

## Types of Regions

### 1️⃣ Boundary-Defined Region

* Region defined by **boundary pixels**
* Filling stops when boundary color is reached
* Uses **Boundary-Fill algorithms**

---

### 2️⃣ Interior-Defined Region

* Region defined by **connected interior pixels**
* Filling spreads until a boundary is encountered
* Uses **Flood-Fill algorithms**

---

## Pixel Connectivity

Because pixels are discrete, **connectivity matters**.

---

### 4-Connected Pixels

Each pixel has **4 neighbors**:

* Up
* Down
* Left
* Right

📌 Diagonal pixels are **NOT connected**

---

### 8-Connected Pixels

Each pixel has **8 neighbors**:

* 4 direct + 4 diagonal

📌 Diagonal pixels **ARE connected**

---

## Why We Must Mix Connectivity Rules ⚠️

To avoid contradictions:

* **Boundary pixels → 8-connected**
* **Interior pixels → 4-connected**

If the same rule is used for both:

* Either the boundary breaks
* Or the region leaks to outside

✔ Using different connectivity avoids ambiguity
✔ Ensures a properly closed region

---

## Exam Gold Points ⭐

* Arcs: **Use trigonometric method**
* Bresenham is **unsafe for arcs**
* Sector = **arc + two lines**
* Rectangle = **4 lines**
* Region filling types:

  * Boundary-fill
  * Flood-fill
* Boundary → **8-connected**
* Interior → **4-connected**

---

## One-Line Exam Answers ⭐

**Arc scan conversion:**

> Arcs are scan-converted using polynomial or trigonometric methods, with the trigonometric method preferred because it avoids symmetry and endpoint errors.

**Sector scan conversion:**

> A sector is scan-converted by drawing an arc and two radial lines from the center to the arc endpoints.

**Region filling:**

> Region filling is the process of coloring all pixels inside a closed region using boundary-fill or flood-fill algorithms.
