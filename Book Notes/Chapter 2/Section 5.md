<img width="746" height="415" alt="image" src="https://github.com/user-attachments/assets/1c9d59cf-b5b8-4984-bfb7-5181b5c87082" />


## 1. What is a display monitor?

* A display monitor (or video monitor) **converts digital images into visible pictures**
* Two main types: **monochrome (black & white)** and **color**
* Most older monitors use a **Cathode Ray Tube (CRT)**

---

## 2. How a monochrome CRT works

### Components:

1. **Phosphor-coated screen**

   * Glows when hit by electrons
   * Emits light (fluorescence)
   * Continues glowing after electron beam is gone (phosphorescence)
   * **Persistence** = how long it glows

2. **Electron gun**

   * Sends electrons toward the screen
   * Intensity of electrons → brightness of pixel

3. **Deflection system**

   * **Horizontal plates** → scan left to right, then retrace
   * **Vertical plates** → scan top to bottom, then retrace
   * Alternative: **magnetic deflection coils**

4. **Control circuits**

   * Synchronize beam movement
   * Control intensity according to pixel value
   * Shut off beam during retraces

---

### 3. Frame buffer & refresh rate

* Image is stored in **frame buffer (refresh buffer)**
* **Refresh rate** = how many times per second image is sent to the screen

  * Typical: 60 Hz or higher
* **Purpose:** avoid flicker
* **Interlacing:**

  * Refresh **odd lines first**, then **even lines**
  * Reduces flicker without increasing full-screen refresh speed

---

## 4. How a color CRT works

### Main differences from monochrome:

1. **Three electron guns** → Red, Green, Blue
2. **Screen phosphors** arranged in **dot triads**:

   * Each dot emits R, G, or B light
3. **Shadow mask** → ensures each electron beam hits the correct phosphor dot
4. **Pitch** → distance between triad centers; affects maximum resolution

### How colors are formed:

* Light from the three phosphors **blends together**
* Our eyes perceive it as a single **color**

---

<img width="749" height="356" alt="image" src="https://github.com/user-attachments/assets/04893de9-8d91-48cd-a611-fc703df5be3a" />


## 5. Key points to remember

| Feature         | Monochrome CRT        | Color CRT                                      |
| --------------- | --------------------- | ---------------------------------------------- |
| Electron guns   | 1                     | 3 (R, G, B)                                    |
| Phosphor        | Single type           | Dot triads (R, G, B)                           |
| Color formation | N/A                   | Beam hits corresponding phosphor; colors blend |
| Shadow mask     | N/A                   | Ensures correct beam-phosphor alignment        |
| Persistence     | Needed for visibility | Same                                           |
| Refresh rate    | 60 Hz or more         | Same                                           |

---

## 6. Key Exam Terms

* **Fluorescence** → light emitted while electron beam hits phosphor
* **Phosphorescence** → continued glow after beam stops
* **Persistence** → how long phosphor glows
* **Frame buffer** → memory storing image for display
* **Refresh rate** → how often frame buffer is displayed per second
* **Interlacing** → refresh half of lines first to reduce flicker
* **Shadow mask** → directs electron beams to correct phosphor dots
* **Pitch** → distance between phosphor triads, limits resolution

---

## One-Line Exam Answers

* **CRT monitor** uses an electron beam to excite phosphor pixels on a screen.
* **Frame buffer** stores pixel values; refresh rate determines flicker-free display.
* **Color CRT** uses three guns (R,G,B), dot triads, and a shadow mask to display colors.
* **Interlacing** refreshes odd and even lines alternately to reduce flicker.

---
