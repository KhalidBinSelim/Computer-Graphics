### 1. Transformation (placing the triangle)

After defining a triangle, the next step is **where and how it appears on the screen**.

This part of computer graphics is called **Transformation**.

* **Matrices** are used to move the triangle from object space to image space
* Using a **transformation matrix**, we can:

  * Change **position** (move it left, right, up, down)
  * Change **orientation** (rotate it)
  * Change **size** (scale it bigger or smaller)

 Important idea:
From **one triangle model** in object space, we can draw:

* Many triangles
* At different locations
* With different sizes and rotations
  just by changing the transformation matrix

---

### 2. Why computer lines look different from paper lines

A triangle drawn on **paper**:

* Has **smooth, continuous edges**

A triangle on a **computer screen**:

* Looks slightly **jagged**, especially on slanted edges

Why?

Because:

* Paper is **continuous**
* Computer screens are **not continuous**

---

### 3. Pixels and discrete image space

Computer image space is made of **pixels**:

* Small square picture elements
* Arranged in **rows and columns**

So:

* Horizontal/vertical lines → rows or columns of pixels
* Slanted lines → look like **stairs**

---

### 4. Scan Conversion

The process of converting:

* **Continuous shapes** (lines, triangles)
* Into **discrete pixels**

is called:

> **Scan Conversion**

---

### 5. Aliasing

The **distortion or jagged appearance** caused by scan conversion is called:

> **Aliasing**

Example:

* Slanted lines look like stair steps

---

### 6. Why not just use smaller pixels?

Smaller pixels → smoother image
BUT:

* If pixel width and height are cut in half
  → total pixels become **4 times more**
* This means:

  * **4× memory**
  * **4× processing cost**

So it’s expensive.

---

### 7. Anti-Aliasing

Instead of only reducing pixel size, computer graphics uses other techniques to reduce jaggedness.

This area is called:

> **Anti-Aliasing**

Its goal:

* Reduce the visual effects of aliasing
* Without excessive cost

---

## Key Exam Terms (Very Important)

* **Transformation** → uses matrices to move, rotate, and scale objects
* **Scan Conversion** → converts continuous shapes into pixels
* **Aliasing** → distortion due to pixel-based display
* **Anti-Aliasing** → techniques to reduce aliasing effects
* **Pixel** → smallest picture element on the screen

---

## One-Line Exam Answers

* **Transformation** uses matrices to control position, size, and orientation of objects.
* **Scan conversion** converts continuous graphics into discrete pixels.
* **Aliasing** is the distortion caused by representing continuous shapes with pixels.
* **Anti-aliasing** reduces the jagged appearance of images.
