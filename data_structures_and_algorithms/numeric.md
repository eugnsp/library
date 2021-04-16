# Numeric data structures and algorithms <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [Floating-point arithmetic](#floating-point-arithmetic)
	- [IEEE 754](#ieee-754)
		- [Denormal numbers](#denormal-numbers)
		- [NaNs](#nans)
	- [Applications](#applications)
- [Arithmetic algorithms](#arithmetic-algorithms)
	- [Arithmetic means](#arithmetic-means)
	- [Binomial coefficient](#binomial-coefficient)
	- [Division algorithms](#division-algorithms)
		- [Integer division](#integer-division)
	- [Horner’s method](#horners-method)
	- [Kahan summation algorithm](#kahan-summation-algorithm)
	- [Powers and logarithms](#powers-and-logarithms)
		- [Square root](#square-root)
		- [Inverse square root](#inverse-square-root)
- [Prime numbers](#prime-numbers)
- [Linear equations solution algorithms](#linear-equations-solution-algorithms)
	- [Iterative methods](#iterative-methods)
		- [Jacobi method](#jacobi-method)
- [Matrix diagonalization](#matrix-diagonalization)
	- [Jacobi eigenvalue algorithm](#jacobi-eigenvalue-algorithm)
- [Wavelets](#wavelets)
- [Applications](#applications-1)
	- [Finite elements and finite volume methods](#finite-elements-and-finite-volume-methods)
	- [Spacecrafts dynamics](#spacecrafts-dynamics)

---

## Introduction and overview

:link:

- R.Munafo. [*Notable properties of specific numbers*](https://mrob.com/pub/math/numbers.html)

:movie_camera:

- S.Strogatz. [*The beauty of calculus*](https://www.youtube.com/watch?v=1r6893ga_So) (2019)
- S.Strogatz. [*The joy of `x`: A guided tour of math*](https://www.youtube.com/watch?v=lmL8RKB7mlE) (2014)

---

## Floating-point arithmetic

> Floating-point arithmetic is arithmetic in which real numbers are represented approximately to a fixed number of significant digits and scaled using an exponent in some fixed base: <code>r = significand &times; base<sup>exponent</sup></code>. The relative error due to rounding is uniform, i.e. it is independent of the magnitude of the number. The binary-based floating-point system has the smallest possible wobble (a range of relative errors).

:link:

- [*Floating-point arithmetic*](https://en.wikipedia.org/wiki/Floating-point_arithmetic) – Wikipedia
- C.Moler. [*Floating point arithmetic before IEEE 754*](https://blogs.mathworks.com/cleve/2019/01/18/floating-point-arithmetic-before-ieee-754/) (2019)

:page_facing_up:

- J.Gustafson, I.Yonemoto. [*Beating floating point at its own game: Posit arithmetic*](http://www.johngustafson.net/pdfs/BeatingFloatingPoint.pdf)

### IEEE 754

> IEEE 754 is a technical standard for floating-point arithmetic established in 1985 by the Institute of Electrical and Electronics Engineers (IEEE). If two (non-extended) floating-point numbers in the same format are ordered, then they are ordered the same way when their bits are reinterpreted as sign-magnitude integers. NaNs are endowed with a field of bits into which software can record, say, how and/or where the NaN came into existence; no software exists now to exploit this feature.

:link:

- [*IEEE 754*](https://en.wikipedia.org/wiki/IEEE_754) – Wikipedia
- R.Harris. [*You’re going to have to think!*](https://accu.org/journals/overload/18/99/harris_1702/) – [Overload **99**](https://accu.org/journals/overload/overload99) (2010)
- D.Goldberg. [*What every computer scientist should know about floating-point arithmetic*](https://www.itu.dk/~sestoft/bachelor/IEEE754_article.pdf) (1991)

:grey_question:

- [*How many unique values are there between 0 and 1 of a standard float?*](https://stackoverflow.com/q/17949796) – Stack Overflow
- [*Why does IEEE 754 reserve so many NaN values?*](https://stackoverflow.com/q/19800415) – Stack Overflow
- [*How many normalized numbers can be represented using IEEE-754 single precision?*](https://stackoverflow.com/q/12558780) – Stack Overflow

:page_facing_up:

- W.Kahan. [*Lecture notes on the status of IEEE standard 754 for binary floating-point arithmetic*](https://people.eecs.berkeley.edu/~wkahan/ieee754status/IEEE754.PDF) (1997)
- C.Allison. [*Where did all my decimals go?*](http://uvu.freshsources.com/decimals.pdf) (2006)

:book:

- M.L.Overton. [*Numerical computing with IEEE floating point arithmetic*](https://doi.org/10.1137/1.9780898718072) – SIAM (2001)
- Sec. 2.5: *Floating-point arithmetic* – D.H.Eberly. [*GPGPU
programming for games and science*](https://www.crcpress.com/GPGPU-Programming-for-Games-and-Science/Eberly/p/book/9781466595354) – CRC Press (2014)
- C.Allison. [*Floating-point numbers aren’t real*](http://freshsources.com/FPNotReal.pdf) – K.Henney. [*97 things every programmer should know*](https://www.oreilly.com/library/view/97-things-every/9780596809515/) (2010)

:movie_camera:

- J.Farrier. [*Demystifying floating point*](https://www.youtube.com/watch?v=k12BJGSc2Nc) – CppCon (2015)
- J.Gustafson. [*Beating floats at their own game*](https://www.youtube.com/watch?v=N05yYbUZMSQ) – HPC Advisory Council Australia Conference (2017)

#### Denormal numbers

:link:

- [*Denormal number*](https://en.wikipedia.org/wiki/Denormal_number) – Wikipedia
- C.Moler. [*Floating point denormals, insignificant but controversial*](https://blogs.mathworks.com/cleve/2014/07/21/floating-point-denormals-insignificant-but-controversial-2/) (2014)

:movie_camera:

- D.Kohlbrenner. [*On subnormal floating point and abnormal timing*](https://www.youtube.com/watch?v=DftejgRgmc8) – IEEE Symposium on Security and Privacy (2015)

#### NaNs

:link:

- [*What is the rationale for all comparisons returning false for IEEE754 NaN values?*](https://stackoverflow.com/q/1565164) – Stack Overflow

### Applications

:link:

- M.Rayman. [*How many decimals of &pi; do we really need?*](https://www.jpl.nasa.gov/edu/news/2016/3/16/how-many-decimals-of-pi-do-we-really-need/) – NASA (2016)

---

## Arithmetic algorithms

:link:

- T.Prince. [*Tuning up math functions*](https://eugnsp.github.io/CUJ/10.12/prince/prince.md) – C/C++ Users Journal **10** (1992)

### Arithmetic means

> To compute the arithmetic mean <code>&mu; = 1 / N &sum; x<sub>i</sub></code> in a numerically stable way, the following recurrence relation can be used: <code>&mu;<sub>N</sub> = &mu;<sub>N - 1</sub> + 1 / N (x<sub>N</sub> - &mu;<sub>N - 1</sub>)</code>.

:link:

- D.Assencio. [*Numerically stable computation of arithmetic means*](https://diego.assencio.com/?index=c34d06f4f4de2375658ed41f70177d59) (2015)
- T.Finch. [*Incremental calculation of weighted mean and variance*](https://fanf2.user.srcf.net/hermes/doc/antiforgery/stats.pdf) (2009)

### Binomial coefficient

:link:

- M.Dominus. [*How to calculate binomial coefficients*](https://blog.plover.com/math/choose.html)
- M.Dominus. [*How to calculate binomial coefficients, again*](https://blog.plover.com/math/choose-2.html)

### Division algorithms

<!-- https://en.wikipedia.org/wiki/Division_algorithm
https://web.stanford.edu/class/ee486/doc/chap5.pdf -->

#### Integer division

:link:

- I.Kaplan. [*Integer division*](http://bearcave.com/software/divide.htm) (1996)

### Horner’s method

> Horner’s method is a polynomial evaluation method expressed by <code>p(x) = a<sub>0</sub> + a<sub>1</sub> x + a<sub>2</sub> x<sup>2</sup> + ... + a<sub>N</sub> x<sup>N</sup> = a<sub>0</sub> + x (a<sub>1</sub> + x (a<sub>2</sub> + ... + x (a<sub>N</sub>) ... ))</code>.

:link:

- [Horner’s method](https://en.wikipedia.org/wiki/Horner%27s_method) – Wikipedia

### Kahan summation algorithm

:link:

- [*Kahan summation algorithm*](https://en.wikipedia.org/wiki/Kahan_summation_algorithm) – Wikipedia

:grey_question:

- [*Kahan summation*](https://stackoverflow.com/q/4940072) – Stack Overflow

### Powers and logarithms

:link:

- [*How to check if an integer is a power of `3`?*](https://stackoverflow.com/q/1804311) – Stack Overflow

#### Square root

:link:

- [*Methods of computing square roots*](https://en.wikipedia.org/wiki/Methods_of_computing_square_roots) – Wikipedia
- P.Martin. [*Eight rooty pieces*](https://accu.org/journals/overload/24/135/martin_2294/) – [Overload **135**](https://accu.org/journals/overload/overload135) (2016)

#### Inverse square root

- [*Fast inverse square root*](https://en.wikipedia.org/wiki/Fast_inverse_square_root) – Wikipedia
- C.Lomont. [*Fast inverse square root*](http://www.lomont.org/papers/2003/InvSqrt.pdf) (2003)

<!-- https://web.archive.org/web/20030426190503/http://www.magic-software.com/Documentation/FastInverseSqrt.pdf
https://www.beyond3d.com/content/articles/8/
David Eberly, Fast inverse square root (revisited), 2010.
http://www.azillionmonkeys.com/qed/sqroot.html
 -->

---

## Prime numbers

:grey_question:

- [*How many prime numbers are there (available for RSA encryption)?*](https://stackoverflow.com/q/16091581) – Stack Overflow

---

## Linear equations solution algorithms

### Iterative methods

:link:

- G.Strang. [*Iterative methods*](https://ocw.mit.edu/courses/mathematics/18-086-mathematical-methods-for-engineers-ii-spring-2006/readings/am62.pdf) (2006)

:book:

- Sec. 20.5: *Relaxation methods for boundary value problems* – W.H.Press et al. [*Numerical recipes: The art of scientific computing*](http://numerical.recipes/) (2007)

#### Jacobi method

> A recurrence relation: <code>x<sub>K+1</sub> = D<sup>-1</sup> (D - A) x<sub>K</sub> + D<sup>-1</sup> b</code>, where the preconditioner `D` is the diagonal part of `A`: `D = diag(A)`.

:link:

- [*Jacobi method*](https://en.wikipedia.org/wiki/Jacobi_method) – Wikipedia
- [*Jacobi method*](http://mathworld.wolfram.com/JacobiMethod.html) – Wolfram MathWorld

:movie_camera:

- G.Strang. [*Iterative methods and preconditioners*](https://www.youtube.com/watch?v=LtNVodIs1dI) – MIT 18.086 [*Mathematical methods for engineers II*](https://ocw.mit.edu/courses/mathematics/18-086-mathematical-methods-for-engineers-ii-spring-2006/) (2006)

---

## Matrix diagonalization

### Jacobi eigenvalue algorithm

:link:

- [*Jacobi eigenvalue algorithm*](https://en.wikipedia.org/wiki/Jacobi_eigenvalue_algorithm) – Wikipedia
- J.Lambers. [*Jacobi methods*](https://web.stanford.edu/class/cme335/lecture7.pdf) – CME 335 (2010)

:book:

- Sec. 11.1: *Jacobi transformations of a symmetric matrix* – W.H.Press et al. [*Numerical recipes: The art of scientific computing*](http://numerical.recipes/) (2007)
- Sec. 8.5: *Jacobi methods* – G.H.Golub, C.F.Van Loan. [*Matrix computations*](https://my.siam.org/Store/Product/viewproduct/?ProductId=23915573) – SIAM (2013)
- H.Rutishause. Contrib. II/1: *The Jacobi method for real symmetric matrices* – J.H.Wilkinson, C.Reinsch. [*Handbook for automatic computation. Vol. II: Linear algebra*](https://www.springer.com/gp/book/9783642869426) (1971)

---

## Wavelets

:movie_camera:

- G.Strang. [*Multiresolution, wavelet transform and scaling function*](https://www.youtube.com/watch?v=LtNVodIs1dI) – MIT 18.085 *Computational science and engineering I* (2008?)
- G.Strang. [*Splines and orthogonal wavelets: Daubechies construction*](https://www.youtube.com/watch?v=LeafEHx9d0c) – MIT 18.085 *Computational science and engineering I* (2008?)

:book:

- Sec. 11.1: *Jacobi transformations of a symmetric matrix* – W.H.Press et al. [*Numerical recipes: The art of scientific computing*](http://numerical.recipes/) (2007)

<!--
https://www.math.wustl.edu/~wick/teaching/Math2605Notes/chap3.pdf

https://www.maths.tcd.ie/~dbennett/js/ising.pdf
-->

---

## Applications

### Finite elements and finite volume methods

:movie_camera:

- D.Arnold. [*The fundamental theorem of numerical analysis*](https://www.youtube.com/watch?v=mmIrLgCFFhM) – Annual conference of the Great Lakes section of the SIAM (2015)
- P.Roe. [*Colorful fluid dynamics: Behind the scenes*](https://www.youtube.com/watch?v=uaH91P665PI) – AE585 Seminar lecture series (2014)

### Spacecrafts dynamics

:movie_camera:

- J.Arrieta. [*Traveling the Solar system with C++: Programming rocket science*](https://www.youtube.com/watch?v=YXs3DFrZZL4) – CppCon (2017)
