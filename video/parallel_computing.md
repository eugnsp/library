# GPU computing
## C++ on GPUs done right?

*Peter Steinbach* @ Meeting C++ (2015)

> *No description is available.*

[Watch at YouTube](https://www.youtube.com/watch?v=z43l_LaOqnM)

[See more details](https://github.com/psteinb/meetingcpp2015)

# Multi-core computing
## `atomic<>` Weapons

*Herb Sutter* @ C++ and Beyond (2012)

> **The facts.** The C++11 memory model and what it requires you to do to make sure your code is correct and stays correct. We'll include clear answers to several FAQs: "how do the compiler and hardware cooperate to remember how to respect these rules?", "what is a race condition?", and the ageless one-hand-clapping question "how is a race condition like a debugger?" **The tools.** The deep interrelationships and fundamental tradeoffs among mutexes, atomics, and fences/barriers. I'll try to convince you why standalone memory barriers are bad, and why barriers should always be associated with a specific load or store. **The unspeakables.** I'll grudgingly and reluctantly talk about the Thing I Said I'd Never Teach That Programmers Should Never Need To Now: relaxed atomics. Don't use them! If you can avoid it. But here's what you need to know, even though it would be nice if you didn't need to know it. *The rapidly-changing hardware reality.* How locks and atomics map to hardware instructions on ARM and x86/x64, and throw in POWER and Itanium for good measure &mdash; and I'll cover how and why the answers are actually different last year and this year, and how they will likely be different again a few years from now. We'll cover how the latest CPU and GPU hardware memory models are rapidly evolving, and how this directly affects C++ programmers.

Watch at YouTube: [Part I](https://www.youtube.com/watch?v=A8eCGOqgvH4) [Part II](https://www.youtube.com/watch?v=KeLBd2EJLOU) 

[See more details](https://channel9.msdn.com/Shows/Going+Deep/Cpp-and-Beyond-2012-Herb-Sutter-atomic-Weapons-1-of-2)

