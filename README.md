# Curlicue
An exploration of curlicue fractals, with accompanying code.

![face1](media/face2.png "\"The Face\"")

As an amatuer mathematician/enthusiast, I've found it difficult to piece together curlicue fractal information. However, the learning process is rewarding, and I hope to continue to work towards a more formalized understanding. For the curious enthusiast like myself, this article aims to consolidate and link information.

I would also like to present some of my own findings, which could very well duplicate past work. If this is the case, I apologize in advance and would very much appreciate feedback.

# What is a Curlicue fractal?
> $$\text{Where the function } R(n) \text{ returns a rotation, the plot of each term of}$$
> $$\displaystyle\sum_{n=1}^m e^{i 2 \pi R(n)}$$
> $$\text{may exhibit chaotic behavior if } R(n) \bmod 1 \text{ is not periodic,}$$
> $$\text{otherwise will repeat a potentially intricate pattern after } P \text{ terms}$$
> $$\text{(where } P \text{ is the period of } R(n) \text{).}$$
*(An attempt at a generalized definition)*
 
![e8](media/e8.png "θ(n)=39 * n ^ 2")

The preceding formula can model a more intuitive system, and I hope to demonstrate that it is derived from a simple process. Multiple approaches can generate what are described as curlicue fractals. However, there is a common theme:
1. Define a function which produces an angle (*theta*) from a given integer $`n`$:  $$θ(n)= ...$$
2. Starting from some origin point (typically $`(0, 0)`$), draw a line at the angle produced by $`θ(1)`$, and with a length defined by some constant value $`r`$ (typically $`1`$).
3. From the endpoint of this line, draw a new line at angle $`θ(2)`$.
4. Repeat this process, drawing a line from the previous line, each at an angle determined by $`θ(n)`$ (where $`n`$ cooresponds to the line/iteration number, increasing sequentially by $`1`$), and each with length $`r`$.
5. Stop this process once a maximum $`n`$ value, $`m`$, is reached.

The resulting plot can vary significantly based on the $`θ(n)`$ function. Some can produce patterns which are chaotic/fractal, while others produce patterns which are bounded/simple.

## Example
1. Define a simple theta function: $$θ(n)=n$$
2. Let $`r=100`$.
3. Start at the origin $`(0, 0)`$:

![e1](media/e1.png)

4. Draw a line from this point at an angle of $`θ(1)`$ and with a length of $`r`$:

![e2](media/e2.png)

5. Next, draw a line from the end of the previous line, at an angle of $`θ(2)`$:

![e3](media/e3.png)

6. Repeat this for $`n=3`$:

![e4](media/e4.png)

6. If this process is repeated up to $`n=100`$, the following plot is produced:

![e5](media/e5.png)

Although interesting, this $`θ(n)`$ function is very simple and the resulting circular "*Spirograph*" pattern never deviates. A much more complex plot can be produced by simply squaring $`n`$, expressed as the function: $$θ(n)=n^2$$

The following plot is produced by this function:

![e6](media/e6.png)

When "zoomed out" ($`r=1`$), the resulting pattern can be seen on a much larger scale ($`m=1000000`$):

![e6](media/e7.png "θ(n)=n ^ 2")

# Relation to Euler's formula
Euler's formula is given by: $$e^{i θ}=\cos θ + i \sin θ$$
In the curlicue fractal process described previously, lines and points are drawn on a two dimensional plane. A line is drawn from the previous endpoint at an angle $`θ`$ calculated by $`θ(n)`$. A given endpoint can be expressed as a sum of previous endpoints:
$$x_{0}=0$$
$$y_{0}=0$$
$$x_{n}=x_{n - 1} + r \cos{θ(n)}$$
$$y_{n}=y_{n - 1} + r \sin{θ(n)}$$
This moving endpoint can instead be expressed as a complex number, where $`x`$ is the real part, and $`y`$ is the imaginary part (and instead plotted on the complex plane), and Euler's formula can further simplify the expression:
$$p_{0}=0$$
$$p_{n}=p_{n - 1} + r e^{i θ(n)}$$
This can also be expressed as a summation: $$p_{m}=\displaystyle\sum_{n=1}^m r e^{i θ(n)}$$
$`r`$ can then be extracted: $$r \displaystyle\sum_{n=1}^m e^{i θ(n)}$$
This demonstrates that $`r`$ is simply a scaling factor, and otherwise has no bearing on the summation and the resulting plot. $`r`$ can be removed, and the following can be succinctly expressed: $$\text{A curlicue fractal may result from the plot of each term of } \displaystyle\sum_{n=1}^m e^{i θ(n)} \text{, where } θ(n) \text{ is a function which produces an angle.}$$

