## 2.6 Dithering

**Dithering** is a technique used to approximate halftones **without reducing spatial resolution**.
Unlike halftone approximation (which groups pixels into grids), dithering works **pixel by pixel** while preserving the original image resolution.

### Basic idea

* A **dither matrix** is repeatedly tiled over the entire image (like floor tiles).
* Each pixel compares its intensity with a threshold value from the dither matrix.
* The pixel is turned **ON** (printed/displayed) if its intensity is greater than the corresponding dither matrix value; otherwise it is turned **OFF**.

---

<img width="876" height="763" alt="image" src="https://github.com/user-attachments/assets/5f334b77-0a39-4764-a21c-438d120cd5ac" />


### Important observation

* For **constant-intensity image regions**, dithering produces **exactly the same result** as halftone approximation.
* Differences appear **only when intensity varies** across pixels.

---

## 2.7 Error Diffusion (Floyd–Steinberg)

Another method for continuous-tone reproduction **without reducing spatial resolution** is **error diffusion**, most notably the **Floyd–Steinberg algorithm**.

### Basic idea

1. Each pixel is converted to the **nearest intensity level** that the output device can produce.
2. The **quantization error** is calculated.
3. This error is **distributed to neighboring unprocessed pixels**, so the overall image brightness is preserved.

---

<img width="947" height="710" alt="image" src="https://github.com/user-attachments/assets/8d601bc1-f0e6-41cb-a476-bd69d193cf4b" />


### Key characteristics

* Preserves **spatial resolution**
* Produces **smoother visual results** than simple dithering
* Can introduce **worm-like artifacts** in some images
* Widely used in **printers and grayscale displays**

---

## Dithering vs Error Diffusion (Exam Table)

| Feature        | Dithering            | Error Diffusion   |
| -------------- | -------------------- | ----------------- |
| Resolution     | Preserved            | Preserved         |
| Method         | Threshold comparison | Error propagation |
| Complexity     | Low                  | Higher            |
| Visual quality | Good                 | Better            |
| Artifacts      | Pattern-based        | Worm patterns     |

---

## One-line Exam Answers

* **Dithering** uses a tiled threshold matrix to approximate halftones without reducing resolution.
* **Error diffusion** distributes quantization error to neighboring pixels to preserve overall intensity.
* **Floyd–Steinberg** is a popular error diffusion algorithm using weighted error propagation.
