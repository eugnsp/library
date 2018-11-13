# Allocators
### An allocator is a handle to a heap

*Arthur O'Dwyer* @ C++Now (2018)

> C++17 introduced the `std::pmr` framework. In this framework, a `std::pmr::polymorphic_allocator<T>` holds a pointer to a `std::pmr::memory_resource`. The memory resource is in charge of managing and organizing the heap itself, and the allocator object is just a thin "handle" pointing to the memory resource. This is not just a convenient implementation strategy for `std::pmr`! Rather, this elucidates the true meaning of the Allocator concept which has existed, unchanged, since C++98. An Allocator <b>is</b> a handle to a MemoryResource. Even `std::allocator` can &ndash; and should &ndash; be viewed as a handle to a global singleton "heap", and not as a MemoryResource in its own right. From this core insight we derive many corollaries, such as the need for allocator types to be lightweight and efficiently copyable, the fundamental impossibility of implementing an "in-place" `std::vector` via stupid allocator tricks, and the philosophical underpinnings of "rebinding." We'll show at least two non-standard examples of types modeling Allocator that act as different kinds of handles to heaps: a `shmem_allocator` that holds a `shmem_ptr` to a memory resource, and a `shutdown_safe_allocator` that holds a `weak_ptr` to a memory resource. We'll discuss what we can expect from a "moved-from" allocator object, relate the notion of "handle" to neighboring notions such as "fa&ccedil;ade" and "adaptor", and suggest similarities between "allocator/heap" and "executor/execution-context".

<a href="http://www.youtube.com/watch?feature=player_embedded&v=0MdSJsCTRkY" target="_blank"><img src="http://img.youtube.com/vi/0MdSJsCTRkY/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> 

[Source / Details](https://cppnow2018.sched.com/event/767e288589eae513fb3afff01fbca567)

# Containers
### If I had my 'druthers: a proposal for improving the containers in C++2x

*Bob Steagall* @ C++Now (2018)

> This talk will first review weaknesses in the current container library and discuss corresponding opportunities for improvement. We'll then list some tentative requirements, distinguishing between the needs of ordinary users and power users. We'll cover the need for meaningful names, and emphasize the distinction between low-level concrete containers, such as linked lists, and high-level adaptor containers, such as stacks. We'll then present a proposed high-level design for the container library and an idiom for container implementation that fulfills those requirements. We'll also cover changes to allocators and memory management facilities needed to support the proposed design. Along the way we'll look at example code for implementation and usage, and discuss ways to improve the containers' public APIs.


<a href="http://www.youtube.com/watch?feature=player_embedded&v=bAE0qteS4Rk" target="_blank"><img src="http://img.youtube.com/vi/bAE0qteS4Rk/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> 

[Source / Details](https://cppnow2018.sched.com/event/ec102c7cabeea1c91c5629bd6d926ca4)

# Utilities
### Initializer lists are broken, let's fix them

*Jason Turner* @ C++Now (2018)

> C++11's `std::initializer_list` objects are flawed in ways that prevent them from being used in some contexts and used efficiently in other contexts. They allow you to create dangling references that most compilers and static analysis tools are unable to track. Specific examples, benchmarks, and quotes from the standard will illustrate these problems and how they are mandated. Will it be possible to address these issues with library changes or do we need to make a change to the standard? We will attempt to come to a consensus as a group. 

<a href="http://www.youtube.com/watch?feature=player_embedded&v=sSlmmZMFsXQ" target="_blank"><img src="http://img.youtube.com/vi/sSlmmZMFsXQ/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> 

[Source / Details](https://cppnow2018.sched.com/event/4058f00b8431f1610d3246f62066ac51)

### `tuple<>`: What's new and how it works

*Stephan T. Lavavej* @ CppCon (2016)

> `std::tuple` has been gaining new abilities, like get-by-type in C++14 and conditionally-explicit constructors in C++17. This talk will begin by briefly summarizing what you can do with tuples in C++11 and C++14. Next, we'll explore what's new in C++17, and how it can improve your code. We'll also delve into how this magic is implemented, with new metaprogramming tools like `std::conjunction`. Finally, we'll look at active issues in tuple's design, and what the Library Working Group is doing about them.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=JhgWFYfdIho" target="_blank"><img src="http://img.youtube.com/vi/JhgWFYfdIho/0.jpg" alt="Watch at YouTube" width="240" height="180"></a> 

[Source / Details](https://cppcon2016.sched.com/event/7nLk/tupleltgt-whats-new-and-how-it-works)

<sub>*(Note: this file was generated automatically)*</sub>