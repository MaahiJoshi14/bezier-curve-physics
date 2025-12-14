#Bézier Curve with Physics & Sensor Control

##Project Overview

In this project, I created an interactive cubic Bézier curve that behaves like a flexible, springy rope. The curve reacts smoothly to real-time user input (mouse movement on the web), and I also visualize tangent vectors along the curve to better understand its direction and behavior at different points.

The main purpose of this assignment is to apply concepts from computer graphics and basic physics, specifically Bézier curve mathematics, tangent computation, and spring–damping motion, without relying on any built-in Bézier, physics, or animation libraries.

The project is implemented using HTML Canvas and plain JavaScript, and it runs in real time at around 60 FPS in a modern browser.

##Mathematical Background
Cubic Bézier Curve

A cubic Bézier curve is defined using four control points:

P₀ – starting point (fixed)

P₁ – first control point (moves dynamically)

P₂ – second control point (moves dynamically)

P₃ – ending point (fixed)

The position of the curve for a parameter 
𝑡
∈
[
0
,
1
]
t∈[0,1] is calculated using the standard cubic Bézier equation:

B(t) = (1 - t)^3 P0
     + 3(1 - t)^2 t P1
     + 3(1 - t) t^2 P2
     + t^3 P3

To draw the curve on the screen, I sample values of 
𝑡
t at small intervals and connect the resulting points using straight line segments. This approach approximates the smooth Bézier curve manually, without using any built-in Bézier drawing functions.

##Tangent Computation

To visualize the direction of the curve, I compute tangent vectors using the analytical derivative of the cubic Bézier equation:

B'(t) = 3(1 - t)^2 (P1 - P0)
      + 6(1 - t) t (P2 - P1)
      + 3 t^2 (P3 - P2)


The resulting vectors are normalized and drawn as short line segments at selected points along the curve. This helped me better understand how the curve direction changes as 
𝑡
t varies.

##Physics Model

To make the curve feel more natural and rope-like, the middle control points (P₁ and P₂) are not moved directly. Instead, I used a spring–damper model so that their movement feels smooth and slightly elastic.

The acceleration for each dynamic control point is calculated using:

a = -k (x - x_target) - d v
where:

k         = spring stiffness constant
d         = damping coefficient
v         = current velocity
x_target  = target position
​

 is the target position based on user input

To update motion over time, I used explicit Euler integration:

velocity += acceleration × dt
position += velocity × dt


Damping is important here because it prevents the control points from oscillating indefinitely and allows the motion to settle smoothly.

##Interaction Design
Web Interaction (Mouse Input)

On the web version, mouse movement controls a target offset relative to the center of the screen. This offset influences where P₁ and P₂ want to move, while the endpoints P₀ and P₃ always remain fixed.

Because the control points follow a spring system rather than snapping directly to the mouse position, the curve responds with a slight delay and overshoot, creating a motion that feels similar to a rope or elastic band.

##Rendering Approach

For each animation frame, the following steps are performed:

Update the spring physics for the dynamic control points

Sample and draw the Bézier curve

Compute and draw tangent vectors

Render the control points and the control polygon

The animation loop is driven using requestAnimationFrame, which keeps the rendering efficient and smooth.

##How to Run the Project

Clone or download this repository

Open index.html in any modern web browser

Move the mouse to interact with the Bézier curve

No additional setup or external libraries are required.

##Academic Integrity & Acknowledgment

This project was completed independently by me as part of an academic assignment. All implementation logic and code were written by me based on my understanding of computer graphics and basic physics concepts. External resources were used only for conceptual reference and learning purposes.

##References

Farin, G. (2002). Curves and Surfaces for Computer-Aided Geometric Design. Morgan Kaufmann.

Wikipedia contributors. (2024). Bézier curve.
https://en.wikipedia.org/wiki/B%C3%A9zier_curve

Wikipedia contributors. (2024). Damping.
https://en.wikipedia.org/wiki/Damping

OpenAI. (2025). ChatGPT (used for conceptual explanations of Bézier curves, tangent computation, and spring–damper systems).
https://openai.com/

##Submission Information

GitHub Repository Link:
https://github.com/MaahiJoshi14/bezier-curve-physics

GitHub Profile Link:
https://github.com/MaahiJoshi14
