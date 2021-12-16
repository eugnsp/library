# Parsers and compilers <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Parsers](#parsers)
	- [Bottom-up](#bottom-up)
		- [Shunting yard algorithm](#shunting-yard-algorithm)
	- [Parsing XML](#parsing-xml)
- [Compilers](#compilers)
	- [Introduction and overview](#introduction-and-overview)
	- [Optimizations](#optimizations)

---

## Parsers

### Bottom-up

#### Shunting yard algorithm

:link:

- [*Shunting-yard algorithm*](https://en.wikipedia.org/wiki/Shunting-yard_algorithm) – Wikipedia
- [*Shunting yard algorithm*](https://web.archive.org/web/20180807214703/http://wcipeg.com/wiki/Shunting_yard_algorithm) – PEGWiki
- T.Norvell. [*Parsing expressions by recursive descent*](https://www.engr.mun.ca/~theo/Misc/exp_parsing.htm#shunting_yard)
- N.Reed. [*The shunting-yard algorithm*](http://www.reedbeta.com/blog/the-shunting-yard-algorithm/) – N.Reed blog
- Z.Nasibov. [*Inside the mathematical expressions evaluator*](https://www.codeproject.com/Articles/21137/Inside-the-Mathematical-Expressions-Evaluator) – CodeProject
- B.Miller, D.Ranum. [*General infix-to-postfix conversion*](https://interactivepython.org/runestone/static/pythonds/BasicDS/InfixPrefixandPostfixExpressions.html#general-infix-to-postfix-conversion)

### Parsing XML

:link:

- A.Kapoulkine. [*Parsing XML at the speed of light*](https://www.aosabook.org/en/posa/parsing-xml-at-the-speed-of-light.html) – The Performance of Open Source Applications

---

## Compilers

See also [*Optimizations* – Hardware, optimization, and OS internals](../cpp/optimization_and_hardware.md#optimizations).

### Introduction and overview

:link:

- A.Balaam. [*How to write a programming language: Part 1, The lexer*](https://accu.org/journals/overload/26/145/balaam_2510/) – [Overload **145**](https://accu.org/journals/overload/overload145) (2018)
- A.Balaam. [*How to write a programming language: Part 2, The parser*](https://accu.org/journals/overload/26/146/balaam_2532/) – [Overload **146**](https://accu.org/journals/overload/overload146) (2018)
- A.Balaam. [*How to write a programming language: Part 3, The evaluator*](https://accu.org/journals/overload/26/147/balaam_2565/) – [Overload **147**](https://accu.org/journals/overload/overload147) (2018)

### Optimizations

See also

- G.Horv&aacute;th. [*Algorithms from a compiler developer’s toolbox*](https://www.youtube.com/watch?v=eeS1WP7FK-A) – C++Now (2021
