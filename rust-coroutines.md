
# Generators are dead, long live coroutines, generators are back

https://blog.rust-lang.org/inside-rust/2023/10/23/coroutines.html

https://www.reddit.com/r/rust/comments/17fnzet/generators_are_dead_long_live_coroutines/

https://github.com/rust-lang/rfcs/pull/3513

https://github.com/oli-obk/rfcs/blob/iter_fn/text/0000-gen-fn.md#prior-art

## https://news.ycombinator.com/item?id=37990180

From: empath-nirvana

new syntax:

```rust
fn foo() -> impl Iterator<Item = u32> { gen { yield 42; for x in 3..6 { yield x } } }
```
	
From: kibwen

>Note that generators are already implemented, and underpin the async state machine/stackless coroutine transformation as an implementation detail. However, there's still a few things to iron out before they can be stabilized, and I'm happy to see work there proceeding.
	
	
From: rstuart4133

>They are also what underpins the "may" crate https://crates.io/crates/may, a green thread library.
>
>"may" does the same job as async/await (eg, happily support thousands of network threads on one native thread), runs at about the speed as async/await https://www.techempower.com/benchmarks/#section=data-r21 but the code looks completely "normal" - so special no keywords are needed, and almost none of the usual Rust async/await complaints apply. "Almost" because one does apply: may introduces coloured code, just like async/await. (If it didn't, it would run slower than async/await.)
>
>Also, there is: https://github.com/rust-lang/rust/issues/111272 Translated: co-routines currently use malloc to allocate stacks, so if you overflow the stack you get the experience the C like joys of random memory corruption, with no warning. Why it's implemented like that is a bit of a mystery, given Linux and BSD offer ways to create fast "safe" stacks, and in fact this is the very mechanism used every native thread stack, including Rust's main stack: https://man7.org/linux/man-pages/man2/mmap.2.html (see: MAP_GROWSDOWN). Anyway, as may uses the stacks from co-routines it also suffers from this problem.
>
>Hopefully, this will now be fixed. Generator's are interesting, but somewhat esoteric. Event driven I/O is now main steam, and as Go demonstrates green threads are the least painful way to do it. 
