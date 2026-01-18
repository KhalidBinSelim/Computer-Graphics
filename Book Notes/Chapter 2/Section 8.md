## 2.6 IMAGE FILES

A **digital image file** is how an image is stored or sent in a computer.
It is saved as a **binary file** (0s and 1s).

<img width="635" height="375" alt="image" src="https://github.com/user-attachments/assets/f338c2d2-600f-4438-80b7-e044f9f03d2f" />


### Common image file formats

Some popular image formats are:

* **BMP** – Windows Bitmap (simple, usually large size)
* **JPEG (JPG)** – Uses compression, good for photographs
* **TIFF** – High quality, often used in printing and scanning

Even though these formats differ, their **basic structure is similar**.

---

## Basic Structure of an Image File

An image file mainly has **two parts**:

### 1. Header

### 2. Image Data

```
| Header | Image Data |
```

---

## 1. Header (Image Information)

The **header** stores information *about* the image, not the image itself.

### Header contains:

* **Format identification**
  (tells whether the file is BMP, JPEG, TIFF, etc.)
* **Version number** (optional)
* **Image width and height** (in pixels)
* **Image type**, such as:

  * Black & white (1 bit per pixel)
  * 8-bit grayscale (256 gray levels)
  * 8-bit color (uses lookup table)
  * 24-bit true color
* **Image data format**

  * Pixel storage order
* **Compression type** (if any)
* **Color map (lookup table)** – only if needed

✔ The header size is often **fixed**, so the system knows where the image data begins.

---

## 2. Image Data (Actual Picture)

This part stores the **actual pixel values**.

### Pixel storage order

Common orders are:

* **Left to right, top to bottom**
* **Left to right, bottom to top**

---

## Interlaced vs Non-Interlaced Color Storage

### Interlaced format

* RGB values for each pixel are stored **together**
* Order looks like:

```
R G B | R G B | R G B | ...
```

✔ Easier to process pixel-by-pixel

---

### Non-Interlaced format

* All values of one color are stored first
* Order looks like:

```
R R R ... | G G G ... | B B B ...
```

✔ Easier for color-based processing

---

## Compression in Image Files

Image data may be **compressed** to save space.

### Run-Length Encoding (RLE)

**Idea:**
Replace repeating values with:

```
(count, value)
```

### Example:

Original string:

```
xxxxxxyyzzzz   (12 bytes)
```

Compressed:

```
6x2y4z   (6 bytes)
```

✔ During decompression, each character is repeated according to its count.

---

## Key Points to Remember (Exam Focus)

* Image files consist of **Header + Image Data**
* Header describes **how to read the image**
* Image data contains **pixel values**
* **Interlaced** → RGB stored together
* **Non-interlaced** → all R, then G, then B
* **RLE** is a simple lossless compression method
* Header length is often **fixed**

---

## One-Line Exam Answers

* An image file stores a digital image in **binary form**.
* The header contains **format, size, type, and compression information**.
* Image data stores **actual pixel values**.
* **RLE** compresses data by replacing repeated values with a count.
