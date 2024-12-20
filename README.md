**Project State Document: Inverse Pendulum on a Cart Simulation**

**1. Original Goals:**

The initial goal was to derive the equations of motion for an inverse pendulum on a cart using Lagrangian mechanics. This involved:

* Defining the system and its degrees of freedom.
* Determining the kinetic and potential energy of the system.
* Formulating the Lagrangian.
* Applying Lagrange's equations to derive the equations of motion.

**2. Lagrangian Formulation:**

Given the generalized coordinates *x* (cart position) and *θ* (pendulum angle from the upward vertical), and system parameters *M* (cart mass), *m* (pendulum mass), and *l* (pendulum length), the Lagrangian was formulated as:

$`L = \frac{1}{2} (M + m) \dot{x}^2 + \frac{1}{2} m l^2 \dot{\theta}^2 + m l \dot{x} \dot{\theta} \cos(\theta) - m g l \cos(\theta)`$

Applying Lagrange's equations yielded the following equations of motion (with an external force *F* on the cart):

* **Cart Equation:**  $`(M + m) \ddot{x} + m l \ddot{\theta} \cos(\theta) - m l \dot{\theta}^2 \sin(\theta) = F`$
* **Pendulum Equation:** $`l \ddot{\theta} + \ddot{x} \cos(\theta) - g \sin(\theta) = 0`$

**3. State-Space Formulation:**

The Lagrangian equations of motion were then converted into a state-space representation for simulation purposes. The state variables were defined as:

* $x_1 = x$ (cart position)
* $x_2 = \dot{x}$ (cart velocity)
* $x_3 = \theta$ (pendulum angle)
* $x_4 = \dot{\theta}$ (pendulum angular velocity)

This resulted in a set of non-linear first-order differential equations that describe the system's dynamics:

$`
\begin{equation}
\frac{d}{dt} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} = \begin{bmatrix}
x_2 \\
\frac{F - m g \sin(x_3) \cos(x_3) + m l x_4^2 \sin(x_3)}{M + m \sin^2(x_3)} \\
x_4 \\
\frac{(M + m) g \sin(x_3) - F \cos(x_3) - ml x_4^2 \sin(x_3) \cos(x_3)}{l (M + m \sin^2(x_3))}
\end{bmatrix}
\end{equation}
`$

**4. Current Goals Informing the Code:**

The current goals driving the code development are to create an interactive web-based simulation of the inverse pendulum on a cart, allowing the user to influence the system through:

* **Setting System Parameters:** Input boxes allow users to define the cart mass, pendulum mass, and pendulum length.
* **Applying a Base Force:** A range slider allows the user to apply a constant horizontal force to the cart.
* **Interactive Dragging:**  Clicking and dragging on the cart applies a force proportional to the distance between the mouse and the cart, providing a more intuitive control mechanism.

How can we analytically find stable perfectly damped PID parameters for both the cart and the pendulum?
