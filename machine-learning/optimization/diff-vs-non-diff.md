Simple differentiable functions can be optimized analytically using calculus. Typically, the objective functions that we are interested in cannot be solved analytically.

Optimization is significantly easier if the gradient of the objective function can be calculated, and as such, there has been a lot more research into optimization algorithms that use the derivative than those that do not.

Optimization algorithms that make use of the derivative of the objective function are fast and efficient.

Nevertheless, there are objective functions where the derivative cannot be calculated, typically because the function is complex for a variety of real-world reasons. Or the derivative can be calculated in some regions of the domain, but not all, or is not a good guide.

Some difficulties on objective functions for the classical algorithms described in the previous section include:

- No analytical description of the function (e.g. simulation).
- Multiple global optima (e.g. multimodal).
- Stochastic function evaluation (e.g. noisy).
- Discontinuous objective function (e.g. regions with invalid solutions).

As such, there are optimization algorithms that do not expect first- or second-order derivatives to be available.

These algorithms are sometimes referred to as black-box optimization algorithms as they assume little or nothing (relative to the classical methods) about the objective function.

A grouping of these algorithms include:

Direct Algorithms
Stochastic Algorithms
Population Algorithms