# Revolutions vs. radians
Revolutions can sometimes be simpler to work with and more intiuative than radians.

In the previous examples, $`θ(n)`$ produces an angle (a radian value). If we would instead like our $`θ(n)`$ function to produce revolutions, we can multiply its result by $`2 \pi`$ to convert to radians: $$2 \pi θ(n)$$
Since $`θ(n)`$ no longer returns an angle in this case, we can instead use the name $`R(n)`$ for functions which produce a rotation. The previous summation can then be written as: $$\displaystyle\sum_{n=1}^m e^{i 2 \pi R(n)}$$

As it turns out, this is a helpful abstraction for the analysis of curlicue patterns, and is common in other sources, dating back to Gauss sums (and possibly earlier).

# Relation to modular arithmetic
There is an implicit modulo operation occuring within these summations.

The angle or revolutions for a given $`n`$ produced by $`θ(n)`$ or $`R(n)`$ respectively can be greater than $`2 \pi`$ or $`1`$, and can also be less than $`0`$. Modulation can be applied to these values since they will be used within $`\sin`$ and $`\cos`$, since: $$\sin θ=\sin(θ \bmod{2 \pi})$$ $$\cos θ=\cos(θ \bmod{2 \pi})$$
The implicit modulos within these sums can be explicitly added without affecting their results:
$$\displaystyle\sum_{n=1}^m e^{i θ(n)}=\displaystyle\sum_{n=1}^m e^{i (θ(n) \bmod{2 \pi})}$$
$$\displaystyle\sum_{n=1}^m e^{i 2 \pi R(n)}=\displaystyle\sum_{n=1}^m e^{i 2 \pi (R(n) \bmod 1)}$$

