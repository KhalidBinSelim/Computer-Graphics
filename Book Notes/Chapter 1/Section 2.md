<img width="596" height="373" alt="image" src="https://github.com/user-attachments/assets/ccdd8f7c-9faf-494d-af73-7790fa6295e3" />


First, think about **drawing a triangle**.

#### 1. How humans draw a triangle

In real life:

* First, we **imagine** the triangle in our mind
  (its **type, size, shape**)
* Then we **draw it** using a pen on paper

In computer graphics terms:

* This imagined triangle is called the **object definition**
* It exists in an imaginary, mathematical space called **object space**
* Object space is **continuous**, meaning it has no fixed pixels yet

---

#### 2. From imagination to paper (mapping)

When we draw the triangle on paper:

* We are **mapping** the triangle from **object space**
  → to **image space**

**Image space**:

* The surface where the image appears (paper or screen)
* It is also continuous

This mapping depends on choices like:

* **Where** the triangle is placed (center, corner, etc.)
* **Orientation** (pointing left, right, up, etc.)

---

#### 3. How computers do the same thing

A **computer follows the same idea**, but mathematically.

To represent a triangle:

* A **2D Cartesian coordinate system (x, y)** is used in object space
* The triangle is defined by **three vertices**
* Each vertex has **x and y coordinates**

Example idea:

* Vertex 1 → (x₁, y₁)
* Vertex 2 → (x₂, y₂)
* Vertex 3 → (x₃, y₃)

The computer:

* Connects vertex 1 to 2
* Connects 2 to 3
* Connects 3 to 1
  → This forms the triangle

---

#### 4. Important term for exam

The process of **defining objects efficiently using mathematical descriptions** is called:

> **Geometric Representation**

---

### Key Exam Points (Remember These)

* **Object Space** → imaginary, mathematical space where objects are defined
* **Image Space** → space where the image is displayed
* **Object Definition** → description of the object (shape, size, vertices)
* **Geometric Representation** → mathematical way to represent objects
* A triangle is represented by **three vertices (x, y coordinates)**

---

### One-Line Exam Answer

> In computer graphics, a triangle is defined in object space using the coordinates of its vertices and then mapped to image space to produce the final picture.
