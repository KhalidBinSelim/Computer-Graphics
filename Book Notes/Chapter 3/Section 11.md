
# Boundary-Fill, Flood-Fill & Scan-Line Fill

## 1️⃣ Boundary-Fill Algorithm

### What is it?

A **recursive region filling algorithm** that fills pixels **until it hits a boundary color**.

---

### How it Works (Idea)

* Start from a **seed pixel inside the region**
* If the pixel is:

  * ❌ boundary color → stop
  * ❌ already filled → stop
  * ✅ otherwise → fill it
* Then **recursively apply the same process to neighboring pixels**

---

### Steps (Simple)

1. Pick a **seed pixel** inside the region
2. Check:

   * Is it a boundary pixel?
   * Is it already filled?
3. If NO → fill it
4. Call boundary-fill on:

   * left
   * right
   * top
   * bottom
     (and diagonals if 8-connected)

---

### Why It Works Well

* Handles **any arbitrary shape**
* Fills all connected interior pixels
* Stops exactly at the boundary

---

### Problems ❌

* Too many **recursive calls**
* High **memory usage**
* Stack overflow for large regions

---

### Optimization Trick 💡

Instead of filling pixel-by-pixel:

* Fill **entire horizontal line** (left → right)
* Then look **above and below** that line for new seeds

✅ Fewer recursive calls
✅ Faster execution

---

### Best Use Case

✔ Region has a **clearly defined boundary color**
✔ Interior may have **multiple colors**

---

## 2️⃣ Flood-Fill Algorithm

### What is it?

Also a **recursive filling algorithm**, but it fills based on **interior color**, not boundary color.

---

### How it Works (Idea)

* Start from a **seed pixel**
* If the pixel has the **original region color**:

  * Fill it with a new color
  * Recursively apply to neighbors
* If not → stop

---

### Steps (Simple)

1. Choose seed pixel
2. Check:

   * Does pixel have original color?
3. If YES → fill it
4. Call flood-fill on neighboring pixels

---

### Key Difference from Boundary-Fill ⚠️

| Boundary-Fill                 | Flood-Fill                  |
| ----------------------------- | --------------------------- |
| Stops at boundary color       | Stops when color changes    |
| Needs boundary color          | No boundary needed          |
| Interior can be multi-colored | Interior must be same color |

---

### Best Use Case

✔ Region has **uniform interior color**
✔ Boundary is **not clearly defined**

---

### Efficiency

Same optimization as boundary-fill:

* Fill horizontal lines
* Reduce recursion

---

## 3️⃣ Scan-Line Fill Algorithm

### Big Picture 🧠

* **Non-recursive**
* Works on **polygonal regions**
* Uses **geometry**, not pixel chasing
* **Fastest and most efficient**

---

### Core Idea

Fill a polygon **one scan line at a time** (left → right).

---

### Step-by-Step Working

1. Find **first and last scan line** of the polygon
2. For each scan line:

   * Find all **intersection points** with polygon edges
   * Sort intersections by **x-coordinate**
   * Pair them: (x1,x2), (x3,x4), …
   * Fill pixels **between each pair**

---

### Important Rules ⚠️

#### Horizontal edges

* **Ignored**
* Automatically filled when scan line reaches them

---

#### Vertex Intersection Problem

If a scan line passes through a vertex:

* Local **max/min** → OK
* Two edges both increasing/decreasing → ❌ double counting

✅ **Fix:**
Subtract **1 from ymax of lower edge**, so only one edge is counted

---

## Edge List (Very Important for Exams ⭐)

To make scan-line filling efficient, we use an **Edge List**.

---

### What is Stored for Each Edge?

Each non-horizontal edge stores:

* `ymin` → smaller y of edge
* `ymax` → larger y (sometimes ymax − 1)
* `x at ymin`
* `1/m` → inverse slope

---
<img width="1154" height="387" alt="image" src="https://github.com/user-attachments/assets/e58d0a87-1517-403f-9f65-b7d47a336929" />


---

### Edge Activation

* Edge becomes **active** when scan line = ymin
* Edge becomes **inactive** when scan line > ymax

---

### Why Subtract 1 from ymax?

To avoid **double intersections** at shared vertices
(prevents wrong filling)

---

## One-Line Exam Answers ⭐

**Boundary-Fill Algorithm:**

> A recursive algorithm that fills a region starting from a seed pixel and stops when boundary pixels are encountered.

**Flood-Fill Algorithm:**

> A recursive algorithm that fills a region by replacing all connected pixels of the same interior color.

**Scan-Line Algorithm:**

> A polygon filling algorithm that fills regions by processing one scan line at a time using edge intersections.

---

## Quick Comparison Table ⭐