Although this seemingly complicates the sums without changing their behavior, noting this relationship lends itself to analysis, and also has implications for computation (as modular arithmetic may be employed to circumvent potential limits of a computer's numerical representation system).

[This article on modular arithmetic](https://github.com/sonofthort/Modular-Arithmetic) contains formulas which can be useful during analysis and which are referenced in this article.

[The Wikipedia article on modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic) also contains helpful formulas and identities. 

# Analysis of specific $`θ(n)`$ functions
In the following subsections, specific forms of $`θ(n)`$ are analyzed. Each exhibit their own behavior and intricacies, but also share some characteristics and analysis methodologies.

Also, since $`θ(n)`$ functions can be arbitratily mapped to $`R(n)`$ functions, these sections will study $`R(n)`$ functions for their tendency to simplify analysis.

## Analysis of $`R(n)=k`$
Let $`k`$ be an arbitrary real number. This is the simplest form of $`R(n)`$ functions.

Give: $$\displaystyle\sum_{n=1}^m e^{i 2 \pi R(n)}$$
Substituting $`R(n)`$ with $`k`$ yields: $$\displaystyle\sum_{n=1}^m e^{i 2 \pi k}$$
The summation function $`e^{i 2 \pi k}`$ is a constant, therefore: $$\displaystyle\sum_{n=1}^m e^{i 2 \pi k} = m e^{i 2 \pi k}$$
The resulting plot will simply be that of a line of length $`m`$ from the origin, at an angle of $`2 \pi k`$.

(TODO, show image)

### Range of $`k`$
Recall that an implicit modulo operation can be explicitly added to a rotation function: $$R(n)=k \bmod 1$$
This shows that only values within $`0 \leq k < 1`$ are of interest, as values outside of this range map to values within this range by $`\bmod 1`$.

In other words, all angles $`0 \leq θ < 2 \pi`$ can be represented by $`0 \leq k < 1`$.

For negative $`k`$ value mapping, we can refer to [these relationships](https://github.com/sonofthort/Modular-Arithmetic/blob/main/README.md#negative-numbers) to show that $`-k \bmod 1 = \lceil k \rceil - k`$.

## Analysis of $`R(n)=k n`$
Let $`k`$ be an arbitrary real number.

### Range of $`k`$
Since modulation can be applied to $`R(n)`$ functions, the function can be rewritten as: $$R(n)=k n \bmod 1$$

From here, a [modular multiplation rule](https://github.com/sonofthort/Modular-Arithmetic/blob/main/README.md#multiplication) can be applied: $$R(n)=(k \bmod 1) n \bmod 1$$

This shows that only values within $`0 \leq k < 1`$ are of interest, since values outside of this range map to values within this range by $`\bmod 1`$.

### Rational $`k`$ values
In the case that k is a rational number, $`k`$ can be expressed as $$k=a/b$$
where $`a`$ and $`b`$ are positive coprime integers ($`a/b`$ is a reduced fraction), and where $`b \neq 0`$ and $`a \lt b`$.

We can then rewrite $`R(n)`$ as: $$R(n)=a n / b \bmod 1$$
From here, we can use [modulus conversion](https://github.com/sonofthort/Modular-Arithmetic/blob/main/README.md#modulus-conversion): $$a n / b \bmod 1=(a n \bmod b) / b$$
The modulo operands are now integers, so an [integer modular multiplication rule](https://github.com/sonofthort/Modular-Arithmetic/blob/main/README.md#multiplication) can be applied: $$(a n \bmod b) / b = ((a \bmod b)(n \bmod b) \bmod b) /b$$
($`a \bmod b`$ is technically redundant, since $`0 \leq a \lt b`$)

As $`n`$ is the only variable, we can reduce the periodicity of this function to that of $`n \bmod b`$. Modulo is periodic by the modulus. Therefore, $`R(n)`$ will have a period of $`b`$. Is it possible that there are additional periods due to multiplication by $`a`$?

An algebraic approach can also be employed to determine the periodicity of this function. A period for a given function can be expressed as:$$f(x) = f(x + p) \text{, where } p \text{ is a period}$$
Apply this to our function, solve for all $`p`$ values: $$a n \equiv a (n + p) \pmod b$$
From the [Wikipedia modular arithmetic article](https://en.wikipedia.org/wiki/Modular_arithmetic#Basic_properties), we have the following:

> $$\text{If }a + k \equiv b + k \pmod m \text{, where } k \text{ is any integer, then } a \equiv b \pmod m \text{. (1)}$$
> 
> $$\text{If }k a \equiv k b \pmod m \text{ and } k \text{ is coprime with } m \text{, then } a \equiv b \pmod m \text{. (2)}$$

Attempt to apply these rules to cancel out terms:
- $`a n \equiv a (n + p) \pmod b`$
- $`a n \equiv a n + a p \pmod b`$
- This matches the form of rule (1), where $`a n`$ is the common term. Apply this rule.
- $`0 + a n \equiv a p + a n \pmod b`$
- $`0 \equiv a p \pmod b`$
- This now matches the form of the rule (2), where $`a`$ is the common term. Apply this rule.
- $`a 0 \equiv a p \pmod b`$
- $`0 = p \pmod b`$

Solving for $`p`$ yields every integer multiple of $`b`$, hence the period is $`b`$.

### Irrational $`k`$ values
This is a very handwavy "proof", but any irrational number $`k`$ can be approximated as a rational number (fraction) by $`k \approx \lfloor k z \rfloor / z`$, where $`z`$ is an integer.

As $`z`$ approaches $`\infty`$, the approximation error approaches $`0`$. In theory, the approximation becomes equivalent to $`k`$ at $`z = \infty`$.
$$\lim_{z\to\infty} k - \lfloor k z \rfloor / z = 0$$
$$\lim_{z\to\infty} \lfloor k z \rfloor / z = k$$

In this way, an irrational number can be thought of as a fraction of infinitely large terms. Irrational $`k`$ values should result in a period of $`\infty`$. In other words, the function is not periodic.

### Describing the plot
TODO, should always result in a circle of some radius based on k.

## Analysis of $`R(n)=k n^2`$
- TODO

## Analysis of $`R(n)=R(n-1) + k n ^ 2`$
- TODO

# Application to music
- TODO

# Relation to Gauss sums and theta functions
Although I would like to further explore and document these relations (while attemping to fill my knowledge gaps in the process), it's worth noting that summations which are similar to: $$\displaystyle\sum_{n=1}^m e^{i 2 \pi R(n)}$$ can be found referenced in materials pertaining to Gauss sums and theta functions:
- [Gauss sum (Wikipedia)](https://en.wikipedia.org/wiki/Gauss_sum)
- [Quadratic Gauss sum (Wikipedia)](https://en.wikipedia.org/wiki/Quadratic_Gauss_sum)
- [Theta function (Wikipedia)](https://en.wikipedia.org/wiki/Theta_function)
