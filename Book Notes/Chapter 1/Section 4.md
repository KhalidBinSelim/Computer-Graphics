<img width="637" height="196" alt="image" src="https://github.com/user-attachments/assets/098e36a8-ed2c-4958-bcab-4eb700a833ca" />


### 1. Simplified Graphics Pipeline

All the steps we discussed together form a **graphics pipeline**.

A **graphics pipeline** is the **step-by-step process** a computer follows to turn data into a picture on the screen.

---

### 2. Start of the pipeline: Primitive objects

At the beginning:

* We have **primitive objects** (simple shapes like points, lines, triangles)
* They are stored as **data**, not pictures

Example:

* A triangle is stored using the coordinates of its **three vertices**
* These coordinates can be stored in a **3 × 2 array**:

  * 3 rows → 3 vertices
  * 2 columns → x and y values

---

### 3. Transformation stage

Next:

* The graphics system applies **transformations**
* These are based on **user-defined parameters**

Transformations include:

* Translation (move)
* Rotation
* Scaling (resize)

---

### 4. Scan conversion stage

After transformation:

* The system performs **scan conversion**
* **Anti-aliasing** may or may not be used
* This converts the transformed shapes into **pixels** on the screen

---

### 5. World Coordinate System (very important)

Between object space and screen space, there is an **intermediate coordinate system** called:

> **World Coordinate System**

Purpose:

* It decides **where transformed objects are placed**
* Helps combine multiple objects into one picture

Example:

* One triangle is:

  * Scaled and moved
* Another triangle is:

  * Scaled
  * Rotated 90° counterclockwise
  * Then moved

Both come from the **same original object**

---

### 6. How programs use the pipeline

In practice:

* We write a program in a **host language** (like C, C++, Java)
* We call **graphics library functions**

These functions:

* Set transformation parameters
* Send object data into the pipeline

The pipeline automatically applies:

* Transformations
* Scan conversion
  → Final output is the **picture on the screen**

---

<img width="536" height="137" alt="image" src="https://github.com/user-attachments/assets/2b332075-960e-48c0-b8e1-d79fd321267b" />


### 7. From 2D to 3D graphics

So far, everything discussed is **two-dimensional graphics**.

In **three-dimensional graphics**:

* Objects have **depth (x, y, z)**
* There is a **big difference** between:

  * The actual 3D object
  * Its 2D picture on the screen

---

### 8. Projection (new important concept)

A 3D object **cannot be shown directly** on a 2D screen.

So:

* The object is **projected** onto a 2D surface

This process is handled by another area of computer graphics called:

> **Projection**

Different projections can create different drawings of the **same 3D object**.

---

## Key Exam Terms (Must Remember)

* **Graphics Pipeline** → sequence of steps to produce an image
* **Primitive Objects** → basic shapes (points, lines, triangles)
* **World Coordinate System** → intermediate space for placing objects
* **Scan Conversion** → converts shapes to pixels
* **Projection** → maps 3D objects onto 2D screen

---

## One-Line Exam Answers

* A **graphics pipeline** converts object data into a screen image through transformation and scan conversion.
* The **world coordinate system** is an intermediate system used to place transformed objects in a scene.
* **Projection** maps a 3D object onto a 2D display surface.
