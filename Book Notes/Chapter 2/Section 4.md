<img width="726" height="353" alt="image" src="https://github.com/user-attachments/assets/405f7e03-a955-41bf-b0b9-9480c9de1906" />


## 1. What is a Lookup Table (LUT)?

* A **lookup table (LUT)** is a way to **reduce storage** while still showing many colors
* **Idea:** Pixel values **don’t store color directly**
* Instead, each pixel is an **index** into a **table of color values**

---

### 2. How it works

* Imagine a **table with 256 entries**
* Each entry contains a **24-bit RGB color**
* Each pixel is **1 byte (8 bits)** → can have a value 0–255
* The pixel value tells the computer **which table entry to use** for the color

Example:

* Pixel value = 5 → use **table entry 5**
* That entry contains the **24-bit RGB color**
* That’s the color displayed for the pixel

---

### 3. Advantages

* Reduces **storage requirements**
* Still allows **many colors simultaneously**

Example:

* 1000 × 1000 image

  * **Direct 24-bit color:** 3,000,000 bytes
  * **8-bit LUT:** 1,000,000 bytes + 768 bytes (color table)

* 8-bit LUT allows **256 colors** at the same time

* These colors can be **chosen from 16.7 million possible colors**

---

### 4. Color map

* **Important:** With LUTs, an image is defined by:

  1. **Pixel values**
  2. **Color table (lookup table) entries**

* The table entries together are called the **color map**

---

## Key Exam Points (Must Memorize)

* **Lookup Table (LUT)** = pixel stores **index, not color**
* 8-bit pixel → index into **256-entry table**
* Each table entry → **24-bit RGB color**
* Reduces memory while supporting **256 simultaneous colors**
* **Color map** = LUT entries that define the image colors

---

## One-Line Exam Answers

* **Lookup table** uses pixel values as indices into a color table.
* 8-bit LUT allows **256 simultaneous colors** from 16.7 million.
* **Color map** = all color values in the LUT that define the image.

---
