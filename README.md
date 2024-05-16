# Curlicue
An exploration of curlicue fractals.

As an amatuer mathematician/enthusiast, I've found it difficult to string together information pertaining to these fractals. This repo serves to coalesce information I've found, and to present my own findings (which could very well duplicate past mathematician's work, in which case, please let me know as I would love to learn more).

# What is a Curlicue Fractal?
There are varying definitions, as multiple approaches/formulas can generate what are described in literature as curlicue fractals. However, there is one connecting theme:
1. Define a function which produces an angle (theta) from a given integer $`n`$:  $$θ(n)= ...$$
2. Starting from some origin point (typically $`(0, 0)`$), draw a line from this point at the angle produced by $`θ(1)`$, and with a length defined by some constant value $`r`$ (typically $`1`$).
3. From the endpoint of this line, continue to draw new lines, each at an angle determined by $`θ(n)`$ (where $`n`$ cooresponds to the line/iteration number, increasing sequentially by $`1`$), and each with length $`r`$.
4. Repeat this step up to some maximum $`n`$ value, $`m`$.

The resulting plot can vary significantly depening on the $`θ(n)`$ function. Some functions can produce chaotic/fractal patterns, where others can produce bounded or simply plots.

Here is an example:
1. Define a very simple theta function: $$θ(n)=n$$
2. Let $`r=100`$ to assist in visualization.
3. Start at the origin $`(0, 0)`$:

![e1](media/e1.png)

4. Draw a line from this point at an angle of $`θ(1)`$ and with a length of $`r`$:

![e2](media/e2.png)

5. Next, draw a line from the end of the previous line, at an angle of $`θ(2)`$:

![e3](media/e3.png)

6. Do this again for $`n=3`$:

![e4](media/e4.png)

6. If we repeat this process up to $`n=100`$, we will achieve the following plot:

![e5](media/e5.png)

This is a rather uninteresting example as the function $`θ(n)`$ is very simple and does not produce a chaotic pattern.
