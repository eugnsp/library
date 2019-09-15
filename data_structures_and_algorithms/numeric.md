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

* [*How to calculate binomial coefficients* &ndash; M.Dominus](https://blog.plover.com/math/choose.html)
* [*How to calculate binomial coefficients, again* &ndash; M.Dominus](https://blog.plover.com/math/choose-2.html)

---

## Arithmetic algorithms

### Arithmetic means

> To compute the arithmetic mean <code>&mu; = 1 / n &sum; x<sub>i</sub></code> in a numerically stable way, use the following recurrence relation: <code>&mu;<sub>n</sub> = &mu;<sub>n - 1</sub> + 1 / n (x<sub>n</sub> - &mu;<sub>n - 1</sub>)</code>.

:link:

* [Numerically stable computation of arithmetic means &ndash; D.Assencio (2015)](https://diego.assencio.com/?index=c34d06f4f4de2375658ed41f70177d59)
* [Incremental calculation of weighted mean and variance &ndash; T.Finch (2009)](https://fanf2.user.srcf.net/hermes/doc/antiforgery/stats.pdf)

### Division algorithms

<!-- https://en.wikipedia.org/wiki/Division_algorithm
https://web.stanford.edu/class/ee486/doc/chap5.pdf -->

#### Integer division

:link:

* [Integer division &ndash; I.Kaplan (1996)](http://bearcave.com/software/divide.htm)

### Kahan summation algorithm

:link:

* [*Kahan summation algorithm* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Kahan_summation_algorithm)
* [*Kahan summation* &ndash; Stack Overflow](https://stackoverflow.com/questions/4940072/kahan-summation)

---

## Floating-point numbers

:link:

* [*What every computer scientist should know about floating-point arithmetic* &ndash; D.Goldberg](https://www.itu.dk/~sestoft/bachelor/IEEE754_article.pdf)
* [*Floating point arithmetic before IEEE 754* &ndash; C.Moler (2019)](https://blogs.mathworks.com/cleve/2019/01/18/floating-point-arithmetic-before-ieee-754/)
* [*Beating floating point at its own game: Posit arithmetic* &ndash; J.L.Gustafson, I.Yonemoto](http://www.johngustafson.net/pdfs/BeatingFloatingPoint.pdf)

:movie_camera:

* [*Demystifying floating point* &ndash; J.Farrier @ CppCon (2015)](https://www.youtube.com/watch?v=k12BJGSc2Nc)
* [*Beating floats at their own game* &ndash; J.Gustafson @ HPC Advisory Council Australia Conference (2017)](https://www.youtube.com/watch?v=N05yYbUZMSQ)

### Denormal numbers

:link:

* [*Denormal number* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Denormal_number)
* [*Floating point denormals, insignificant but controversial* &ndash; C.Moler (2014)](https://blogs.mathworks.com/cleve/2014/07/21/floating-point-denormals-insignificant-but-controversial-2/)

:movie_camera:

* [*On subnormal floating point and abnormal timing* &ndash; D.Kohlbrenner @ IEEE Symposium on Security and Privacy (2015)](https://www.youtube.com/watch?v=DftejgRgmc8)

---

## Linear equations solution algorithms

### Iterative methods

:link:

* [*Iterative methods* &ndash; G.Strang (2006)](https://ocw.mit.edu/courses/mathematics/18-086-mathematical-methods-for-engineers-ii-spring-2006/readings/am62.pdf)

:book:

* [Sec. 20.5: *Relaxation methods for boundary value problems* &ndash; *Numerical recipes: The art of scientific computing.* W.H.Press, et al. Cambridge University Press, 3rd ed. (2007)](https://www.cambridge.org/ru/academic/subjects/mathematics/numerical-recipes/numerical-recipes-art-scientific-computing-3rd-edition)

#### Jacobi method

> A recurrence relation: <code>x<sub>k+1</sub> = D<sup>-1</sup> (D - A) x<sub>k</sub> + D<sup>-1</sup> b</code>, where the preconditioner `D` is the diagonal part of `A`: `D = diag(A)`.

:link:

* [*Jacobi method* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Jacobi_method)
* [*Jacobi method* &ndash; Wolfram MathWorld](http://mathworld.wolfram.com/JacobiMethod.html)

:movie_camera:

* [Lec. 15: *Iterative methods and preconditioners* &ndash; G.Strang @ MIT 18.086 Mathematical methods for engineers II (2008)](https://www.youtube.com/watch?v=LtNVodIs1dI)

---

## Matrix diagonalization

### Jacobi eigenvalue algorithm

:link:

* [*Jacobi eigenvalue algorithm* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Jacobi_eigenvalue_algorithm)
* [*Jacobi methods* &ndash; J.Lambers, CME 335 (2010)](https://web.stanford.edu/class/cme335/lecture7.pdf)

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
