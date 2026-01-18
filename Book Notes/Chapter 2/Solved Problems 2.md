## Solved Problems 2 — Chapter 2 (Continued)

### **2.20 What do you call the path the electron beam takes when returning to the left side of the CRT screen?**

**Solution:**
This path is called **horizontal retrace**.

✔ It happens at the end of each scan line.

---

### **2.21 What do you call the path the electron beam takes at the end of each refresh cycle?**

**Solution:**
This path is called **vertical retrace**.

✔ It occurs when the beam moves from the bottom back to the top of the screen.

---

### **2.22 What is the pitch of a color CRT?**

**Solution:**
Pitch is the **distance between the centers of adjacent phosphor dot patterns** on the screen.

✔ Smaller pitch → sharper image.

---

### **2.23 Why do many color printers use black pigment?**

**Solution:**
Because:

* Cyan, magenta, and yellow pigments are **expensive**
* Producing pure black by mixing colors is **technically difficult**
* Black pigment gives **better contrast and lower cost**

---

### **2.24 Show that an n × n pixel grid with m intensity levels gives approximately n²(m−1)+1 intensity levels.**

**Solution:**

* Each pixel has **m − 1 nonzero intensity levels**
* Pixels can be turned on one by one → **n² combinations**
* This gives **n²(m − 1)** nonzero intensity levels
* Add **1** for the zero-intensity case (all pixels off)

✔ Total ≈ **n²(m − 1) + 1**

---

### **2.25 Represent the grid patterns in Fig. 2-8 with a dither matrix.**

**Solution:**
A valid dither matrix is:

[
\begin{bmatrix}
0 & 2 \
3 & 1
\end{bmatrix}
]

✔ Used for ordered dithering.

---

### **2.26 Error propagation formulas for Floyd–Steinberg (top-to-bottom, right-to-left)?**

**Solution:**
If error = **e**, then:

* ( S(x-1, y) += a e )
* ( S(x+1, y-1) += b e )
* ( S(x, y-1) += c e )
* ( S(x-1, y-1) += d e )

✔ Error is distributed to neighboring pixels.

---

### **2.27 What is RLE?**

**Solution:**
**RLE (Run-Length Encoding)** is a **lossless image compression technique** that stores consecutive repeated values as a single value and count.

---

### **2.28 Reconstruct the string compressed as "981435" using RLE.**

**Solution:**

* 9 of ‘8’ → `888888888`
* 4 of ‘5’ → `555`

✔ Result: **"8888888884555"**

---

### **2.29 Offset of pixel (x, y) stored left-to-right and bottom-to-top?**

**Solution:**
[
\text{offset} = y \times n + x
]

✔ (n) = number of pixels per row.

---

### **2.30 Offset if stored left-to-right and top-to-bottom?**

**Solution:**
[
\text{offset} = (m - y - 1) \times n + x
]

✔ (m) = number of rows.

---

### **2.31 Pseudo-code to initialize a 256-entry grayscale lookup table**

**Solution:**

```
int i, rgb[3];
for (i = 0; i < 256; i++) {
    rgb[0] = rgb[1] = rgb[2] = i;
    setEntry(i, rgb);
}
```

✔ All entries become grayscale.

---

### **2.32 Pseudo-code to swap red and green in a lookup table**

**Solution:**

```
int i, temp, rgb[3];
for (i = 0; i < 256; i++) {
    getEntry(i, rgb);
    temp = rgb[0];
    rgb[0] = rgb[1];
    rgb[1] = temp;
    setEntry(i, rgb);
}
```

---

### **2.33 Pseudo-code to draw a rectangle of width w and height h**

**Solution:**

```
int i, j;
setColor(rgb);
for (j = y; j < y + h; j++)
    for (i = x; i < x + w; i++)
        setPixel(i, j);
```

---

### **2.34 Pseudo-code to draw a right-angled triangle**

**Solution:**

```
int i, j;
setColor(rgb);
for (j = y; j <= y + t; j++)
    for (i = x; i <= x + y + t - j; i++)
        setPixel(i, j);
```

---

### **2.35 Reset pixels to complementary colors (lookup table)**

**Solution:**

```
int i, rgb[3];
for (i = 0; i < 256; i++) {
    getEntry(i, rgb);
    rgb[0] = 255 - rgb[0];
    rgb[1] = 255 - rgb[1];
    rgb[2] = 255 - rgb[2];
    setEntry(i, rgb);
}
```

---

### **2.36 Same task for 24-bit true color image**

**Solution:**

```
int i, j, rgb[3];
for (j = 0; j < height; j++)
    for (i = 0; i < width; i++) {
        getPixel(i, j, rgb);
        rgb[0] = 255 - rgb[0];
        rgb[1] = 255 - rgb[1];
        rgb[2] = 255 - rgb[2];
        setPixel(i, j, rgb);
    }
```

---

### **2.37 Sum and product of (0.5 + 2.0i) and (1.0 − 1.0i)**

**Solution:**
**Sum:**
[
(0.5 + 1.0) + (2.0 - 1.0)i = 1.5 + 1.0i
]

**Product:**
[
(0.5×1.0 - 2.0×(-1.0)) + (0.5×(-1.0) + 2.0×1.0)i = 2.5 + 1.5i
]

---

### **2.38 Square of the two complex numbers in Prob. 2.37**

**Solution:**
[
(0.5 + 2.0i)^2 = -3.75 + 2.0i
]
[
(1.0 - 1.0i)^2 = 0 - 2.0i
]

---

### **2.39 Show that ( c = 1 + 254 \times \frac{count}{N} ) is proportional mapping**

**Solution:**
Proportional mapping requires:
[
\frac{c - 1}{255 - 1} = \frac{count}{N}
]
Solving gives:
[
c = 1 + 254 \times \frac{count}{N}
]

---

### **2.40 Modify Mandelbrot code to visualize Julia sets**

**Solution:**
In Julia sets:

* **z is fixed**
* **x varies**

✔ Replace `x = x + z` with a fixed complex constant **z** in iteration.

---

### **2.41 How to avoid square-root calculation in Mandelbrot/Julia algorithms?**

**Solution:**
Instead of testing:
[
|x| < 2
]
Test:
[
|x|^2 < 4
]

✔ Faster and computationally efficient.

---
