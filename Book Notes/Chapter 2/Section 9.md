## 2.7 Setting the Color Attributes of Pixels

Setting the color of a pixel is the **most basic operation in computer graphics**.
It is done by **writing color values into the frame buffer** using graphics system or library functions.

Each pixel’s color is usually represented by **three values**:

* **R** (Red)
* **G** (Green)
* **B** (Blue)

These are often stored in a **3-element array**.

---

## Two Protocols for Setting Pixel Color

There are **two main ways** to specify pixel coordinates and color values.

---

### **Protocol 1: Specify Pixel and Color Together**

In this method, the application provides:

* Pixel coordinates `(x, y)`
* Color information at the same time

#### (a) Direct Coding (24-bit image)

```c
setPixel(x, y, rgb)
```

* `rgb[0] = r`
* `rgb[1] = g`
* `rgb[2] = b`

✔ Used when each pixel directly stores its RGB color.

---

#### (b) Lookup Table Representation

```c
setPixel(x, y, i)
```

* `i` is the **index** of the color in the lookup table
* The actual `(r, g, b)` value is stored in table entry `i`

✔ Used when pixels store **indices**, not colors.

---

### **Protocol 2: Use a Current Color**

In this method, the system keeps a **current color**.

#### Step 1: Set the current color

* **Direct coding**

```c
setColor(rgb)
```

* **Lookup table**

```c
setColor(i)
```

#### Step 2: Set pixels using only coordinates

```c
setPixel(x, y)
```

✔ The pixel is automatically colored using the **current color**.

---

## Setting and Reading Lookup Table Entries

### Set a lookup table entry

```c
setEntry(i, rgb)
```

* Stores color `(r, g, b)` at table index `i`

---

### Read a lookup table entry

```c
getEntry(i, rgb)
```

* Retrieves the color from entry `i` into array `rgb`

---

## RGB Value Formats

There are usually **two ways** to specify RGB values:

### 1. Floating-point format

* Range: **[0.0 , 1.0]**
* Example: `(0.5, 0.2, 1.0)`

### 2. Integer format

* Range: **[0 , 255]**
* Example: `(128, 51, 255)`

✔ Internally, **floating-point values are converted to integers** before storing in the frame buffer.

---

## Reading Pixel Values (Image Processing Support)

To read pixel data back from the frame buffer:

### Direct coding

```c
getPixel(x, y, rgb)
```

### Lookup table

```c
getPixel(x, y, i)
```

✔ Used in **image processing operations**.

---

## Setting Multiple Pixels at Once

Graphics systems often provide functions to:

* Read or write **rectangular blocks of pixels**
* Clear the screen efficiently

### Example: Clearing the screen

1. Set the background color:

```c
setColor(rgb)
```

2. Clear all pixels:

```c
clear()
```

✔ This sets **every pixel** to the current color.

---

## Key Exam Points (Very Important)

* Setting pixel color is the **most primitive graphics operation**
* Pixel colors are written to the **frame buffer**
* Two protocols:

  1. **Pixel + color together**
  2. **Current color + pixel**
* Lookup table pixels store **indices**, not RGB values
* RGB values may be **float [0–1] or integer [0–255]**
* `clear()` fills the image with the **current color**

---

## One-Line Exam Answers

* Pixel color attributes are set by writing values into the **frame buffer**.
* The **current color** simplifies repeated pixel drawing.
* Lookup table images separate **pixel indices** from **color values**.
* `getPixel()` supports pixel-based image processing.
