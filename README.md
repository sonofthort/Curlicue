# Curlicue
An exploration of curlicue fractals.

As an amatuer mathematician/enthusiast, I've found it difficult to string together information pertaining to these fractals. This repo serves to coalesce information I've found, and to present my own findings (which could very well duplicate past mathematician's work, in which case, please let me know as I would love to learn more).

# What is a Curlicue Fractal?
There are varying definitions, as multiple approaches/formulas can generate what are described in literature as curlicue fractals. However, there is one connecting theme:
1. Define a function which produces an angle (theta) from a given integer:  $$θ(n)= ...$$
2. Starting from some origin point (typically $`(0, 0)`$), draw a line from this point at the angle produced by $`θ(1)`$, and with a length defined by some constant value $`r`$ (typically $`1`$).
3. From the endpoint of this line, continue to draw new lines, each at an angle determined by $`θ(n)`$ (where $`n`$ cooresponds to the line/iteration number, increasing sequentially by $`1`$), and each with length $`r`$.
4. Repeat this step up to some maximum $`n`$ value, $`m`$.

The resulting plot can vary significantly depening on our $`θ(n)`$ function. Some functions can produce chaotic/fractal patterns, where others can produce bounded or simply plots.
