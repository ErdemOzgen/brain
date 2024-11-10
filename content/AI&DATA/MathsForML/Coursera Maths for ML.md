
---
# Linear Algebra


## Singularity
https://community.deeplearning.ai/t/singular-vs-non-singular-naming/274873

Suppose the linear system we have is 

𝐴𝑥=𝑏

where 𝐴∈𝐑𝑛×𝑛 and 𝑥,𝑏∈𝐑𝑛.

You need to be a bit more precise to be correct to relate the number (or existence) of solutions to the singularity of 𝐴.

The following statements are correct:

1. A linear system has a unique solution if and only if the matrix is non-singular.
2. A linear system has either no solution or infinite number of solutions if and only if the matrix is singular.
3. A linear system has a solution if and only if 𝑏 is in the range of 𝐴.

Now by definition,

1. The matrix is non-singular if and only if the determinant is nonzero.

However, like your professor mentioned, you do not need to evaluate the determinant to see whether a matrix is singular or not (though most such methods evaluates the determinant as by-product).

For example, you can use [Gaussian elimination](https://en.wikipedia.org/wiki/Gaussian_elimination) to tell whether a matrix is singular. This has the following advantages.

1. The time complexity of Gaussian elimination is 𝑂(𝑛3) (whereas brute-force evaluation of determinant by the original definition takes 𝑂(𝑛!)).
2. Gaussian elimination evaluates the determinant as by-product (i.e., with no additional cost).

Hope this helps you!