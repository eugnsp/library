# Interface design
## Modern C++ API design: from rvalue-references to type design

*Titus Winters* @ C++Now (2018)

> The old rules for C++API design are due for an update &mdash; we made ad hoc changes to design principles in the standard library, but haven't really written down the new ideas. Parameter passing and API design for free functions/member functions is due for a general update, particularly as a result of rvalue-references and reference qualification. How do we express "maybe move" APIs? When do we want reference-qualified overload sets? What does an rvalue-reference qualified non-overloaded method mean? How do we express call once semantics? This talk will focus on modern C++ design from small (choice of passing by value or reference) to large (regular types, reference types, move-only types, etc). We will also introduce a taxonomy of type properties as a means to discuss known-good type design families. 

[Watch at YouTube](https://www.youtube.com/watch?v=2UmDvg5xv1U)

[See more details](https://cppnow2018.sched.com/event/593e9796afdddded34505f1bc066a14e)

## Free your functions!

*Klaus Iglberger* @ CppCon (2017)

> You are devoted to minimize coupling and duplication? You are taking care to maximize cohesion, flexibility, extensibility, encapsulation, testability, and even performance in order to achieve the high goals of (object-oriented) programming? Awesome! But wait: You still favor member functions? Seriously? You have been deceived! You have been praying at the altar of false promises! Shed the shackles of Java philosophy! Free your functions! In this talk I will demonstrate why in C++ free functions should generally be preferred to member functions, and why free functions &mdash; not member functions! &mdash; provide you with all the aforementioned advantages you expect from object-oriented programming. Note, though, that this talk might fundamentally change your perception of C++ and object-oriented programming in general! 

[Watch at YouTube](https://www.youtube.com/watch?v=WLDT1lDOsb4)

[See more details](https://cppcon2017.sched.com/event/BgsL/free-your-functions)

