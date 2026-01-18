## Solved Problems 1 — Chapter 2


### **2.1 What is the resolution of an image?**

**Solution:**
Resolution is the **number of pixels per unit length** (e.g., pixels per inch) in both horizontal and vertical directions.

---

### **2.2 Compute the size of a 640 × 480 image at 240 pixels per inch.**

**Solution:**

* Width = 640 ÷ 240 = **2⅔ inches**
* Height = 480 ÷ 240 = **2 inches**

✔ Image size = **2⅔ × 2 inches**

---

### **2.3 Compute the resolution of a 2 × 2 inch image that has 512 × 512 pixels.**

**Solution:**

* Resolution = 512 ÷ 2 = **256 pixels per inch**

---

### **2.4 What is an image’s aspect ratio?**

**Solution:**
Aspect ratio is the **ratio of image width to height**, measured either in pixels or physical units.

---

### **2.5 If an image has a height of 2 inches and an aspect ratio of 1.5, what is its width?**

**Solution:**

* Width = Aspect ratio × Height
* Width = 1.5 × 2 = **3 inches**

---

### **2.6 Resize a 1024 × 768 image to 640 pixels wide (same aspect ratio). Find height.**

**Solution:**

* Height = 640 × (768 ÷ 1024)
* Height = **480 pixels**

---

### **2.7 Coordinates of the lower-left corner of a 512 × 512 sub-image cut from the center of an 800 × 600 image?**

**Solution:**

* x = (800 − 512) ÷ 2 = **144**
* y = (600 − 512) ÷ 2 = **44**

✔ Coordinates = **(144, 44)**

---

### **2.8 Convert coordinates from upper-left origin to lower-left origin.**

**Solution:**
If original coordinates are (x, y), then:
[
(x', y') = (x, m - y - 1)
]
where **m** is the image height in pixels.

✔ This flips the vertical axis.

---

### **2.9 Find CMY coordinates of RGB (0.2, 1, 0.5).**

**Solution:**
[
(C, M, Y) = (1 - R, 1 - G, 1 - B)
]
[
= (0.8, 0, 0.5)
]

---

### **2.10 Find RGB coordinates of CMY (0.15, 0.75, 0).**

**Solution:**
[
(R, G, B) = (1 - C, 1 - M, 1 - Y)
]
[
= (0.85, 0.25, 1)
]

---

### **2.11 With 2 bits per RGB primary, how many colors per pixel?**

**Solution:**

* Each primary: (2^2 = 4) levels
* Total colors = (4 × 4 × 4 = 64)

---

### **2.12 With 10 bits per RGB primary, how many colors per pixel?**

**Solution:**
[
2^{10} × 2^{10} × 2^{10} = 1024^3 = 1,073,741,824
]

✔ Over **1 billion colors**

---

### **2.13 5 bits for Red & Blue, 6 bits for Green. Total colors?**

**Solution:**
[
2^5 × 2^6 × 2^5 = 2^{16} = 65,536
]

---

### **2.14 12-bit pixel values in lookup table representation. Entries?**

**Solution:**
[
2^{12} = 4096 \text{ entries}
]

---

### **2.15 2-byte pixel values in a 24-bit lookup table. Table size?**

**Solution:**

* Entries = (2^{16} = 65,536)
* Each entry = 24 bits = 3 bytes

[
65,536 × 3 = 196,608 \text{ bytes}
]

---

### **2.16 Fluorescence refers to light after electron beam exposure. True or False?**

**Solution:**
❌ **False**

* **Fluorescence** → light during exposure
* **Phosphorescence** → light after exposure

---

### **2.17 What is persistence?**

**Solution:**
Persistence is the **duration of phosphorescence** of a phosphor.

---

### **2.18 Function of the control electrode in a CRT?**

**Solution:**
It **regulates the intensity of the electron beam**.

---

### **2.19 Two methods of bending an electron beam?**

**Solution:**

1. **Electrostatic deflection**
2. **Magnetic deflection**

---
