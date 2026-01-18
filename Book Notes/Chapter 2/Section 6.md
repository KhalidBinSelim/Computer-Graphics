## 1. How printers work

* A printer **puts color pigments onto paper**
* Paper reflects light → we see the printed image
* Main pigments: **Cyan, Magenta, Yellow (CMY)** → mix to make all RGB colors
* **Black (K)** is often added:

  * Cheaper than mixing CMY to make black
  * Produces better-quality blacks

---
<img width="644" height="159" alt="image" src="https://github.com/user-attachments/assets/a4e38dd8-1269-4cf5-bc51-2dc5ce6e6c55" />

## 2. Halftoning (for bilevel printers)

* Printers often **can’t vary pigment intensity continuously**
* **Halftoning** = trick to simulate different intensities

  * Use **small dots of varying size**
  * Viewed from far away → our eyes perceive **smooth shades**
* Dots are often placed at a **45° angle** to avoid patterns
* Examples:

  * Newspapers: 60–80 dots/inch
  * Books/magazines: 120–200 dots/inch

---
<img width="707" height="430" alt="image" src="https://github.com/user-attachments/assets/e8c04ffa-43c1-4169-8bb1-18161f74c08a" />

## 3. Halftone approximation using pixel grids

* Instead of changing dot size, use **pixel patterns (dither patterns)**
* Example: 2×2 grid of pixels → can produce **5 intensity levels**
* If pixels can have multiple intensity levels → more overall intensities

  * Example: 2×2 grid, 4 intensity levels per pixel → 13 intensity levels
* These grids approximate **shades of gray or color**

---

### 4. Design considerations for dither patterns

1. Intensify pixels **from the center outward**
2. Once a pixel is intensified, it should **stay at that level** in later patterns
3. Avoid **symmetry** → reduces visual streaks
4. Avoid **isolated “on” pixels** → hard to reproduce

* Use a **dither matrix** to define the order of pixel intensities
* Example: 3×3 matrix → 10 intensity levels for bilevel, 19 levels for 3-level pixels

---

## 5. Applying halftoning to color

* Replace each pixel dot with **RGB or CMY triad patterns**
* Example: 2×2 grid, 2 intensity levels per primary → 5×5×5 = **125 color combinations**

💡 Key idea: **Halftoning trades spatial resolution for more colors/intensity levels**

* Example: 400×400 pixels/inch printer → 2×2 halftone → effective resolution = 200×200 pixels/inch

---


# **How the math of halftoning works**


## **1. Why halftoning works at all**

A single pixel can show only a **limited number of intensity levels** (for example, ON or OFF).

 Instead of changing intensity of one pixel, we:

* **Group pixels together** (like a 2×2 or 3×3 grid)
* Change **how many pixels are ON**

Your eye **averages** them and perceives **shades of gray**.

---

## **2. 2×2 grid with bilevel pixels (ON / OFF)**

### Step 1: Count pixels

A 2×2 grid has:

[
2 \times 2 = 4 \text{ pixels}
]

Each pixel can be:

* OFF (0)
* ON (1)

---

### Step 2: How many ON pixels can we have?

Possible number of ON pixels:

* 0 → all OFF (black)
* 1
* 2
* 3
* 4 → all ON (white)

So total intensity levels:

[
4 + 1 = 5 \text{ levels}
]

✔ **That’s where “5 intensity levels” comes from**

---

## **3. General rule (important for exams)**

For an **n × n grid** with **bilevel pixels**:

[
\text{Intensity levels} = n^2 + 1
]

Example:

* 3×3 → (9 + 1 = 10) levels
* 4×4 → (16 + 1 = 17) levels

---

## **4. 2×2 grid with multiple intensity levels per pixel**

Now pixels are **not just ON/OFF**.

### Given:

* Grid = 2×2 → 4 pixels
* Each pixel has **4 intensity levels**: 0,1,2,3

---

