# Type traits
## The best type traits that C++ doesn't have

*Arthur O'Dwyer* @ C++Now (2018)

> I'll present three candidates for the best type trait that doesn't (yet!) exist in C++. The first trait, `is_trivially_relocatable_v<T>`, tells whether objects of type `T` can be "atomically move-constructed-and-destroyed" by `std::memcpy`. The canonical use-cases for this operation are vector resizing and hash-table rehashing. We'll look at benchmarks for resizing `std::vector<std::unique_ptr<T>>` with and without this type trait, and consider the curious case of **swapping** two trivially relocatable objects. The second trait, `is_trivially_equality_comparable_v<T>`, tells whether objects of type `T` can be compared by `std::memcmp`. The canonical use-case for this operation is compare-exchange on `std::atomic<T>`, which is already implemented in terms of `std::memcmp` but has undefined behavior for types that are not trivially comparable. (WG21 has begun to tackle this problem via papers N4130 and P0528.) With the introduction of "operator spaceship" in C++2a, the compiler now has enough information to determine the trivial comparability of every user-defined type; this could be exposed as a built-in type trait. We'll look at benchmarks for `std::vector<std::unique_ptr<T>>::operator==` with and without this type trait, and give a nod to `is_trivially_less_than_comparable_v<T>`. The third trait is actually a traits class: `tombstone_traits<T>`. This part of the talk will build on Mark Zeren's C++Now 2017 session "Rethinking Strings". Most object types have invalid or "spare" representations, for example the all-bits-zero representation of a `std::reference_wrapper<U>` or the `0x02` representation of a `bool`. By opting into a specialization of `tombstone_traits<T>`, the programmer can make these "spare" representations available to tombstone-aware library classes such as `std::optional<T>` and `cuckoo_hash<T>`. We'll show how `tombstone_traits<bool>` exposes the spare representations, how `tombstone_traits<std::optional<T>>` propagates them appropriately, and how the tombstone representations can be used in practice by a Robin Hood hash table.

[Watch at YouTube](https://www.youtube.com/watch?v=MWBfmmg8-Yo)

[See more details](https://cppnow2018.sched.com/event/ae35e6b500090e00c295aeeef68762c0)

## Type traits: what are they and why should I use them?

*Marshall Clow* @ CppCon (2015)

> In this talk, I will answer the questions, "What are type traits?" and "Why are type traits useful?", along with some examples of why when when they should be used.

[Watch at YouTube](https://www.youtube.com/watch?v=VvbTP_k_Df4)

[See more details](https://cppcon2015.sched.com/event/3vci/type-traits-what-are-they-and-why-should-i-use-them)