| Feature           | Boundary-Fill | Flood-Fill      | Scan-Line |
| ----------------- | ------------- | --------------- | --------- |
| Recursion         | Yes           | Yes             | No        |
| Boundary required | Yes           | No              | Geometric |
| Speed             | Medium        | Medium          | Fast      |
| Best for          | Pixel regions | Uniform regions | Polygons  |



# Scan-Line Algorithm (FULL EXPLANATION)

---

## 1️⃣ What problem does this algorithm solve?

Boundary-fill and flood-fill work at the **pixel level**, so they:

* Are recursive
* Can be slow
* Use a lot of memory

👉 **Scan-line algorithm is different**
It fills **polygonal regions defined geometrically** (by vertices and edges), not by pixels.

This makes it:

* Faster
* Non-recursive
* Ideal for **filled polygons**

---

## 2️⃣ Polygon Representation (Fig. 3-19)

The polygon is defined by:

* Vertices: ( V_1, V_2, V_3, \dots )
* Edges: ( E_1, E_2, E_3, \dots )

Each edge connects two vertices.

Before filling:

* All vertex coordinates are already **scan-converted to integers**

---

## 3️⃣ Main Idea of Scan-Line Filling

We fill the polygon **one horizontal scan line at a time**, from:

* **first scan line** (lowest y)
* to **last scan line** (highest y)

For **each scan line**:

1. Find where the scan line **intersects polygon edges**
2. Sort intersection points by **x**
3. Pair them:
   ((x_1, x_2), (x_3, x_4), \dots)
4. Draw horizontal lines between each pair

This fills the interior correctly.

---

## 4️⃣ Intersection Example (Fig. 3-19)

For scan line **j**:

* It intersects edges (E_1, E_7, E_6, E_4)
* Intersection points: **a, b, c, d**
* Sorted by x → paired as:

  * (a, b)
  * (c, d)

Pixels between **a–b** and **c–d** are filled.

---

## 5️⃣ Why Horizontal Edges Are Ignored

Horizontal edges (like (E_5)):

* Are automatically filled when scan lines pass through them
* Do NOT affect inside/outside decisions

So:
👉 **Horizontal edges are ignored in intersection calculations**

---

## 6️⃣ Vertex Intersection Problem (Very Important)

### Case 1: Local Minimum or Maximum (V₁, V₇)

* Two edges meet
* Both produce intersection points
* ✅ No problem

### Case 2: Two edges increasing or decreasing (V₄)

* Both edges produce intersection at same vertex
* ❌ Causes extra intersection
* ❌ Leads to incorrect fill

---

## 7️⃣ The Fix: Decrease ymax by 1 ⭐

To solve vertex ambiguity:

* For the **lower edge**, reduce `ymax` by **1**
* This deactivates it **one scan line early**

Result:

* Only **one edge** contributes an intersection at that vertex
* Correct pairing of intersections

This is why **ymax is sometimes stored as ymax − 1**

---

## 8️⃣ Edge List (Table 3-1)

To make the algorithm efficient, we use an **Edge List**.

Each **non-horizontal edge** gets one record.

---

### What is stored for each edge?

| Field       | Meaning                        |
| ----------- | ------------------------------ |
| `Edge`      | Edge name (E₁, E₂, …)          |
| `ymin`      | Smaller y of the edge          |
| `ymax`      | Larger y (sometimes −1)        |
| `x at ymin` | x-coordinate where edge starts |
| `1/m`       | Inverse slope of the edge      |

---

### Why inverse slope (1/m)?

Because:

* Scan lines move **up by 1** in y
* So x changes by:
  [
  x_{new} = x_{old} + \frac{1}{m}
  ]

This allows **incremental x calculation**, no division each time.

---

## 9️⃣ Sorting the Edge List

Edge list is **sorted by ymin**

Example:

* Edges starting at lowest vertex (V_1) appear first
* They become active first

---

## 🔟 Active Edge List (AEL)

An edge becomes **active** when:
[
\text{scan line y} = ymin
]

An edge becomes **inactive** when:
[
\text{scan line y} > ymax
]

Only **active edges** are used to find intersections.

---

## 1️⃣1️⃣ First Intersection Point

For an active edge:

* First intersection is always its **lower endpoint**
* That x value is already stored

---

## 1️⃣2️⃣ Incremental Intersection Calculation ⭐

If an edge intersects scan line y at:
[
(x, y)
]

Then at next scan line:
[
(x + 1/m, y + 1)
]

So:

* We just **add 1/m to x**
* Very fast and efficient

---

## 1️⃣3️⃣ Edge Deactivation

Once scan line reaches `ymax`:

* Edge is removed from active list
* It will never intersect again

---

## 1️⃣4️⃣ Why This Algorithm Is Efficient

✔ No recursion
✔ Uses geometry
✔ Incremental calculations
✔ Correct handling of vertices
✔ Works for complex polygons

---

## One-Paragraph Exam Answer ⭐

