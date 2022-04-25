# Geometric algorithms <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Polygons](#polygons)
	- [Inscribed circle](#inscribed-circle)
- [Closest pair of points](#closest-pair-of-points)
- [Points generation](#points-generation)
	- [Random points generation](#random-points-generation)
		- [Random points in triangles](#random-points-in-triangles)
		- [Random points in polygons](#random-points-in-polygons)
- [Polyline algorithms](#polyline-algorithms)
	- [Ramer–Douglas–Peucker algorithm](#ramerdouglaspeucker-algorithm)
- [Drawing algorithms](#drawing-algorithms)
	- [Bresenham’s-type algorithms](#bresenhams-type-algorithms)
		- [Bresenham’s line algorithm](#bresenhams-line-algorithm)
		- [Bresenham’s circle algorithm](#bresenhams-circle-algorithm)

---

## Polygons

### Inscribed circle

:link:

- [*Confusion on Delaunay triangulation and largest inscribed circle*](https://stackoverflow.com/q/27872964) – Stack Overflow
- [*Largest circle inside a non-convex polygon*](https://stackoverflow.com/q/4279478) – Stack Overflow

---

## Closest pair of points

> Problem: in the given set of <code>n &geq; 2</code> points in a metric space, find a pair of points with the smallest distance between them.

:link:

- [*Closest pair of points*](https://en.wikipedia.org/wiki/Closest_pair_of_points_problem) – Wikipedia

:book:

- Sec. 33.4: *Finding the closest pair of points* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)

---

## Points generation

### Random points generation

:book:

- Sec. 1.5: G.Turk. *Generating random points in triangles* – A.S.Glassner. [*Graphics gems*](https://www.glassner.com/portfolio/graphics-gems/) (1990)

#### Random points in triangles

> Problem: given three points `A`, `B` and `C` that describe a triangle, pick a random point in it with uniform probability.

:grey_question:

- [*Uniform random point in triangle*](https://math.stackexchange.com/q/18686) – Mathematics

#### Random points in polygons

> Problem: given `N` points <code>A<sub>1</sub></code>, <code>A<sub>2</sub></code>, ..., <code>A<sub>N</sub></code> that describe a polygon, pick a random point in it with uniform probability.

:grey_question:

- [*How to get a random point on the interior of an irregular polygon?*](https://stackoverflow.com/q/19481514) – Stack Overflow

---

## Polyline algorithms

### Ramer–Douglas–Peucker algorithm

:link:

- [*Ramer–Douglas–Peucker algorithm*](https://en.wikipedia.org/wiki/Ramer%E2%80%93Douglas%E2%80%93Peucker_algorithm) – Wikipedia

---

## Drawing algorithms

### Bresenham’s-type algorithms

#### Bresenham’s line algorithm

:link:

- [*Bresenham’s line algorithm*](https://en.wikipedia.org/wiki/Bresenham%27s_line_algorithm) – Wikipedia

:page_facing_up:

- R.F.Sproull. [*Using program transformations to derive line-drawing algorithms*](http://public.callutheran.edu/~reinhart/CSC505/Week1/BresenhamLines.pdf) – [ACM Transactions on Graphics **1**, 259](https://doi.org/10.1145/357311.357312) (1982)

#### Bresenham’s circle algorithm

:link:

- [*Midpoint circle algorithm*](https://en.wikipedia.org/wiki/Midpoint_circle_algorithm) – Wikipedia
- J.Kennedy. [*A fast Bresenham type algorithm for drawing circles*](https://web.engr.oregonstate.edu/~sllu/bcircle.pdf)