### Step 1: Maximum total intensity

Each pixel max = 3
Total max intensity:

[
4 \times 3 = 12
]

---

### Step 2: Count total possible overall intensities

Possible total intensities:
[
0, 1, 2, ..., 12
]

Total number of levels:

[
12 + 1 = 13
]

✔ **That’s why:**

> **2×2 grid + 4 levels per pixel → 13 intensity levels**

---

## **5. General formula (VERY IMPORTANT)**

For an **n × n grid** with **m intensity levels per pixel**:

[
\boxed{\text{Overall intensity levels} = n^2 (m - 1) + 1}
]

---

### Example check:

* n = 2
* m = 4

[
2^2 (4 - 1) + 1 = 4 \times 3 + 1 = 13
]

✔ Matches perfectly.

---

## **6. Why “intensify from the center outward”?**

Your eyes are **most sensitive to clusters**, not isolated dots.

So:

* First turn ON center pixels
* Then move outward

This:
✔ Looks smoother
✔ Avoids noisy patterns

---

## **7. Why “once ON, stay ON”?**

If a pixel turns ON and later turns OFF:

* Image flickers
* Causes visual artifacts

So:
✔ Each intensity pattern is a **superset** of the previous one

---

## **8. Why avoid symmetry and isolated pixels?**

### Symmetry:

* Creates visible repeating patterns (streaks)

### Isolated pixels:

* Hard for printers to reproduce
* Look noisy to human eye

✔ Random-looking but ordered patterns look best

---

## **9. What is a dither matrix doing mathematically?**

A **dither matrix**:

* Assigns a **priority order** to pixels
* Lower value = turn ON earlier

Example 3×3 matrix:

```
0 7 3
6 5 2
4 1 8
```

As intensity increases:

* Pixels turn ON in this order
* Produces smooth gray transitions

---

## **10. Why 3×3 bilevel → 10 levels?**

Pixels = 9
Bilevel → ON/OFF

[
9 + 1 = 10 \text{ intensity levels}
]

✔ Simple counting again

---

## **11. Why 3-level pixels give 19 levels in 3×3?**

* n = 3 → 9 pixels
* m = 3 intensity levels (0,1,2)

[
9(3 - 1) + 1 = 18 + 1 = 19
]

---

## **12. Halftoning for color (this looks scary but isn’t)**

### Example:

* 2×2 grid
* 2 intensity levels per primary (0 or 1)

Each primary:
[
5 \text{ levels (from halftoning)}
]

For RGB:
[
5 \times 5 \times 5 = 125 \text{ colors}
]

✔ Each color channel is halftoned **independently**

---

## **13. Resolution trade-off (last example)**

Printer resolution:
[
400 \times 400 \text{ pixels/inch}
]

Using **2×2 halftone cells**:

* Each cell becomes **one effective pixel**

So:
[
400 / 2 = 200
]

✔ Effective resolution:
[
200 \times 200 \text{ pixels/inch}
]

---

## **Key idea to remember for exams**

> **Halftoning increases intensity/color levels by grouping pixels, but reduces spatial resolution.**

---




## 6. Key Exam Points

| Concept                  | Explanation                                                          |
| ------------------------ | -------------------------------------------------------------------- |
| Pigments                 | CMY (main), K (black)                                                |
| Halftoning               | Use dot size/pattern to simulate intensity                           |
| Pixel-grid approximation | Use small grids (e.g., 2×2) to create multiple intensity levels      |
| Dither patterns          | Determine pixel intensity sequence; avoid symmetry & isolated pixels |
| Trade-off                | More colors/intensity → lower effective resolution                   |

---

## One-Line Exam Answers

* **Printers use CMY pigments (and often black) to produce colors.**
* **Halftoning** simulates continuous intensity using dot patterns.
* **Dither patterns** in pixel grids approximate multiple intensity levels.
* Halftoning **trades resolution for more colors/intensity levels**.

---
