
# 3.4 Scan-Converting an Ellipse 

## 1. Symmetry of an Ellipse (Important Difference)

Like a circle, an **ellipse is symmetric** — but:

* **Circle** → 8-way symmetry
* **Ellipse** → **4-way symmetry**

👉 Because an ellipse usually has **different major and minor axes**, diagonal symmetry does **not** exist.

### Four-way symmetry points

If one point is ((x, y)), the other symmetric points are:

* ((x, -y))
* ((-x, y))
* ((-x, -y))

So:
✔ Compute points in **one quadrant**
✔ Reflect them to get the full ellipse

---

## 2. Mathematical Definitions of an Ellipse

There are **two standard ways** to define an ellipse mathematically:

---

<img width="1052" height="655" alt="image" src="https://github.com/user-attachments/assets/68750231-1d1e-4d0c-997a-287770d262d5" />


### Why This Method Is Inefficient ❌

* Requires:

  * Squaring
  * Floating-point division
  * Square-root calculation
  * Floating-point multiplication
* Very **slow**
* Logic-intensive routines

👉 **Not suitable for real-time graphics**

---

<img width="946" height="407" alt="image" src="https://github.com/user-attachments/assets/c4198f86-2789-409e-909a-c546dba2aca6" />


### How It Works

* Vary (\theta) from **0 to (\pi/2)** (one quadrant)
* Compute (x, y) for each (\theta)
* Use **four-way symmetry** to complete the ellipse

---

### Efficiency Discussion

❌ Computing **sin** and **cos** repeatedly is slow
✔ Can be improved using **lookup tables**

📌 Exam point:

> This method was once impractical due to memory cost, but is now acceptable because memory is cheap.

Still:
👉 **Slower than incremental midpoint methods**

---

## 5. Key Observations (Very Exam-Important ⭐)

| Aspect               | Ellipse                     |
| -------------------- | --------------------------- |
| Symmetry             | 4-way                       |
| Computed region      | One quadrant                |
| Polynomial method    | Uses square root & division |
| Trigonometric method | Uses sin & cos              |
| Performance          | Both are inefficient        |

👉 Hence, **incremental midpoint ellipse algorithms** are preferred (next topic).

---

## 6. One-Line Exam Summary ⭐

> **Scan-converting an ellipse exploits its four-way symmetry and uses either polynomial or trigonometric definitions, though both are inefficient for real-time graphics.**

---

## 7. Quick Memory Trick 🧠

* **Circle** → 8-way symmetry → many reflections
* **Ellipse** → 4-way symmetry → fewer reflections
* **Polynomial & Trig** → slow
* **Midpoint ellipse** → fast (integer-based)
