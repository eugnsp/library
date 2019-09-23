# Numeric data structures and algorithms

## Table of contents

* [Binomial coefficient](#binomial-coefficient)
* [Arithmetic algorithms](#arithmetic-algorithms)
	* [Arithmetic means](#arithmetic-means)
	* [Division algorithms](#division-algorithms)
		* [Integer division](#integer-division)
	* [Kahan summation algorithm](#kahan-summation-algorithm)
* [Floating-point numbers](#floating-point-numbers)
	* [Denormal numbers](#denormal-numbers)
* [Linear equations solution algorithms](#linear-equations-solution-algorithms)
	* [Iterative methods](#iterative-methods)
		* [Jacobi method](#jacobi-method)
* [Matrix diagonalization](#matrix-diagonalization)
	* [Jacobi eigenvalue algorithm](#jacobi-eigenvalue-algorithm)
* [Wavelets](#wavelets)

---

## Binomial coefficient

:link:

* M.Dominus. [*How to calculate binomial coefficients*](https://blog.plover.com/math/choose.html)
* M.Dominus. [*How to calculate binomial coefficients, again*](https://blog.plover.com/math/choose-2.html)

---

## Arithmetic algorithms

### Arithmetic means

> To compute the arithmetic mean <code>&mu; = 1 / n &sum; x<sub>i</sub></code> in a numerically stable way, use the following recurrence relation: <code>&mu;<sub>n</sub> = &mu;<sub>n - 1</sub> + 1 / n (x<sub>n</sub> - &mu;<sub>n - 1</sub>)</code>.

:link:

* [*Numerically stable computation of arithmetic means*](https://diego.assencio.com/?index=c34d06f4f4de2375658ed41f70177d59) &ndash; D.Assencio (2015)
* [*Incremental calculation of weighted mean and variance*](https://fanf2.user.srcf.net/hermes/doc/antiforgery/stats.pdf) &ndash; T.Finch (2009)

### Division algorithms

<!-- https://en.wikipedia.org/wiki/Division_algorithm
https://web.stanford.edu/class/ee486/doc/chap5.pdf -->

#### Integer division

:link:

* [*Integer division*](http://bearcave.com/software/divide.htm) &ndash; I.Kaplan (1996)

### Kahan summation algorithm

:link:

* [*Kahan summation algorithm*](https://en.wikipedia.org/wiki/Kahan_summation_algorithm) &ndash; Wikipedia
* [*Kahan summation*](https://stackoverflow.com/questions/4940072/kahan-summation) &ndash; Stack Overflow

---

## Floating-point numbers

:link:

* [*What every computer scientist should know about floating-point arithmetic*](https://www.itu.dk/~sestoft/bachelor/IEEE754_article.pdf) &ndash; D.Goldberg
* [*Floating point arithmetic before IEEE 754*](https://blogs.mathworks.com/cleve/2019/01/18/floating-point-arithmetic-before-ieee-754/) &ndash; C.Moler (2019)
* [*Beating floating point at its own game: Posit arithmetic*](http://www.johngustafson.net/pdfs/BeatingFloatingPoint.pdf) &ndash; J.L.Gustafson, I.Yonemoto

:movie_camera:

* [*Demystifying floating point*](https://www.youtube.com/watch?v=k12BJGSc2Nc) &ndash; J.Farrier @ CppCon (2015)
* [*Beating floats at their own game*](https://www.youtube.com/watch?v=N05yYbUZMSQ) &ndash; J.Gustafson @ HPC Advisory Council Australia Conference (2017)

### Denormal numbers

:link:

* [*Denormal number*](https://en.wikipedia.org/wiki/Denormal_number) &ndash; Wikipedia
* [*Floating point denormals, insignificant but controversial*](https://blogs.mathworks.com/cleve/2014/07/21/floating-point-denormals-insignificant-but-controversial-2/) &ndash; C.Moler (2014)

:movie_camera:

* [*On subnormal floating point and abnormal timing*](https://www.youtube.com/watch?v=DftejgRgmc8) &ndash; D.Kohlbrenner @ IEEE Symposium on Security and Privacy (2015)

---

## Linear equations solution algorithms

### Iterative methods

:link:

* [*Iterative methods*](https://ocw.mit.edu/courses/mathematics/18-086-mathematical-methods-for-engineers-ii-spring-2006/readings/am62.pdf) &ndash; G.Strang (2006)

:book:

* Sec. 20.5: *Relaxation methods for boundary value problems* &ndash; [*Numerical recipes: The art of scientific computing.* W.H.Press, et al. Cambridge University Press, 3rd ed. (2007)](https://www.cambridge.org/ru/academic/subjects/mathematics/numerical-recipes/numerical-recipes-art-scientific-computing-3rd-edition)

#### Jacobi method

> A recurrence relation: <code>x<sub>k+1</sub> = D<sup>-1</sup> (D - A) x<sub>k</sub> + D<sup>-1</sup> b</code>, where the preconditioner `D` is the diagonal part of `A`: `D = diag(A)`.

:link:

* [*Jacobi method*](https://en.wikipedia.org/wiki/Jacobi_method) &ndash; Wikipedia
* [*Jacobi method*](http://mathworld.wolfram.com/JacobiMethod.html) &ndash; Wolfram MathWorld

:movie_camera:

* G.Strang. [Lec. 15: *Iterative methods and preconditioners*](https://www.youtube.com/watch?v=LtNVodIs1dI) &ndash; MIT 18.086 Mathematical methods for engineers II (2008)

---

## Matrix diagonalization

### Jacobi eigenvalue algorithm

:link:

* [*Jacobi eigenvalue algorithm*](https://en.wikipedia.org/wiki/Jacobi_eigenvalue_algorithm) &ndash; Wikipedia
* J.Lambers. [*Jacobi methods*](https://web.stanford.edu/class/cme335/lecture7.pdf) &ndash; CME 335 (2010)

:book:

* [Sec. 11.1: *Jacobi transformations of a symmetric matrix* &ndash; *Numerical recipes: The art of scientific computing.* W.H.Press, et al. Cambridge University Press, 3rd ed. (2007)](https://www.cambridge.org/ru/academic/subjects/mathematics/numerical-recipes/numerical-recipes-art-scientific-computing-3rd-edition)
* [Sec. 8.5: *Jacobi methods* &ndash; *Matrix computations.* G.H.Golub, C.F.Van Loan. Johns Hopkins University Press (2013)](https://my.siam.org/Store/Product/viewproduct/?ProductId=23915573)
* [Contrib. II/1: *The Jacobi method for real symmetric matrices* &ndash; *Handbook for automatic computation. Vol. II: Linear algebra.* H.Rutishause; J.H.Wilkinson, C.Reinsch (eds.). Springer (1971)](https://www.springer.com/gp/book/9783642869426)

---

## Wavelets

:movie_camera:

* [Lec. 27: *Multiresolution, wavelet transform and scaling function* &ndash; G.Strang @ MIT 18.085 Computational science and engineering I (2008?)](https://www.youtube.com/watch?v=LtNVodIs1dI)
* [Lec. 28: *Splines and orthogonal wavelets: Daubechies construction* &ndash; G.Strang @ MIT 18.085 Computational science and engineering I (2008?)](https://www.youtube.com/watch?v=LeafEHx9d0c)

:book:

* [Sec. 11.1: *Jacobi transformations of a symmetric matrix* &ndash; *Numerical recipes: The art of scientific computing.* W.H.Press, et al. Cambridge University Press, 3rd ed. (2007)](https://www.cambridge.org/ru/academic/subjects/mathematics/numerical-recipes/numerical-recipes-art-scientific-computing-3rd-edition)


<!--
https://www.math.wustl.edu/~wick/teaching/Math2605Notes/chap3.pdf

https://www.maths.tcd.ie/~dbennett/js/ising.pdf
-->
