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

:book:

- Ch. 3: *Linked lists* – Drozdek A. *Data structures and algorithms in C++* – Cengage Learning (2012)

---

## Singly linked lists

> A singly linked list contains nodes which have a data field, and `next` field, which points to the next node in the list.

:book:

- Sec. 3.1: *Singly linked lists* – Drozdek A. *Data structures and algorithms in C++* – Cengage Learning (2012)

:page_facing_up:

- Z.Shao, J.H.Reppy, A.W.Appel. [*Unrolling lists*](http://flint.cs.yale.edu/flint/publications/listrep.ps.gz) – [ACM conference on LISP and functional programming, 185](https://doi.org/10.1145/182409.182453) (1994)

:anchor:

- [*`std::forward_list`*](https://en.cppreference.com/w/cpp/container/forward_list) – C++ reference

---

## Doubly linked lists

> A doubly linked list contains nodes which have a data field, and `next` and `prev` fields, which point to the next and to the previous nodes in the list, respectively.

:link:

- [*Doubly linked list*](https://en.wikipedia.org/wiki/Doubly_linked_list) – Wikipedia

:book:

- Sec. 3.2: *Doubly linked lists* – Drozdek A. *Data structures and algorithms in C++* – Cengage Learning (2012)

:anchor:

- [*`std::list`*](https://en.cppreference.com/w/cpp/container/list) – C++ reference

### XOR doubly linked lists

:memo:

- If garbage collection is enabled, XOR linked list needs to declare its nodes reachable. For C++, see [`std::declare_reachable`](https://en.cppreference.com/w/cpp/memory/gc/declare_reachable) – C++ reference.

:link:

- [*XOR linked list*](https://en.wikipedia.org/wiki/XOR_linked_list) – Wikipedia
- P.Sinha. [*A memory-efficient doubly linked list*](https://www.linuxjournal.com/article/6828) – Linux Journal

### Circular lists

- Sec. 3.3: *Circular lists* – Drozdek A. *Data structures and algorithms in C++* – Cengage Learning (2012)

---

## Skip lists

See [*Skip lists* – Randomized algorithms and probabilistic data structures](random.md#skip-lists)
