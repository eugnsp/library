# Dynamic programming
### Introduction to algorithms: dynamic programming

*Erik Demaine* @ MIT OCW 6.006 (2011)

> <b>I.</b> This lecture introduces dynamic programming, in which careful exhaustive search can be used to design polynomial-time algorithms. The Fibonacci and shortest paths problems are used to introduce guessing, memoization, and reusing solutions to subproblems. <b>II.</b> This lecture starts with a five-step process for dynamic programming, and then covers text justification and perfect-information blackjack. The lecture also describes how parent pointers are used to recover the solution. <b>III.</b> This lecture starts with how to define useful subproblems for strings or sequences, and then looks at parenthesization, edit distance, and the knapsack problem. The lecture ends with a brief discussion of pseudopolynomial time. <b>IV.</b> This lecture introduces a second type of guessing, in which more subproblems are created so that more features of the solution can be found. This type of guessing is illustrated with piano/guitar fingering and the Tetris and Super Mario Brothers games.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=OQ5jsbhAv_M" target="_blank"><img src="http://img.youtube.com/vi/OQ5jsbhAv_M/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> <a href="http://www.youtube.com/watch?feature=player_embedded&v=ENyox7kNKeY" target="_blank"><img src="http://img.youtube.com/vi/ENyox7kNKeY/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> <a href="http://www.youtube.com/watch?feature=player_embedded&v=ocZMDMZwhCY" target="_blank"><img src="http://img.youtube.com/vi/ocZMDMZwhCY/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> <a href="http://www.youtube.com/watch?feature=player_embedded&v=tp4_UXaVyx8" target="_blank"><img src="http://img.youtube.com/vi/tp4_UXaVyx8/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> 

[Source / Details](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

# Standard library algorithms
### STL algorithms: how to use them and how to write your own

*Marshall Clow* @ ACCU (2016)

> The STL contains a collection of containers, which everyone knows about, and a collection of algorithms, which are less well known. In this session, I will talk about the algorithms that are in the STL, how they are designed, and talk about writing your own algorithms that work in the same style as existing ones.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=3nXLxMYXgWs" target="_blank"><img src="http://img.youtube.com/vi/3nXLxMYXgWs/0.jpg" alt="Watch at YouTube" width="240" height="180"></a>

[Source / Details](https://accu.org/index.php/conferences/accu_conference_2016/accu2016_sessions#STL_Algorithms_%E2%80%93_How_to_Use_Them_and_How_to_Write_Your_Own)

# String algorithms
### Fast conversion from UTF-8 with C++, DFAs, and SSE intrinsics

*Bob Steagall* @ C++Now (2018)

> UTF-8 is taking on an increasingly important role in text processing. Many applications require the conversion of UTF-8 to UTF-16 or UTF-32, but typical conversion algorithms are sub-optimal. This talk will describe a fast, correct, DFA-based approach to UTF-8 conversion that requires only three simple lookup tables and a small amount of straightforward C++ code. We'll begin with a quick review UTF-8 and its relation to UTF-16 and UTF-32, as well as the concept of code units and code points. Next, we'll look at the layout of bits within a UTF-8 byte sequence, and from that, show a simple algorithm for converting from UTF-8 to UTF-32. Along the way will be a definition of overlong and invalid byte sequences. Following that will be a discussion of how to construct a DFA to perform the same operations as the simple algorithm. We'll then look at code for the DFA traversal underlying the basic conversion algorithm, and how to gain an additional performance boost by using SSE intrinsics. Finally, we'll compare the performance of this approach to several commonly-available implementations on Windows and Linux, and show how it's possible to do significantly faster conversions. 

<a href="http://www.youtube.com/watch?feature=player_embedded&v=h5oczBeib_M" target="_blank"><img src="http://img.youtube.com/vi/h5oczBeib_M/0.jpg" alt="Watch at YouTube" width="240" height="180"></a>

[Source / Details](https://cppnow2018.sched.com/event/EC6x/fast-conversion-from-utf-8-with-c-dfas-and-sse-intrinsics)

### Regular expressions in C++, present and future

*Tim Shen* @ CppCon (2016)

> Regular expressions are widely used in application development and data processing, yet it is challenging to design and implement a regular expression library that is expressive, efficient and safe. In this talk, Tim Shen, the current maintainer of libstdc++'s `<regex>`, will introduce the basics of implementing regular expressions in C++, the status of existing implementations, and what is expected from the standardization process. For the implementation, several data structures and algorithms will be introduced, with pros and cons listed; we will show how several popular implementations (Boost.Regex, Boost.Xpressive, `<regex>` from standard library implementations, RE2, etc) pick their algorithms. Several popular features/patterns that hurt performance will be explained, with a "safe" regex usage suggested. Finally a wishlist of features will be presented, in order to deliver a more efficient and usable regex library. 

<a href="http://www.youtube.com/watch?feature=player_embedded&v=N_rkHzhXueo" target="_blank"><img src="http://img.youtube.com/vi/N_rkHzhXueo/0.jpg" alt="Watch at YouTube" width="240" height="180"></a>

[Source / Details](https://cppcon2016.sched.com/event/7nDI/regular-expressions-in-c-present-and-future)

<sub>*(Note: this file was generated automatically)*</sub>