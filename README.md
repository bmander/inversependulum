**Project State Document: Inverse Pendulum on a Cart Simulation**

**1. Original Goals:**

The initial goal was to derive the equations of motion for an inverse pendulum on a cart using Lagrangian mechanics. This involved:

* Defining the system and its degrees of freedom.
* Determining the kinetic and potential energy of the system.
* Formulating the Lagrangian.
* Applying Lagrange's equations to derive the equations of motion.

**2. Lagrangian Formulation:**

Given the generalized coordinates *x* (cart position) and *θ* (pendulum angle from the upward vertical), and system parameters *M* (cart mass), *m* (pendulum mass), and *l* (pendulum length), the Lagrangian was formulated as:

```
L = (1/2) * (M + m) * ẋ² + (1/2) * m * l² θ̇² + m * l * ẋ * θ̇ * cos(θ) - m * g * l * cos(θ)
```

Applying Lagrange's equations yielded the following equations of motion (with an external force *F* on the cart):

* **Cart Equation:**  `(M + m) * ẍ + m * l * θ̈ * cos(θ) - m * l * θ̇² * sin(θ) = F`
* **Pendulum Equation:** `l * θ̈ + ẍ * cos(θ) - g * sin(θ) = 0`

**3. State-Space Formulation:**

The Lagrangian equations of motion were then converted into a state-space representation for simulation purposes. The state variables were defined as:

* x₁ = *x* (cart position)
* x₂ = ẋ (cart velocity)
* x₃ = *θ* (pendulum angle)
* x₄ = θ̇ (pendulum angular velocity)

This resulted in a set of non-linear first-order differential equations that describe the system's dynamics:

```
d/dt [x₁]   [ x₂                                                                                                   ]
d/dt [x₂] = [ (F - m * g * sin(x₃) * cos(x₃) + m * l * x₄² * sin(x₃)) / (M + m * sin²(x₃))                           ]
d/dt [x₃]   [ x₄                                                                                                   ]
d/dt [x₄]   [ ((M + m) * g * sin(x₃) - F * cos(x₃) - ml * x₄² * sin(x₃) * cos(x₃)) / (l * (M + m * sin²(x₃))) ]
```

**4. Current Goals Informing the Code:**

The current goals driving the code development are to create an interactive web-based simulation of the inverse pendulum on a cart, allowing the user to influence the system through:

* **Setting System Parameters:** Input boxes allow users to define the cart mass, pendulum mass, and pendulum length.
* **Applying a Base Force:** A range slider allows the user to apply a constant horizontal force to the cart.
* **Interactive Dragging:**  Clicking and dragging on the cart applies a force proportional to the distance between the mouse and the cart, providing a more intuitive control mechanism.

How can we analytically find stable perfectly damped PID parameters for both the cart and the pendulum?
