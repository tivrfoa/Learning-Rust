


# Why do so few languages have this type of coroutine feature?

https://langdev.stackexchange.com/questions/2468/why-do-so-few-languages-have-this-type-of-coroutine-feature

## From: https://langdev.stackexchange.com/a/2469/2807


### It might be a library feature instead of a language feature

In some languages it might be feasible to implement coroutines as a library, without needing any support from the language itself. For example, there are coroutine libraries for C and C++ (Boost::Coroutine existed long before C++20 introduced coroutines as a language feature).

### Coroutines are complicated

A generator is a very limited form of a coroutine. If a general-purpose language wants to implement coroutines, it probably wants to support a wider range of applications than just generators. However, there are lots of things to worry about then: how do you schedule coroutines, do you have stackful or stackless coroutines, how should it integrate with the existing language features, and so on. It could be that some languages decided that it's better to wait before committing to a specific implementation which might later turn out to be a bad decision.

But once you have generic coroutines in your language, then it's rather easy to have generators as well. In fact, that's the very first type of coroutine that will be supported in the C++ standard library (C++23's std::generator).

### Composing generators

You already pointed out that there is a difference in how generators compose between Python and SuperCollider. That's another thing you have to worry about when impementing this as a language feature. Do yields cross coroutine function boundaries or not?

Not automatically passing yields means that each coroutine function has more control over what happens. It can then decide whether or not to pass a yielded value on to the parent. For exampe, in Python you would just write:

```python
def countDownFrom(n):
    for x in range(n, 0, -1):
        yield x

def myRoutine():
    for x in countDownFrom(10):
        yield x

    # Or shorter:
    # yield from countDownFrom(10)

    yield "I've run out of x's!"

for x in myRoutine():
    print(x)
```

This is a bit more verbose. On the other hand, you probably need something more verbose in SuperCollider if you wanted the results of the call to ~countDownFrom.(10) to not be passed to the caller?
It's not an issue of compiled vs. interpreted

    Is it because the language really has to be interpreted in order for this to work? Would there be impassible barriers that would prevent it from being implemented in a strongly typed, compiled language?

There is no reason why this couldn't work in a strongly typed, compiled language. Even your example that can return either an integer or a string from myRoutine() could be written in C++, if you appease the type system:

```cpp
std::generator<int> countDownFrom(int n) {
    while (n > 0)
        co_yield n--;
}

std::generator<std::variant<int, std::string>> myRoutine() {
    for (auto x: countDownFrom(10))
        co_yield x;

    co_yield "I've run out of x's!";
}

for (auto x: myRoutine())
    std::visit([](auto x){ std::print("{}\n", x); }, x);
```



# growing fibers

https://wingolog.org/archives/2017/06/27/growing-fibers


# Evolution of the x86 context switch in Linux

https://www.maizure.org/projects/evolution_x86_context_switch_linux/

