The **chain rule** is a fundamental concept in [[calculus]] used to find the derivative of a **composite function**, that is, a function that is inside another function.

Think of it like a set of **nested boxes**: to open the outer box, you first have to open the inner one. If you have a function $f(g(x))$, where $f$ depends on $g(x)$, and $g(x)$ in turn depends on $x$, the chain rule says that the **rate of change** of the whole function with respect to $x$ is the product of two rates:

1. The rate of change of the **outer function** ($f$) with respect to the **inner function** ($g(x)$).
2. The rate of change of the **inner function** ($g$) with respect to **its variable** ($x$).

Essentially, you take the derivative of the **outside function**, leave the **inside function alone**, and then multiply the result by the derivative of the **inside function**.

### The Mathematical Form

If we let $y=f(u)$ and $u=g(x)$, the rule is formally expressed as:

$$
\frac{dx}{dy} = \frac{dy}{du}· \frac{du}{dx}
$$

This form visually represents the "chain" connecting the derivative of $y$ with respect to $x$.