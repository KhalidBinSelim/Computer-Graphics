## 1. CMY Color Space

* CMY = **Cyan, Magenta, Yellow**
* It’s the **subtractive color model** used for printers
* Colors are represented as **(C, M, Y)** with values 0 or 1

Example:

* (0,0,0) → White
* (1,1,1) → Black
* (0,0,1) → Green
* (1,0,1) → Magenta
* (1,1,0) → Yellow

💡 **Tip:** CMY is just **opposite of RGB**

* C = 1 − R
* M = 1 − G
* Y = 1 − B

---

## 2. Direct Coding of Pixel Colors

* **Direct coding** means: each **pixel stores its color** in memory
* **Simple example:** 3 bits per pixel

  * Bit 1 → R
  * Bit 2 → G
  * Bit 3 → B

This gives **8 colors** (corners of the RGB cube):

* Black, Blue, Green, Cyan, Red, Magenta, Yellow, White

---

<img width="695" height="279" alt="image" src="https://github.com/user-attachments/assets/9399b9be-ae58-42d6-a142-467c53dc0187" />


### 3. True Color Representation (24-bit)

* **Industry standard:** 24 bits per pixel

  * 1 byte (8 bits) per primary color
* Each primary can have **256 intensity levels** (0–255)
* Total colors possible: 256 × 256 × 256 = **16.7 million**

**Why 24-bit is enough:**

* Difference between colors differing by 1 level is **hard to notice**
* More bits → not useful for normal viewing

---

### 4. Special Cases: Bilevel & Gray-Scale

* **Black-and-white images:** 1 bit per pixel

  * 0 → Black
  * 1 → White
* **Gray-scale images:** 8 bits per pixel

  * 256 gray levels
  * All RGB values are the same (r = g = b)

---

### 5. Storage Considerations

* 24-bit images require **lots of memory**

  * Example: 1000 × 1000 image → 3 million bytes
* Most images **don’t use all 16.7 million colors**
* So sometimes 24-bit storage is **more than needed**

---

## Key Exam Points (Must Memorize)

* **Direct coding** = pixel stores color directly
* **3-bit coding** → 8 colors
* **24-bit true color** → 16.7 million colors
* **Bilevel images** → 1 bit/pixel
* **Gray-scale images** → 8 bits/pixel
* True color often **more than needed** for single images

---

## One-Line Exam Answers

* **Direct coding** stores each pixel’s color in memory.
* **24-bit true color** allows 16.7 million colors.
* **Bilevel** uses 1 bit, **gray-scale** uses 8 bits per pixel.
* **3-bit RGB coding** can represent 8 colors.

---
