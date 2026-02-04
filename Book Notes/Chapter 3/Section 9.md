
# Midpoint Ellipse Algorithm 

## 1. What Is the Midpoint Ellipse Algorithm?

It is an **incremental scan-conversion algorithm** used to draw an ellipse:

* Centered at the **origin**
* Major and minor axes **parallel to x and y axes**
* Uses **only integer arithmetic**
* Very similar in spirit to the **midpoint circle algorithm**

Because an ellipse has **four-way symmetry**, we only compute points in the **first quadrant**, then reflect them.

---

<img width="697" height="734" alt="image" src="https://github.com/user-attachments/assets/78f3a69c-79ba-4e9e-938a-a1cadf85fc5e" />


## 4. Starting Point

We always start at the **top of the ellipse**:
[
(x,y) = (0,b)
]

<img width="628" height="536" alt="image" src="https://github.com/user-attachments/assets/64629221-d25d-4ae2-a91e-2dd8522edb74" />

<img width="716" height="742" alt="image" src="https://github.com/user-attachments/assets/5fed111b-04db-422c-aac4-99a539b31adb" />


## 8. Symmetry Usage

Once a point ((x,y)) is found in the first quadrant, plot:

* ((x, y))
* ((-x, y))
* ((x, -y))
* ((-x, -y))

This gives the **full ellipse**.

---

## 9. Key Exam Takeaways ⭐

* Uses **midpoint testing**
* Works in **two regions**
* Uses **integer arithmetic**
* Efficient and fast
* Similar to midpoint **circle**, but slightly more complex
* Exploits **four-way symmetry**

---

## 10. One-Line Exam Answer ⭐

> The midpoint ellipse algorithm is an incremental scan-conversion method that divides the ellipse into two regions based on slope and uses midpoint decision parameters to efficiently generate ellipse pixels using integer arithmetic.

