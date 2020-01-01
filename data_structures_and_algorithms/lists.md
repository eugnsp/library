# Lists <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [General information](#general-information)
- [Singly linked lists](#singly-linked-lists)
- [Doubly linked lists](#doubly-linked-lists)
	- [XOR doubly linked lists](#xor-doubly-linked-lists)
- [Skip lists](#skip-lists)

---

## General information

:link:

- [*Linked list*](https://en.wikipedia.org/wiki/Linked_list) – Wikipedia
- B.Stroustrup. [*Are lists evil?*](http://www.stroustrup.com/bs_faq.html#list) – B.Stroustrup’s FAQ
- K.Hedstr&ouml;m. [*Number crunching: Why you should never, ever, **ever** use linked-list in your code again*](https://kjellkod.wordpress.com/2012/02/25/why-you-should-never-ever-ever-use-linked-list-in-your-code-again/) (2012)

:movie_camera:

- B.Stroustrup. [*Why you should avoid linked lists*](https://www.youtube.com/watch?v=YQs6IC-vgmo) – Going Native (2012)

---

## Singly linked lists

> A singly linked list contains nodes which have a data field, and `next` field, which points to the next node in the list.

:page_facing_up:

- Z.Shao, J.H.Reppy, A.W.Appel. [*Unrolling lists*](http://flint.cs.yale.edu/flint/publications/listrep.ps.gz) – [ACM conference on LISP and functional programming, 185](https://doi.org/10.1145/182409.182453) (1994)

---

## Doubly linked lists

> A doubly linked list contains nodes which have a data field, and `next` and `prev` fields, which point to the next and to the previous nodes in the list, respectively.

:link:

- [*Doubly linked list*](https://en.wikipedia.org/wiki/Doubly_linked_list) – Wikipedia

### XOR doubly linked lists

:memo:

- If garbage collection is enabled, XOR linked list needs to declare its nodes reachable. For C++, see [`std::declare_reachable`](https://en.cppreference.com/w/cpp/memory/gc/declare_reachable) – C++ reference.

:link:

- [*XOR linked list*](https://en.wikipedia.org/wiki/XOR_linked_list) – Wikipedia
- P.Sinha. [*A memory-efficient doubly linked list*](https://www.linuxjournal.com/article/6828) – Linux Journal

---

## Skip lists

:movie_camera:

- [*Randomization: Skip lists*](https://www.youtube.com/watch?v=2g9OSRKJuzM) – MIT OCW 6.046J/18.410J: [Design and analysis of algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/) (2015)

:page_facing_up:

- W.Pugh. [*A skip list cookbook*](http://cglab.ca/~morin/teaching/5408/refs/p90b.pdf) – Tech. Rep. UMIACS-TR-89-72.1 (1990)
