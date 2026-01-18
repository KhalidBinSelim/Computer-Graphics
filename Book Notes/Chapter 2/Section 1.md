1. What is a digital image?

A **digital image** is made up of many tiny dots called:

> **Pixels (picture elements)**

* Pixels are arranged in **rows and columns**
* This rectangular arrangement is called a **raster**

---

### 2. Number of pixels in an image

The **total number of pixels** depends on:

1. **Physical size of the image** (inches)
2. **Resolution** (pixels per inch, PPI)

> **Resolution** = number of pixels per unit length (inch)

#### Example:

* Image size = **3 × 2 inches**
* Resolution = **300 pixels per inch**

Total pixels:

* Width = 3 × 300 = 900 pixels
* Height = 2 × 300 = 600 pixels
* Total = 900 × 600 = **540,000 pixels**

---

### 3. Image size written as pixel dimensions

Often, image size is written as:

* **Width × Height (in pixels)**
  Examples:
* 512 × 512
* 640 × 480
* 1024 × 768

⚠️ Important:

* This format **does NOT tell**:

  * Physical size (inches)
  * Resolution (PPI)

---

### 4. Same pixels, different physical sizes

A **640 × 480 image**:

* At **96 PPI** → 6⅔ × 5 inches
* At **400 PPI** → 1.6 × 1.2 inches

👉 Same pixel count, **different printed/displayed size**

---

### 5. Aspect Ratio

The **aspect ratio** is:

> Width ÷ Height

Examples:

* 2 × 2 inch image → **1 : 1**
* 512 × 512 image → **1 : 1**
* 6 × 4½ inch image → **4 : 3**
* 1024 × 768 image → **4 : 3**

---

### 6. Pixel coordinates

Each pixel has a **coordinate**.

Convention:

* **Lower-left pixel** = (0, 0)

For a **640 × 480 image**:

* Lower-right pixel → (639, 0)
* Upper-right pixel → (639, 479)

(Counting starts from **0**, not 1)

---

### 7. How images are created on a computer

Creating an image means:

* **Setting color values for pixels**

Different pixel colors together form:

* The final **picture we see**

---

### 8. What this chapter covers

This chapter will discuss:

1. **Color models** (how colors are specified)
2. **Direct pixel color coding**
3. **Lookup-table color representation**
4. **Display devices** (monitor)
5. **Printing devices** (printer)
6. **Image files** (storage & transmission)
7. **Basic graphics operations** (setting pixel colors)
8. **Mandelbrot set** (creating images directly in pixel space)

---

## Key Exam Definitions (Very Important)

* **Pixel** → smallest element of a digital image
* **Raster** → rectangular grid of pixels
* **Resolution** → pixels per inch (PPI)
* **Aspect Ratio** → width-to-height ratio
* **Image size (pixels)** → width × height
* **Pixel coordinate system** → system to locate pixels

---

## One-Line Exam Answers

* A **digital image** is composed of discrete pixels arranged in rows and columns.
* **Resolution** refers to the number of pixels per unit length.
* **Aspect ratio** is the ratio of image width to image height.
* Image creation involves **setting pixel color values**.

---
