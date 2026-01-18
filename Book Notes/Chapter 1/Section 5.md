<img width="566" height="272" alt="image" src="https://github.com/user-attachments/assets/99614035-b753-4f4c-85bc-66a4bb85c9d0" />


1. Hidden Surface Removal

A **cube has 6 faces**, but in drawings we usually see **only 3 faces**.

Why?

* Because we draw objects **as we see them in real life**
* Surfaces that face away or are blocked are **not visible**

In computer graphics:

* The process of **removing invisible surfaces** is called:

> **Hidden Surface Removal**

---

### 2. 3D Graphics Pipeline

To support **three-dimensional graphics**, we add two steps to the pipeline:

After **Transformation**, but before **Scan Conversion**, we include:

1. **Projection** – converts 3D objects to 2D views
2. **Hidden Surface Removal** – removes invisible surfaces

This forms a **basic 3D graphics pipeline**.

---

### 3. Making images look real (Photo-realism)

Creating images that look **real like photographs** is a major goal of computer graphics.

Photography works because:

* Light comes from a **light source**
* It reflects off object surfaces
* The camera captures this reflected light

To make computer images realistic, graphics must simulate:

* Light
* Reflection
* Brightness
* Darkness

---

### 4. Illumination and shading

Important observations:

* Surfaces **closer to light** look brighter
* Surfaces **facing away** from light look darker

In computer graphics:

* Mathematical formulas that simulate **direct light reflection** are called:

> **Local Illumination Models**

These consider:

* Light directly from the source to the surface

---

### 5. Global Illumination

In reality, light:

* Reflects from one surface to another
* Passes through transparent objects

To model this more accurately, graphics uses:

> **Global Illumination Models**

These consider:

* All possible light interactions in a scene

(Global illumination is **more realistic but computationally expensive**)

---

### 6. Surface smoothness and textures

Computer-generated objects often look **too smooth and perfect**.

In real life:

* Objects have **roughness and patterns**

In computer graphics:

* These surface details are called:

> **Surface Textures**

Texture techniques:

* Make objects look like wood, marble, metal, etc.
* Increase realism

---

### 7. Shadows

If one object blocks light:

* It should create a **shadow** on another object

The process of computing shadows is called:

> **Shadow Generation**

Shadows are essential for realism.

---

## Key Exam Terms (Very Important)

* **Hidden Surface Removal** → removes invisible surfaces
* **Projection** → converts 3D objects to 2D images
* **Local Illumination Model** → direct light from source
* **Global Illumination Model** → full light interaction
* **Surface Texture** → surface detail and material look
* **Shadow Generation** → computation of shadows

---

## One-Line Exam Answers

* **Hidden surface removal** eliminates surfaces not visible to the viewer.
* **Local illumination models** simulate direct lighting effects.
* **Global illumination models** account for light reflection between surfaces.
* **Surface textures** add realism by modeling surface details.
* **Shadow generation** computes shadows cast by objects.

---
