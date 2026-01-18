## **Supplementary Problems — Chapter 2**


## **2.42 Can a 5 by 3½ inch image be presented at 6 by 4 inch without introducing geometric distortion?**

### **Solution: No, it cannot.**

### **Explanation:**

To avoid geometric distortion, the **aspect ratio must remain the same**.

* Original image size = **5 × 3.5 inches**

* Aspect ratio =
  [
  \frac{5}{3.5} = \frac{10}{7} \approx 1.43
  ]

* New image size = **6 × 4 inches**

* Aspect ratio =
  [
  \frac{6}{4} = 1.5
  ]

Since **1.43 ≠ 1.5**, the aspect ratios are different.

✔ **Conclusion:**
The image **cannot** be resized to 6 × 4 inches **without distortion** (it will look stretched or squashed).

---

## **2.43 Referring to Prob. 2.42, what if the original is 5¼ by 3½ inch?**

### **Solution: Yes, it can be resized without distortion.**

### **Explanation:**

* Original size = **5.25 × 3.5 inches**

* Aspect ratio:
  [
  \frac{5.25}{3.5} = 1.5
  ]

* Target size = **6 × 4 inches**

* Aspect ratio:
  [
  \frac{6}{4} = 1.5
  ]

✔ **Conclusion:**
Both aspect ratios are the **same**, so resizing introduces **no geometric distortion**.

---

## **2.44 Given a portrait image of a person, describe a simple way to make the person look more slender.**

### **Solution:**

Resize the image by **reducing the horizontal scale only** while keeping the vertical scale unchanged.

### **Explanation:**

* Shrinking the width makes the person appear thinner
* Height remains unchanged → no vertical distortion
* This is a **non-uniform scaling** operation

✔ Example:
Scale width by **90%** and keep height at **100%**

⚠ Overdoing it will look unnatural, so the change should be subtle.

---

## 2.45 Convert an RGB image to a gray-scale image using

0.299R + 0.587G + 0.114B**

### **Given:**

* `getPixel(x, y, rgb)` reads RGB values from a **24-bit color image**
* `setPixel(x, y, i)` writes gray values to an output image using a **gray-scale lookup table**

---

### **Explanation:**

Human vision is:

* Most sensitive to **green**
* Less sensitive to **red**
* Least sensitive to **blue**

So we use a **weighted average** to compute the gray level.

---

### **Pseudo-code Solution:**

```
int x, y;
int rgb[3];
int gray;

for (y = 0; y < height; y++) {
    for (x = 0; x < width; x++) {
        getPixel(x, y, rgb);

        gray = 0.299 * rgb[0]
             + 0.587 * rgb[1]
             + 0.114 * rgb[2];

        setPixel(x, y, gray);
    }
}
```

---

### **Why this works:**

* Converts each color pixel into a **single intensity value**
* Produces a visually accurate gray-scale image
* Commonly used in **image processing and computer vision**

---

## ✅ **Quick Summary Table**

| Problem | Key Idea                                   |
| ------- | ------------------------------------------ |
| 2.42    | Aspect ratio mismatch → distortion         |
| 2.43    | Same aspect ratio → no distortion          |
| 2.44    | Horizontal shrinking makes subject slender |
| 2.45    | Weighted RGB → grayscale conversion        |

---

