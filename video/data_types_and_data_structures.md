# Floating point types
### Beyond floating point: next generation computer arithmetic

*John L. Gustafson* @ Stanford Computer Systems Colloquium (2017)

> <details><summary>Description</summary>A new data type called a "posit" is designed for direct drop-in replacement for IEEE Standard 754 floats. Unlike unum arithmetic, posits do not require interval-type mathematics or variable size operands, and they round if an answer is inexact, much the way floats do. However, they provide compelling advantages over floats, including simpler hardware implementation that scales from as few as two-bit operands to thousands of bits. For any bit width, they have a larger dynamic range, higher accuracy, better closure under arithmetic operations, and simpler exception-handling. For example, posits never overflow to infinity or underflow to zero, and there is no "Not-a-Number" (NaN) value. Posits should take up less space to implement in silicon than an IEEE float of the same size. With fewer gate delays per operation as well as lower silicon footprint, the posit operations per second (POPS) supported by a chip can be significantly higher than the FLOPs using similar hardware resources. GPU accelerators, in particular, could do more arithmetic per watt and per dollar yet deliver superior answer quality. A series of comprehensive benchmarks compares how many decimals of accuracy can be produced for a set number of bits-per-value, using various number formats. Low-precision posits provide a better solution than "approximate computing" methods that try to tolerate decreases in answer quality. High-precision posits provide better answers (more correct decimals) than floats of the same size, suggesting that in some cases, a 32-bit posit may do a better job than a 64-bit float. In other words, posits beat floats at their own game. </details>

<a href="http://www.youtube.com/watch?feature=player_embedded&v=aP0Y1uAA-2Y" target="_blank"><img src="http://img.youtube.com/vi/aP0Y1uAA-2Y/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> 

[Source / Details](http://web.stanford.edu/class/ee380/Abstracts/170201.html)

### Demystifying floating point numbers

*John Farrier* @ CppCon (2015)

> <details><summary>Description</summary>Every day we develop software that relies on math while we often overlook the importance of understanding the implications of using our IEEE floats. From the often cited "floating point error" to unstable algorithms, this talk will explain the importance of floats, understanding their storage, the impact of the IEEE floats on math, and designing algorithms better. Finally, the talk will conclude with a quick case study of storing time for games and simulations.</details>

<a href="http://www.youtube.com/watch?feature=player_embedded&v=k12BJGSc2Nc" target="_blank"><img src="http://img.youtube.com/vi/k12BJGSc2Nc/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> 

[Source / Details](https://cppcon2015.sched.com/event/3vn4/demystifying-floating-point-numbers)

<sub>*(Note: this file was generated automatically)*</sub>