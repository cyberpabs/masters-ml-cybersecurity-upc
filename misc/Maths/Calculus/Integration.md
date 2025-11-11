## 1. Immediate integration:

$$
\int \frac{1}{\sqrt{x}} dx = 2\sqrt{x}+C
$$

## 2. Almost immediate integrals (also a formula but more tricky)

$$
\int\frac{x}{x^2+10}dx=\frac{1}{2} \int\frac{2x}{x^2+10}dx=\frac{1}{2} ln|x^2+10|+C
$$

## 3. Integration by parts

Using the following formula:

$$
\int u*dv = u*v-\int v*du
$$

For example:

$$
\int x*sin x *dx = x * (-cosx)-\int -cosx*dx=x(-cosx)+sinx+C
$$

## 4. Rational Integrals

#### 4.1. Degree P(x)>=Q(x)

Like:

$$
\int \frac{P(x)}{Q(x)} dx
$$

For example:

$$
\int \frac{x^3-4}{x^2-2x}dx=
$$

Here we stop and divide the polynomials cause P(x)>Q(x):

$$
x^3 -4 \overline{(x^2-2x}
$$

That gives us a result of $x+2$ and a residue or mod $4x-4$
Now we continue the integration:

$$
= \int x+2 + \frac{4x-4}{x^2-2x}dx= \int x*dx+2\int dx+\int \frac{4x-4}{x^2-2x} dx=
$$

As we can see, the derivative of $x^2-2x = 2x-2$ so we can take 2 from the top part like this:

$$
\int\frac{2(2x-2)}{x^2-2x} = 2 * ln|x^2-2x| +C
$$

And now we take the 2 outside the integral and we join it all together:

$$
= \frac{x^2}{2}+2x+2*ln|x^2-2x|+C
$$

#### 4.2 Needs factorization

Given the following integral:

$$
\int \frac{4x+5}{x^2-3x+2}dx
$$

We set the denominator to zero and we do the equation:

$$
x^2-3x+2=0
$$

$$
x=\frac{3±\sqrt{9-8}}{2}
$$

This gives us $x_1=2$ and $x_2=1$ so we take our integral and continue it:

$$
\int \frac{4x+5}{x^2-3x+2}dx = \int \frac{4x+5}{(x-2)(x-1)}dx=\int \frac{A}{(x-2)}dx + \int \frac{B}{(x-1)} dx
$$

Now we give X the values we got from the second order equation:
$x=2$ and $x=1$.

$$
\frac{4x+5}{\cancel{(x-2)(x-1)}}=\frac{A(x-1)+B(x-2)}{\cancel{(x-2)(x-1)}}
$$

Now we find A and B:

$$
4x+5 = A(x-1)+B(x-2)
$$

$$
4*(2)+5 = A((2)-1)
$$

$$
13 = A
$$

$$
4*(1)+5 = B(1-2)
$$

$$
-9 = B
$$

We go back to the integral:

$$
\int \frac{A}{(x-2)}dx + \int \frac{B}{(x-1)} dx = \int\frac{13}{x-2}dx+\int\frac{-9}{x-1}dx
$$

$$
13\int \frac{1}{x-2}dx-9\int \frac{1}{x-1}dx=13*ln|x-2|-9*ln|x-1|+C
$$

## 4. Areas with 1 function

Given the following function, calculate the area.

$$
f(x) = x^3-3x
$$

![[Pasted image 20250403215943.png]]

First we need to do the polynomial and get the cutting points which are the following:

- $x_1=0$
- $x_2=0$
- $x_3=\sqrt{3}$ (We know a square root its ± so its two points)

We perform the integral in this points $(-\sqrt{3}, 0, \sqrt{3})$:

$$
\int_{0}^{\sqrt{3}} (x^3-3x)dx =  \biggl[\frac{x^4}{4}-3*\frac{x^2}{2} \biggl ]_{0}^{\sqrt{3}} = \bigg |{ \frac{9}{4}}\bigg |
$$

Now we do it for the negative values:

$$
\int_{-\sqrt{3}}^{0} (x^3-3x)dx =  \biggl[\frac{x^4}{4}-3*\frac{x^2}{2} \biggl ]_{-\sqrt{3}}^{0} = \bigg |{ \frac{9}{4}}\bigg |
$$

Now we perform the addition of the areas:

$$
A_{total}=\frac{9}{4}+\frac{9}{4}=\frac{18}{4}=\frac{9}{2}u^2
$$
