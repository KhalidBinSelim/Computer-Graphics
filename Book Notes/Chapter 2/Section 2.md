<img width="621" height="360" alt="image" src="https://github.com/user-attachments/assets/7870f403-1ac6-482f-93b4-91be5b46ea19" />


### 1. What is the RGB color model?

Color is a big topic, but in computer graphics the **most commonly used color model** is:

> **RGB (Red, Green, Blue)**

It uses **three primary colors**:

* **R** → Red
* **G** → Green
* **B** → Blue

---

### 2. Intensity values

Each color component has an **intensity value** between:

* **0** → off (no light)
* **1** → fully on (maximum light)

So any color is written as:

> **(r, g, b)**

Example:

* Black → (0, 0, 0)
* White → (1, 1, 1)
* Red → (1, 0, 0)
* Yellow → (1, 1, 0)

---

### 3. RGB color space (color cube)

* All RGB colors form a **cube-shaped color space**
* Each axis represents one primary color (R, G, B)

Important points:

* **Origin (0,0,0)** → Black
* **Opposite corner (1,1,1)** → White
* Line from black to white → **Gray axis**

Any point on the gray axis has:

> r = g = b

Example:

* (0.7, 0.7, 0.7) → medium gray
* Higher value → brighter gray
* Lower value → darker gray

---

### 4. Additive color model (very important)

RGB is an **additive** color model.

This means:

* We **start with black**
* Add red, green, and blue light
* More light → brighter color

This matches how:

> **Display monitors work**

---

<img width="632" height="103" alt="image" src="https://github.com/user-attachments/assets/60e9baac-60ee-4b40-8b57-0488136d4f07" />


### 5. CMY color model (for printers)

There is another color model called:

> **CMY (Cyan, Magenta, Yellow)**

* It is a **subtractive** color model
* Used mainly in **printers**

How it works:

* Start with **white**
* Subtract colors to get the desired color

Example:

* White − Red = Cyan
* Cyan is the **complement of Red**

---

### 6. Relationship between RGB and CMY

Each CMY component is the **complement** of an RGB component:

* C = 1 − R
* M = 1 − G
* Y = 1 − B

In CMY color space:

* (0,0,0) → White
* (1,1,1) → Black

<img width="720" height="358" alt="image" src="https://github.com/user-attachments/assets/3fd1c46b-23d3-44be-ba4e-1d6b3c4fe3e0" />

---

## Key Exam Points (Must Memorize)

* **RGB model** uses Red, Green, Blue
* Color is represented as **(r, g, b)**
* RGB is an **additive** model (used in monitors)
* **Gray axis** → r = g = b
* **CMY model** is **subtractive** (used in printers)
* CMY values are complements of RGB

---

## One-Line Exam Answers

* The **RGB color model** represents colors using red, green, and blue intensity values.
* RGB is an **additive color model** starting from black.
* The **gray axis** represents equal RGB values.
* The **CMY model** is a subtractive color model used in printing.

---
