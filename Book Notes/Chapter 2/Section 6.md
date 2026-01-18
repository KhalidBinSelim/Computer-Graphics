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