> The scan-line algorithm fills a polygon by processing one horizontal scan line at a time. For each scan line, intersection points with polygon edges are computed, sorted, and paired to fill interior pixels. An edge list stores edge information, and active edges are updated incrementally using inverse slopes. Special handling of vertices is done by adjusting ymax values to avoid duplicate intersections.

---


<img width="486" height="212" alt="image" src="https://github.com/user-attachments/assets/6aa9473a-86cc-47ee-9052-2b5696dc6b6a" />


# Table 3-1: Edge List — Explained from Zero

This table stores **all the information needed for each polygon edge** so the scan-line algorithm can fill the polygon efficiently.

👉 **Each row = one edge of the polygon**
👉 **Only non-horizontal edges appear in this table**

---

## The Table (What You’re Seeing)

| Edge | ymin | ymax   | x coordinate of vertex with y = ymin | 1/m  |
| ---- | ---- | ------ | ------------------------------------ | ---- |
| E1   | y1   | y2 − 1 | x1                                   | 1/m1 |
| E7   | y1   | y7     | x1                                   | 1/m7 |
| E4   | y5   | y4 − 1 | x5                                   | 1/m4 |
| E6   | y6   | y7     | x6                                   | 1/m6 |
| E2   | y2   | y3     | x2                                   | 1/m2 |
| E3   | y4   | y3     | x4                                   | 1/m3 |

Now let’s decode **every single column**.

---

## 1️⃣ Column: **Edge**

Example: `E1, E7, E4, …`

This is just the **name of the edge**.

Each edge:

* Connects two vertices
* Is part of the polygon boundary

Nothing mathematical here—just identification.

---

## 2️⃣ Column: **ymin**

This is the **smaller y-coordinate** of the two endpoints of the edge.

Why this matters:

* A scan line starts intersecting an edge **only when it reaches ymin**
* The edge becomes **active** at `y = ymin`

Example:

* Edge E1 starts at vertex `(x1, y1)`
* So `ymin = y1`

---

## 3️⃣ Column: **ymax**

This is the **larger y-coordinate** of the edge’s endpoints
⚠️ **Sometimes it is reduced by 1**

### Why `ymax − 1` appears

This fixes the **vertex intersection problem**.

If two edges meet at a vertex and both are increasing or decreasing:

* Counting both causes **duplicate intersections**
* Leads to wrong filling

✅ Solution:

* The **lower edge** is deactivated **one scan line early**
* So we store `ymax − 1`

### Example:

* For edge E1:

  * Original ymax = y2
  * Stored as `y2 − 1`

Meaning:

> Edge E1 stops contributing intersections **before** scan line y2

---

## 4️⃣ Column: **x coordinate of vertex with y = ymin**

This is **very important**.

It stores:

> The **x-coordinate where the edge first meets a scan line**

Because:

* The **first intersection point** of an edge is always its **lower endpoint**
* So we need the x-value at `ymin`

Example:

* Edge E1 starts at `(x1, y1)`
* Since `ymin = y1`, store `x1`

This x value will be **updated incrementally** as scan lines move upward.

---

## 5️⃣ Column: **1/m (Inverse Slope)**

Where:
[
m = \frac{\Delta y}{\Delta x}
\quad\Rightarrow\quad
\frac{1}{m} = \frac{\Delta x}{\Delta y}
]

Why store **1/m** instead of m?

Because scan lines move like this:

* `y` increases by **1**
* `x` changes by **1/m**

So:
[
x_{new} = x_{old} + \frac{1}{m}
]

This allows:

* Fast
* Incremental
* No division inside loops

Example:

* If edge E1 slope = m1
* Store `1/m1`
* Each scan line → `x = x + 1/m1`

---

## 6️⃣ Why the Table Is Sorted This Way

Notice the order:

* E1 and E7 both have `ymin = y1` → appear first
* Then edges with `ymin = y2`, then `y4`, etc.

👉 **The edge list is sorted by ymin**

Why?

* So edges become active **exactly when needed**
* Makes scan-line processing efficient

---

## 7️⃣ How This Table Is Used (Step-by-Step)

For each scan line `y`:

1. **Activate edges** whose `ymin == y`
2. **Remove edges** whose `ymax < y`
3. For all active edges:

   * Use stored `x`
4. Sort active x values
5. Fill pixels between pairs
6. Update x using:
   [
   x = x + \frac{1}{m}
   ]

---

## 8️⃣ One-Line Meaning of the Table ⭐

> **The edge list stores when an edge starts, when it stops, where it starts, and how its intersection point moves as scan lines go upward.**

---

## 9️⃣ Exam-Friendly Explanation ⭐

> Each row in the edge list represents a non-horizontal polygon edge. The list stores the minimum and maximum y-coordinates of the edge, the x-coordinate at ymin, and the inverse slope for incremental intersection calculation. The ymax value may be reduced by one to avoid duplicate vertex intersections. The list is sorted by ymin for efficient scan-line filling.

---

