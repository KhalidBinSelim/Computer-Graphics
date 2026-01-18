
## 2.8 Example: Visualizing the Mandelbrot Set

This section shows how **beautiful images can be created by directly setting pixel colors**, using a famous mathematical object called the **Mandelbrot set**.

---

<img width="656" height="326" alt="image" src="https://github.com/user-attachments/assets/3e181600-51c8-46d7-a350-bf2491e78d37" />


<img width="732" height="735" alt="image" src="https://github.com/user-attachments/assets/93758bcd-fc75-4f88-ae2d-737030656176" />


---

## 3. Membership Rule (Very Important)

For a given complex number **z**:

1. Start with **x = 0**
2. Repeatedly compute:
   [
   x = x^2 + z
   ]
3. Check what happens:

* If **|x| becomes greater than 2**,
  👉 **z is NOT in the Mandelbrot set**
* If **|x| never exceeds 2** (within a fixed number of steps),
  👉 **z IS in the Mandelbrot set**

---

## 4. How This Becomes an Image

### Step 1: Map Image Pixels to the Complex Plane

* Each **pixel** represents a **complex number z**
* Horizontal axis → real part
* Vertical axis → imaginary part
* The chosen rectangle has the **same aspect ratio as the image** (to avoid distortion)

---

### Step 2: One Pixel = One z Value

For each pixel:

* Take its corresponding **z**
* Run the iteration test
* Count how many steps it takes for **|x| > 2**

---

## 5. Coloring Strategy (Grayscale Image)

* If **|x| never exceeds 2** after **N iterations**:

  * Color pixel **black**
* If **|x| exceeds 2**:

  * Pixel brightness depends on **how fast divergence happens**
  * **More iterations → brighter pixel**

✔ This makes the boundary region visually rich and detailed.

---

## 6. Why Use Threshold = 2?

Because:

* Once **|x| > 2**, the sequence **diverges very fast**
* This makes **2 a safe and efficient cutoff**

---

## 7. Understanding the Pseudo-Code (Plain English)

### What the code does:

1. Loop over every pixel `(i, j)`
2. Convert `(i, j)` into a complex number `z`
3. Set `x = 0`
4. Repeat:

   * Compute `x = x² + z`
   * Count iterations
5. Decide color:

   * **Black** → if no divergence
   * **Gray** → based on iteration count
6. Draw the pixel

---

### Key Lines Explained

```c
while (|x| <= 2.0 && count < N)
```

✔ Keep iterating until divergence or max steps

```c
setColor(1 + 254*count/N)
```

✔ Maps iteration count to grayscale range `[1, 255]`

```c
setPixel(i, j)
```

✔ Draws the pixel on the screen

---

## 8. The “Mandelbrot Bug”

* The famous black shape is the **actual Mandelbrot set**
* Black region → values that **never diverge**
* Surrounding gray region → values that **diverge slowly**
* Brighter pixels → **slower divergence**

✔ The boundary contains **infinite detail**

---

## 9. Zooming In

* You can **zoom into any boundary region**
* Reduce the complex-plane rectangle
* Increase image resolution or iteration count
* New, more detailed patterns appear endlessly

<img width="533" height="274" alt="image" src="https://github.com/user-attachments/assets/9b072a3e-c8b0-4519-a171-40f44fd1f0bd" />

---

## 10. Julia Sets (Related Concept)

### Difference from Mandelbrot:

| Mandelbrot | Julia      |
| ---------- | ---------- |
| z varies   | z is fixed |
| x₀ = 0     | x₀ varies  |
| Tests z    | Tests x₀   |

* Each fixed **z** produces a **different Julia set**
* Slight change in **z** → totally different image

<img width="1469" height="715" alt="image" src="https://github.com/user-attachments/assets/55b7ed58-9b07-4a2c-bbce-0a1a8708a613" />


## One-Line Exam Answers (Very Useful)

* The Mandelbrot set consists of complex numbers **z** for which the sequence ( x_{n+1} = x_n^2 + z ) does not diverge.
* Each pixel corresponds to a **complex number**.
* Pixel color depends on **divergence speed**.
* Threshold **|x| > 2** indicates divergence.
* Mandelbrot visualization is a direct example of **pixel-level graphics programming**.
