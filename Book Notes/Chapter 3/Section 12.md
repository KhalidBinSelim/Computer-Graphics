# 3.8 Scan-Converting a Character — Big Picture

Characters (letters, digits, symbols) are just **graphics**.
To show text on a screen, the computer must **convert characters into pixels** — that process is called **scan conversion**.

There are **two main ways** to represent characters:

1. **Bitmap (Raster) Fonts**
2. **Outline (Vector) Fonts**

Everything in this section compares these two.

---

## Characters, Fonts, and Sizes (Basics First)

### Characters

* Letters (A–Z), digits (0–9), punctuation
* These are the **building blocks of text**

### Typeface / Font

* A **font** defines how characters look
* Examples:

  * Arial
  * Times New Roman
  * Courier
  * Century Schoolbook

### Font Styles

* Normal
* **Bold**
* *Italic*
* **Bold Italic**

---

## Character Size Units

Character size usually means **height**, measured in:

* **Inches**
* **Points** → 1 point ≈ 1/72 inch
* **Picas** → 1 pica = 12 points

So:

* 12-point font ≈ 1/6 inch tall

---

# Bitmap Font (Raster Font)

### What Is a Bitmap Font?

A **bitmap font** represents each character as a **grid of pixels**.

* Each pixel is either:

  * ON (1)
  * OFF (0)
* This grid is called a **bitmap**

📌 Think of it as **pixel art letters**

---

### Example (Fig. 3-20)

Each letter:

* Is stored as a **fixed pixel pattern**
* Already scan-converted
* No math needed to draw it

---

### How Bitmap Characters Are Drawn

To display a character:

1. Take its bitmap
2. Copy it directly to the image buffer
3. Place it at the desired screen position

✅ Very fast
✅ Very simple

---

### Major Problem with Bitmap Fonts ❌

You need a **separate bitmap for every combination** of:

* Font type
* Font size
* Style (bold, italic, etc.)

Example:

* Arial 10-point
* Arial 12-point
* Arial 12-point bold
* Arial 12-point italic
  → **All need different bitmaps**

That’s a LOT of storage.

---

## Fake Styling Tricks (Fig. 3-21)

### Making Bold

* Overlay the bitmap with a **1-pixel horizontal shift**
* Pixels become thicker

### Making Italic

* Shift rows of pixels sideways
* Top shifts less, bottom shifts more

⚠️ These tricks:

* Work only approximately
* Look rough and low quality

---

## Resolution Dependency (Very Important)

Bitmap fonts depend on **screen resolution**.

### Example from the text:

* Font bitmap height = 12 pixels
* Screen resolution = 72 pixels/inch

So:
[
12 \text{ pixels} = \frac{12}{72} = \frac{1}{6} \text{ inch} = 12 \text{ points}
]

But if resolution = 96 pixels/inch:
[
12 \text{ pixels} = 0.125 \text{ inch} ≈ 9 \text{ points}
]

👉 Same bitmap, different size!

To get 12-point text at 96 PPI:

* You need **16-pixel-high bitmaps**

❌ This makes bitmap fonts inflexible.

---

# Outline Font (Vector Font)

Now comes the smarter method.

---

### What Is an Outline Font?

Instead of pixels, characters are defined using:

* **Lines**
* **Curves**
* **Arcs**

These primitives form the **outline** of the character.

📌 Think of characters as **drawings**, not pixel grids.

(Fig. 3-22 shows this)

---

### Why Outline Fonts Are Powerful

Even though:

* They need more computation
* Scan conversion takes time

They allow:

✅ Any size
✅ Any orientation
✅ Smooth scaling
✅ High quality

---

## Transformations (Key Advantage)

Outline fonts can be transformed mathematically:

* **Scaling** → change size
* **Shearing** → italic
* **Rotation** → angled text

These transformations are covered in **Chapter 4**, but the idea is:

> Modify the geometry → then scan-convert

---

## How Outline Fonts Are Scan-Converted

Two approaches:

### 1️⃣ Direct Scan Conversion

* Convert transformed outlines into filled pixel regions
* Each time the character appears

### 2️⃣ Bitmap Generation (Efficient Way)

* Convert outline → bitmap once
* Reuse bitmap for repeated characters

This saves time when the same character appears many times.

---

# Bitmap vs Outline Font — Quick Comparison

| Feature                 | Bitmap Font | Outline Font   |
| ----------------------- | ----------- | -------------- |
| Representation          | Pixels      | Lines & curves |
| Size flexibility        | ❌ Fixed     | ✅ Any size     |
| Resolution independence | ❌ No        | ✅ Yes          |
| Storage                 | Large       | Compact        |
| Quality                 | Blocky      | Smooth         |
| Scan conversion cost    | Very low    | Higher         |

---

## One-Line Exam Summary ⭐

> Bitmap fonts store characters as fixed pixel patterns and are simple but resolution-dependent, whereas outline fonts represent characters using geometric primitives, allowing flexible scaling, rotation, and styling through scan conversion.
