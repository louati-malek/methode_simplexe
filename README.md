
## Overview

This project implements the **Nelder–Mead optimization algorithm in C++** to find the minimum of a function without requiring explicit gradient computation.

It combines numerical optimization with object-oriented programming, simplex management, polymorphism, and graphical visualization. The project also includes an extension for minimizing functions subject to a linear hyperplane constraint.

## Features

- **Nelder–Mead algorithm:** Implements reflection, expansion, contraction, and simplex reduction.
- **Multidimensional optimization:** Supports optimization problems in 1D, 2D, and 3D.
- **Object-oriented design:** Uses abstract classes, inheritance, encapsulation, and polymorphism.
- **Simplex management:** Represents and validates simplices with exactly \(n+1\) vertices in \(n\) dimensions.
- **Iteration history:** Stores successive simplex states to analyze convergence.
- **SVG visualization:** Generates graphical representations of simplex evolution in 1D and 2D.
- **Constrained optimization:** Extends the algorithm to minimize functions subject to a linear hyperplane constraint.

## Algorithm

At each iteration, the algorithm:

1. Evaluates the objective function at each simplex vertex.
2. Sorts the vertices according to their function values.
3. Computes the centroid, excluding the worst vertex.
4. Applies reflection and, when appropriate, expansion or contraction.
5. Reduces the simplex around the best vertex when necessary.
6. Checks the convergence criteria and stores the resulting simplex state.

The algorithm stops when both the function-value difference and the simplex size are below a specified tolerance, or when the maximum number of iterations is reached.

Default test parameters:

- Maximum iterations: `1000`
- Convergence tolerance: `1e-6`

## Project Architecture

| Class | Responsibility |
|---|---|
| `Fonction` | Abstract interface for objective functions |
| `Polynome` | Concrete polynomial objective function |
| `Simplexe` | Represents and validates a simplex |
| `NelderMead` | Implements the optimization algorithm |
| `CollectionSimplexe` | Stores the history of simplex states |
| `FonctionSurHyperplan` | Handles optimization under a linear constraint |

## Examples and Results

The implementation is tested on functions with known analytical minima.

| Dimension | Objective function | Theoretical minimum |
|---|---|---|
| 1D | \(f(x)=(x-2)^2\) | \(x^*=2\) |
| 2D | \(f(x)=(x-2)^2+(y-3)^2\) | \((x^*,y^*)=(2,3)\) |
| 3D | \(f(x)=(x-1)^2+(y-2)^2+(z-3)^2\) | \((x^*,y^*,z^*)=(1,2,3)\) |

The numerical results are consistent with the theoretical minima, with function values close to zero.

### Constrained Optimization

The project also considers the problem:

\[
\min f(x,y)=(x-2)^2+(y-3)^2
\]

subject to:

\[
x+y=3
\]

The constrained minimum is:

\[
(x^*,y^*)=(1,2), \qquad f(x^*,y^*)=2
\]

The constraint is handled by reconstructing one coordinate from the hyperplane equation, reducing the problem's dimension by one, and reusing the same optimization algorithm.

## Technologies and Concepts

- **Language:** C++
- **Standard Library:** `std::vector`, `std::sort`
- **Programming paradigms:** Object-oriented programming and polymorphism
- **Numerical methods:** Derivative-free optimization
- **Visualization:** SVG generation
- **Mathematics:** Simplex geometry, convergence criteria, and constrained optimization

## Learning Outcomes

This project strengthened my understanding of:

- Implementing numerical algorithms in C++.
- Designing reusable classes and abstract interfaces.
- Managing object copying and assignment.
- Validating class invariants and handling exceptions.
- Analyzing numerical convergence and optimization results.
- Visualizing algorithm behavior and extending an algorithm to constrained problems.

## Future Improvements

- Avoid repeated function evaluations by caching values at unchanged vertices.
- Add more benchmark functions and test cases.
- Improve convergence analysis and performance measurements.
- Extend visualization capabilities to three dimensions.

---

**Project focus:** Numerical Optimization · C++ · Applied Mathematics · Object-Oriented Programming
