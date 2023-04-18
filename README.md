# RootDescent

rootdescent is a Python package for numerical analysis, offering tools for approximating roots and performing numerical integration.

## Features

rootdescent currently includes the following classes and methods:

### RootApproximator

This class provides methods for finding the roots of functions using various numerical approximation techniques. The available methods are:

- Bisection method (`bisection`)

## Bisection Method

The bisection method is a root-finding method that repeatedly bisects an interval and then selects a subinterval in which a root must lie for further processing. It is a simple and robust numerical method for approximating the root of a continuous function in a given interval.

Given a continuous function $f(x)$ and an interval $[a, b]$ such that $f(a)$ and $f(b)$ have opposite signs (i.e., $f(a) \cdot f(b) < 0$), the bisection method can be used to find an approximation of the root. The method works as follows:

1. Compute the midpoint $c$ of the interval $[a, b]$: $$c = \frac{a + b}{2}$$
2. Evaluate the function $f(c)$ at the midpoint $c$.
3. Determine the next interval based on the signs of $f(a)$, $f(b)$, and $f(c)$:
   - If $f(c) == 0$, then $c$ is the root.
   - If $f(a) \cdot f(c) < 0$, the root lies in the interval $[a, c]$, so update $b = c$.
   - If $f(b) \cdot f(c) < 0$, the root lies in the interval $[c, b]$, so update $a = c$.
4. Repeat steps 1-3 until the desired level of accuracy is achieved, or the maximum number of iterations is reached.




- Fixed-point iteration (`fixed_point_iteration`)

## Fixed Point Iteration and Formula

Fixed point iteration is a numerical method used to find the solution of an equation in the form x = g(x). The idea is to iteratively refine the approximation of the solution by applying the function g(x) to the previous approximation. Fixed point iteration converges to the true solution if the function g(x) fulfills certain conditions, such as having a derivative with absolute value less than 1 in the neighborhood of the fixed point.

The fixed-point iteration formula is given by:

$$
x_{n+1} = g(x_n)
$$

where $x_n$ is the current approximation of the solution, $g(x)$ is the function that transforms x, and $x_{n+1}$ is the next approximation of the solution.

To perform fixed point iteration, follow these steps:

1. Choose an initial approximation $x_0$.
2. Calculate $x_{n+1}$ using the formula $x_{n+1} = g(x_n)$.
3. Check for convergence. If the difference between $x_{n+1}$ and $x_n$ is smaller than a predetermined tolerance, then the iteration has converged, and $x_{n+1}$ is the solution. Otherwise, continue iterating.
4. Set $x_n = x_{n+1}$, and repeat steps 2 and 3 until convergence is achieved or a maximum number of iterations is reached.

It is important to note that fixed point iteration may not always converge or could converge slowly, depending on the function $g(x)$ and the initial approximation. In such cases, alternative methods like the Newton-Raphson method or bisection method might be more appropriate.


- Regula Falsi method (`regula_falsi`)
- Newton-Raphson method (`newton_raphson`)
- Secant method (`secant`)

### Integration

This class provides methods for approximating definite integrals of functions using various numerical integration techniques. The available methods are:

- Trapezoidal rule (`trapezoidal_rule`)
- Simpson's 1/3 rule (`simpsons_13_rule`)
- Simpson's 3/8 rule (`simpsons_38_rule`)

## Usage

Here's an example of how to use rootdescent to approximate the root of a function and the integral of another function:

```python
from rootdescent import RootApproximator, Integration

# Define the functions for root approximation and integration
def f(x):
    return x**2 - 4

def g(x):
    return x**3 - 6 * x**2 + 4 * x + 12

# Initialize the RootApproximator and Integration classes
root_approx = RootApproximator()
integration = Integration()

# Approximate the root of f(x) using the bisection method
root = root_approx.bisection(f, 0, 4, error=1e-6, display_iterations=False)
print(f"Root: {root}")

# Approximate the integral of g(x) using the trapezoidal rule
integral = integration.trapezoidal_rule(g, 1, 4, n=100)
print(f"Integral: {integral}")

```
## Installation

To install RootDescent, download the package and run the following command in your terminal or command prompt:

1. ``` pip install rootdescent ```
2. Clone this repository: ``` https://github.com/TshepoMK/rootdescent.git ```




Replace my_function with your desired function and adjust the initial guesses and error according to your needs.

Contributing
Contributions are welcome! Please submit pull requests with bug fixes or new features.

License
This project is released under the MIT License.

