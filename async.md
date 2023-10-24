
## Stackless vs Stackfull coroutines

[Project Loom: Fibers and Continuations for the Java Virtual Machine](https://cr.openjdk.org/~rpressler/loom/Loom-Proposal.html)

[Fibers under the magnifying glass](https://www.open-std.org/JTC1/SC22/WG21/docs/papers/2018/p1364r0.pdf)

## IO Multiplexing - Non-blocking IO

[Chapter 6. I/O Multiplexing: The select and poll Functions](https://notes.shichao.io/unp/ch6/)

>Nonblocking I/O Model
>
>When a socket is set to be nonblocking, we are telling the kernel "when an I/O operation that I request cannot be completed without putting the process to sleep, do not put the process to sleep, but return an error instead".

## glibc aio

https://github.com/bminor/glibc/blob/master/rt/aio_misc.c#L307

# Async Rust

## How to wait for a list of async function calls in Rust?

From: https://stackoverflow.com/a/63327675

The futures crate has a `join_all` function which allows for waiting on a collection of futures:

```rust
use futures::future::join_all;

async fn start_consumers(&self) {
    let mut v = Vec::new();
    for consumer in &self.consumers {
        v.push(consumer.consume());
    }
    join_all(v).await;
 }
```

## join! executing Futures concurrently

From: https://rust-lang.github.io/async-book/06_multiple_futures/02_join.html

>The futures::join macro makes it possible to wait for multiple different futures to complete while executing them all concurrently.


```rust
use futures::{executor, join};

#[derive(Debug)]
struct Music {
	title: String,
}

#[derive(Debug)]
struct Book {
	name: String,
}

async fn get_book() -> Book {
	Book {
		name: "Rust".into(),
	}
}

async fn get_music() -> Music {
	Music {
		title: "Nice".into(),
	}
}

async fn get_book_and_music() -> (Book, Music) {
    let book_fut = get_book();
    let music_fut = get_music();
    join!(book_fut, music_fut)
}


fn main() {
	let book_music_fut = async {
		let (book, music) = get_book_and_music().await;
		println!("{:?}", book);
		println!("{:?}", music);
		(book, music)
	};

	let (book, music) = executor::block_on(book_music_fut);
	dbg!(book, music);
}
```

`cargo expand`

```rust
#![feature(prelude_import)]
#[prelude_import]
use std::prelude::rust_2021::*;
#[macro_use]
extern crate std;
use futures::{executor, join};
struct Music {
    title: String,
}
#[automatically_derived]
impl ::core::fmt::Debug for Music {
    fn fmt(&self, f: &mut ::core::fmt::Formatter) -> ::core::fmt::Result {
        ::core::fmt::Formatter::debug_struct_field1_finish(
            f,
            "Music",
            "title",
            &&self.title,
        )
    }
}
struct Book {
    name: String,
}
#[automatically_derived]
impl ::core::fmt::Debug for Book {
    fn fmt(&self, f: &mut ::core::fmt::Formatter) -> ::core::fmt::Result {
        ::core::fmt::Formatter::debug_struct_field1_finish(
            f,
            "Book",
            "name",
            &&self.name,
        )
    }
}
async fn get_book() -> Book {
    Book { name: "Rust".into() }
}
async fn get_music() -> Music {
    Music { title: "Nice".into() }
}
async fn get_book_and_music() -> (Book, Music) {
    let book_fut = get_book();
    let music_fut = get_music();
    {
        use ::futures_util::__private as __futures_crate;
        {
            let mut _fut0 = __futures_crate::future::maybe_done(book_fut);
            let mut _fut0 = unsafe { __futures_crate::Pin::new_unchecked(&mut _fut0) };
            let mut _fut1 = __futures_crate::future::maybe_done(music_fut);
            let mut _fut1 = unsafe { __futures_crate::Pin::new_unchecked(&mut _fut1) };
            __futures_crate::future::poll_fn(move |
                    __cx: &mut __futures_crate::task::Context<'_>|
                {
                    let mut __all_done = true;
                    __all_done
                        &= __futures_crate::future::Future::poll(_fut0.as_mut(), __cx)
                            .is_ready();
                    __all_done
                        &= __futures_crate::future::Future::poll(_fut1.as_mut(), __cx)
                            .is_ready();
                    if __all_done {
                        __futures_crate::task::Poll::Ready((
                            _fut0.as_mut().take_output().unwrap(),
                            _fut1.as_mut().take_output().unwrap(),
                        ))
                    } else {
                        __futures_crate::task::Poll::Pending
                    }
                })
                .await
        }
    }
}
fn main() {
    let book_music_fut = async {
        let (book, music) = get_book_and_music().await;
        {
            ::std::io::_print(format_args!("{0:?}\n", book));
        };
        {
            ::std::io::_print(format_args!("{0:?}\n", music));
        };
        (book, music)
    };
    let (book, music) = executor::block_on(book_music_fut);
    (
        match book {
            tmp => {
                {
                    ::std::io::_eprint(
                        format_args!(
                            "[{0}:{1}] {2} = {3:#?}\n",
                            "src/main.rs",
                            41u32,
                            "book",
                            &tmp,
                        ),
                    );
                };
                tmp
            }
        },
        match music {
            tmp => {
                {
                    ::std::io::_eprint(
                        format_args!(
                            "[{0}:{1}] {2} = {3:#?}\n",
                            "src/main.rs",
                            41u32,
                            "music",
                            &tmp,
                        ),
                    );
                };
                tmp
            }
        },
    );
}
```
