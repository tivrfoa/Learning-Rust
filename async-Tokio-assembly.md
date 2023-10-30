Assembly generated using https://godbolt.org/

  - rustc 1.73.0
  - edition 2021
  - tokio 1.19.2


```rust
// Type your code here, or load an example.
pub async fn square(num: i32) -> i32 {
    num * num
}

pub fn square0(num: i32) -> i32 {
    num * num
}

// If you use `main()`, declare it as `pub` to see it in the output:
#[tokio::main]
pub async fn main() {
    println!("{}", square(2).await);
}
```

```asm
<core::result::Result<T,F> as core::ops::try_trait::FromResidual<core::result::Result<core::convert::Infallible,E>>>::from_residual:
        mov     byte ptr [rsp - 1], 2
        mov     al, byte ptr [rsp - 1]
        ret

std::thread::local::LocalKey<T>::with:
        push    rax
        call    qword ptr [rip + std::thread::local::LocalKey<T>::try_with@GOTPCREL]
        mov     rdi, rax
        mov     rsi, rdx
        lea     rdx, [rip + .L__unnamed_1]
        mov     ecx, 70
        lea     r8, [rip + .L__unnamed_2]
        call    qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        pop     rcx
        ret

std::thread::local::LocalKey<T>::with:
        push    rax
        call    qword ptr [rip + std::thread::local::LocalKey<T>::try_with@GOTPCREL]
        lea     rsi, [rip + .L__unnamed_1]
        mov     edx, 70
        lea     rcx, [rip + .L__unnamed_2]
        movzx   edi, al
        call    qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        and     al, 1
        movzx   eax, al
        pop     rcx
        ret

std::thread::local::LocalKey<T>::with:
        push    rax
        call    qword ptr [rip + std::thread::local::LocalKey<T>::try_with@GOTPCREL]
        lea     rsi, [rip + .L__unnamed_1]
        mov     edx, 70
        lea     rcx, [rip + .L__unnamed_2]
        movzx   edi, al
        call    qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        pop     rcx
        ret

std::thread::local::LocalKey<T>::with:
        push    rax
        call    qword ptr [rip + std::thread::local::LocalKey<T>::try_with@GOTPCREL]
        movzx   edi, al
        and     edi, 1
        lea     rsi, [rip + .L__unnamed_1]
        lea     rcx, [rip + .L__unnamed_2]
        mov     rax, qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        mov     edx, 70
        call    rax
        pop     rax
        ret

std::thread::local::LocalKey<T>::with:
        push    rax
        call    qword ptr [rip + std::thread::local::LocalKey<T>::try_with@GOTPCREL]
        lea     rsi, [rip + .L__unnamed_1]
        mov     edx, 70
        lea     rcx, [rip + .L__unnamed_2]
        movzx   edi, al
        call    qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        and     al, 1
        movzx   eax, al
        pop     rcx
        ret

std::thread::local::LocalKey<T>::try_with:
        sub     rsp, 120
        mov     qword ptr [rsp + 8], rsi
        mov     byte ptr [rsp + 103], 1
        mov     rax, qword ptr [rdi]
        mov     qword ptr [rsp + 56], 0
        mov     rdi, qword ptr [rsp + 56]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB6_3
.LBB6_1:
        test    byte ptr [rsp + 103], 1
        jne     .LBB6_15
        jmp     .LBB6_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 104], rcx
        mov     dword ptr [rsp + 112], eax
        jmp     .LBB6_1
.LBB6_3:
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 48], rax
        mov     rdx, qword ptr [rsp + 48]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB6_5
        mov     qword ptr [rsp + 40], 0
        jmp     .LBB6_6
.LBB6_5:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 40], rax
.LBB6_6:
        mov     rdx, qword ptr [rsp + 40]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB6_8
        mov     rax, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB6_9
.LBB6_8:
        mov     qword ptr [rsp + 32], 0
.LBB6_9:
        mov     rdx, qword ptr [rsp + 32]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB6_11
        mov     rcx, qword ptr [rsp + 8]
        mov     rax, qword ptr [rsp + 32]
        mov     byte ptr [rsp + 103], 0
        mov     rdx, qword ptr [rcx + 16]
        mov     qword ptr [rsp + 80], rdx
        movups  xmm0, xmmword ptr [rcx]
        movaps  xmmword ptr [rsp + 64], xmm0
        mov     qword ptr [rsp + 88], rax
        mov     rsi, qword ptr [rsp + 88]
        mov     rax, qword ptr [rip + tokio::coop::with_budget::{{closure}}@GOTPCREL]
        lea     rdi, [rsp + 64]
        call    rax
        mov     byte ptr [rsp + 7], al
        jmp     .LBB6_12
.LBB6_11:
        mov     byte ptr [rsp + 31], 2
        jmp     .LBB6_13
.LBB6_12:
        mov     al, byte ptr [rsp + 7]
        and     al, 1
        mov     byte ptr [rsp + 31], al
.LBB6_13:
        mov     al, byte ptr [rsp + 31]
        add     rsp, 120
        ret
.LBB6_14:
        mov     rdi, qword ptr [rsp + 104]
        call    _Unwind_Resume@PLT
        ud2
.LBB6_15:
        jmp     .LBB6_14

std::thread::local::LocalKey<T>::try_with:
        sub     rsp, 120
        mov     qword ptr [rsp + 8], rsi
        mov     byte ptr [rsp + 103], 1
        mov     rax, qword ptr [rdi]
        mov     qword ptr [rsp + 56], 0
        mov     rdi, qword ptr [rsp + 56]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB7_3
.LBB7_1:
        test    byte ptr [rsp + 103], 1
        jne     .LBB7_15
        jmp     .LBB7_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 104], rcx
        mov     dword ptr [rsp + 112], eax
        jmp     .LBB7_1
.LBB7_3:
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 48], rax
        mov     rdx, qword ptr [rsp + 48]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB7_5
        mov     qword ptr [rsp + 40], 0
        jmp     .LBB7_6
.LBB7_5:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 40], rax
.LBB7_6:
        mov     rdx, qword ptr [rsp + 40]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB7_8
        mov     rax, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB7_9
.LBB7_8:
        mov     qword ptr [rsp + 32], 0
.LBB7_9:
        mov     rdx, qword ptr [rsp + 32]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB7_11
        mov     rcx, qword ptr [rsp + 8]
        mov     rax, qword ptr [rsp + 32]
        mov     byte ptr [rsp + 103], 0
        movups  xmm0, xmmword ptr [rcx]
        movaps  xmmword ptr [rsp + 64], xmm0
        mov     qword ptr [rsp + 88], rax
        mov     rsi, qword ptr [rsp + 88]
        mov     rax, qword ptr [rip + tokio::coop::with_budget::{{closure}}@GOTPCREL]
        lea     rdi, [rsp + 64]
        call    rax
        jmp     .LBB7_12
.LBB7_11:
        mov     rdi, qword ptr [rsp + 8]
        mov     byte ptr [rsp + 31], 1
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget<(),tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>::{{closure}}>@GOTPCREL]
        jmp     .LBB7_13
.LBB7_12:
        mov     byte ptr [rsp + 31], 0
.LBB7_13:
        mov     al, byte ptr [rsp + 31]
        and     al, 1
        movzx   eax, al
        add     rsp, 120
        ret
.LBB7_14:
        mov     rdi, qword ptr [rsp + 104]
        call    _Unwind_Resume@PLT
        ud2
.LBB7_15:
        mov     rdi, qword ptr [rsp + 8]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget<(),tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>::{{closure}}>@GOTPCREL]
        call    rax
        jmp     .LBB7_14
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2

std::thread::local::LocalKey<T>::try_with:
        sub     rsp, 104
        mov     qword ptr [rsp + 8], rsi
        mov     byte ptr [rsp + 87], 1
        mov     rax, qword ptr [rdi]
        mov     qword ptr [rsp + 64], 0
        mov     rdi, qword ptr [rsp + 64]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB8_3
.LBB8_1:
        test    byte ptr [rsp + 87], 1
        jne     .LBB8_15
        jmp     .LBB8_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 88], rcx
        mov     dword ptr [rsp + 96], eax
        jmp     .LBB8_1
.LBB8_3:
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 56], rax
        mov     rdx, qword ptr [rsp + 56]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB8_5
        mov     qword ptr [rsp + 48], 0
        jmp     .LBB8_6
.LBB8_5:
        mov     rax, qword ptr [rsp + 56]
        mov     qword ptr [rsp + 48], rax
.LBB8_6:
        mov     rdx, qword ptr [rsp + 48]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB8_8
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 40], rax
        jmp     .LBB8_9
.LBB8_8:
        mov     qword ptr [rsp + 40], 0
.LBB8_9:
        mov     rdx, qword ptr [rsp + 40]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB8_11
        mov     rdi, qword ptr [rsp + 8]
        mov     rax, qword ptr [rsp + 40]
        mov     byte ptr [rsp + 87], 0
        mov     qword ptr [rsp + 72], rax
        mov     rsi, qword ptr [rsp + 72]
        mov     rax, qword ptr [rip + tokio::macros::scoped_tls::ScopedKey<T>::set::{{closure}}@GOTPCREL]
        call    rax
        mov     qword ptr [rsp], rax
        jmp     .LBB8_12
.LBB8_11:
        mov     qword ptr [rsp + 24], 1
        jmp     .LBB8_13
.LBB8_12:
        mov     rax, qword ptr [rsp]
        mov     qword ptr [rsp + 32], rax
        mov     qword ptr [rsp + 24], 0
.LBB8_13:
        mov     rax, qword ptr [rsp + 24]
        mov     rdx, qword ptr [rsp + 32]
        add     rsp, 104
        ret
.LBB8_14:
        mov     rdi, qword ptr [rsp + 88]
        call    _Unwind_Resume@PLT
        ud2
.LBB8_15:
        jmp     .LBB8_14

std::thread::local::LocalKey<T>::try_with:
        sub     rsp, 120
        mov     qword ptr [rsp + 8], rsi
        mov     byte ptr [rsp + 103], 1
        mov     rax, qword ptr [rdi]
        mov     qword ptr [rsp + 56], 0
        mov     rdi, qword ptr [rsp + 56]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB9_3
.LBB9_1:
        test    byte ptr [rsp + 103], 1
        jne     .LBB9_15
        jmp     .LBB9_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 104], rcx
        mov     dword ptr [rsp + 112], eax
        jmp     .LBB9_1
.LBB9_3:
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 48], rax
        mov     rdx, qword ptr [rsp + 48]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB9_5
        mov     qword ptr [rsp + 40], 0
        jmp     .LBB9_6
.LBB9_5:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 40], rax
.LBB9_6:
        mov     rdx, qword ptr [rsp + 40]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB9_8
        mov     rax, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB9_9
.LBB9_8:
        mov     qword ptr [rsp + 32], 0
.LBB9_9:
        mov     rdx, qword ptr [rsp + 32]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB9_11
        mov     rcx, qword ptr [rsp + 8]
        mov     rax, qword ptr [rsp + 32]
        mov     byte ptr [rsp + 103], 0
        mov     rdx, qword ptr [rcx + 16]
        mov     qword ptr [rsp + 80], rdx
        movups  xmm0, xmmword ptr [rcx]
        movaps  xmmword ptr [rsp + 64], xmm0
        mov     qword ptr [rsp + 88], rax
        mov     rsi, qword ptr [rsp + 88]
        mov     rax, qword ptr [rip + tokio::coop::with_budget::{{closure}}@GOTPCREL]
        lea     rdi, [rsp + 64]
        call    rax
        mov     byte ptr [rsp + 7], al
        jmp     .LBB9_12
.LBB9_11:
        mov     byte ptr [rsp + 31], 2
        jmp     .LBB9_13
.LBB9_12:
        mov     al, byte ptr [rsp + 7]
        and     al, 1
        mov     byte ptr [rsp + 31], al
.LBB9_13:
        mov     al, byte ptr [rsp + 31]
        add     rsp, 120
        ret
.LBB9_14:
        mov     rdi, qword ptr [rsp + 104]
        call    _Unwind_Resume@PLT
        ud2
.LBB9_15:
        jmp     .LBB9_14

std::thread::local::LocalKey<T>::try_with:
        sub     rsp, 120
        mov     qword ptr [rsp + 8], rsi
        mov     byte ptr [rsp + 103], 1
        mov     rax, qword ptr [rdi]
        mov     qword ptr [rsp + 56], 0
        mov     rdi, qword ptr [rsp + 56]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB10_3
.LBB10_1:
        test    byte ptr [rsp + 103], 1
        jne     .LBB10_15
        jmp     .LBB10_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 104], rcx
        mov     dword ptr [rsp + 112], eax
        jmp     .LBB10_1
.LBB10_3:
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 48], rax
        mov     rdx, qword ptr [rsp + 48]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB10_5
        mov     qword ptr [rsp + 40], 0
        jmp     .LBB10_6
.LBB10_5:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 40], rax
.LBB10_6:
        mov     rdx, qword ptr [rsp + 40]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB10_8
        mov     rax, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB10_9
.LBB10_8:
        mov     qword ptr [rsp + 32], 0
.LBB10_9:
        mov     rdx, qword ptr [rsp + 32]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB10_11
        mov     rcx, qword ptr [rsp + 8]
        mov     rax, qword ptr [rsp + 32]
        mov     byte ptr [rsp + 103], 0
        mov     rdx, qword ptr [rcx + 16]
        mov     qword ptr [rsp + 80], rdx
        movups  xmm0, xmmword ptr [rcx]
        movaps  xmmword ptr [rsp + 64], xmm0
        mov     qword ptr [rsp + 88], rax
        mov     rsi, qword ptr [rsp + 88]
        mov     rax, qword ptr [rip + tokio::coop::with_budget::{{closure}}@GOTPCREL]
        lea     rdi, [rsp + 64]
        call    rax
        mov     byte ptr [rsp + 7], al
        jmp     .LBB10_12
.LBB10_11:
        mov     byte ptr [rsp + 31], 3
        jmp     .LBB10_13
.LBB10_12:
        mov     al, byte ptr [rsp + 7]
        mov     byte ptr [rsp + 31], al
.LBB10_13:
        mov     al, byte ptr [rsp + 31]
        add     rsp, 120
        ret
.LBB10_14:
        mov     rdi, qword ptr [rsp + 104]
        call    _Unwind_Resume@PLT
        ud2
.LBB10_15:
        jmp     .LBB10_14

<() as core::fmt::Debug>::fmt:
        push    rax
        mov     qword ptr [rsp], rsi
        mov     rax, rdi
        mov     rdi, qword ptr [rsp]
        lea     rsi, [rip + .L__unnamed_3]
        mov     edx, 2
        call    qword ptr [rip + core::fmt::Formatter::pad@GOTPCREL]
        and     al, 1
        movzx   eax, al
        pop     rcx
        ret

core::fmt::Arguments::new_v1:
        sub     rsp, 136
        mov     qword ptr [rsp], r8
        mov     qword ptr [rsp + 8], rcx
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 24], rsi
        mov     qword ptr [rsp + 32], rdi
        mov     qword ptr [rsp + 40], rdi
        cmp     rdx, r8
        jb      .LBB12_2
        mov     rax, qword ptr [rsp + 16]
        mov     rcx, qword ptr [rsp]
        add     rcx, 1
        cmp     rax, rcx
        seta    al
        and     al, 1
        mov     byte ptr [rsp + 55], al
        jmp     .LBB12_3
.LBB12_2:
        mov     byte ptr [rsp + 55], 1
.LBB12_3:
        test    byte ptr [rsp + 55], 1
        jne     .LBB12_5
        mov     rax, qword ptr [rsp + 40]
        mov     rcx, qword ptr [rsp + 32]
        mov     rdx, qword ptr [rsp]
        mov     rsi, qword ptr [rsp + 8]
        mov     rdi, qword ptr [rsp + 16]
        mov     r8, qword ptr [rsp + 24]
        mov     qword ptr [rsp + 104], 0
        mov     qword ptr [rcx], r8
        mov     qword ptr [rcx + 8], rdi
        mov     r8, qword ptr [rsp + 104]
        mov     rdi, qword ptr [rsp + 112]
        mov     qword ptr [rcx + 32], r8
        mov     qword ptr [rcx + 40], rdi
        mov     qword ptr [rcx + 16], rsi
        mov     qword ptr [rcx + 24], rdx
        add     rsp, 136
        ret
.LBB12_5:
        mov     qword ptr [rsp + 120], 0
        lea     rax, [rip + .L__unnamed_4]
        mov     qword ptr [rsp + 56], rax
        mov     qword ptr [rsp + 64], 1
        mov     rcx, qword ptr [rsp + 120]
        mov     rax, qword ptr [rsp + 128]
        mov     qword ptr [rsp + 88], rcx
        mov     qword ptr [rsp + 96], rax
        lea     rax, [rip + .L__unnamed_5]
        mov     qword ptr [rsp + 72], rax
        mov     qword ptr [rsp + 80], 0
        lea     rsi, [rip + .L__unnamed_6]
        mov     rax, qword ptr [rip + core::panicking::panic_fmt@GOTPCREL]
        lea     rdi, [rsp + 56]
        call    rax
        ud2

core::mem::forget:
        ret

core::ptr::drop_in_place<tokio::runtime::task::LocalNotified<alloc::sync::Arc<tokio::runtime::basic_scheduler::Shared>>>:
        push    rax
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::task::Task<alloc::sync::Arc<tokio::runtime::basic_scheduler::Shared>>>@GOTPCREL]
        pop     rax
        ret

core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>:
        push    rax
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::task::LocalNotified<alloc::sync::Arc<tokio::runtime::basic_scheduler::Shared>>>@GOTPCREL]
        pop     rax
        ret

core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::enter<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}},()>::{{closure}}>:
        push    rax
        add     rdi, 8
        call    qword ptr [rip + core::ptr::drop_in_place<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>@GOTPCREL]
        pop     rax
        ret

core::ptr::drop_in_place<tokio::coop::with_budget<(),tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>::{{closure}}>:
        push    rax
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>@GOTPCREL]
        pop     rax
        ret

core::ptr::drop_in_place<()>:
        ret

core::ptr::drop_in_place<tokio::runtime::basic_scheduler::Context::run_task<(),tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>::{{closure}}>:
        push    rax
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>@GOTPCREL]
        pop     rax
        ret

core::ptr::drop_in_place<std::thread::local::AccessError>:
        ret

core::ptr::drop_in_place<tokio::runtime::handle::EnterGuard>:
        push    rax
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::context::EnterGuard>@GOTPCREL]
        pop     rax
        ret

core::ptr::drop_in_place<core::option::Option<tokio::runtime::basic_scheduler::CoreGuard>>:
        push    rax
        mov     qword ptr [rsp], rdi
        mov     rdx, qword ptr [rdi]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB22_2
.LBB22_1:
        pop     rax
        ret
.LBB22_2:
        mov     rdi, qword ptr [rsp]
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard>@GOTPCREL]
        jmp     .LBB22_1

core::task::wake::Context::from_waker:
        mov     qword ptr [rsp - 8], rdi
        mov     rax, qword ptr [rsp - 8]
        ret

core::option::Option<T>::or_else:
        sub     rsp, 40
        mov     qword ptr [rsp + 8], rsi
        mov     qword ptr [rsp + 16], rdi
        mov     byte ptr [rsp + 39], 1
        mov     rdx, qword ptr [rsp + 16]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB24_2
        mov     rdi, qword ptr [rsp + 8]
        mov     byte ptr [rsp + 39], 0
        call    qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}@GOTPCREL]
        mov     qword ptr [rsp + 24], rax
        jmp     .LBB24_3
.LBB24_2:
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 24], rax
.LBB24_3:
        test    byte ptr [rsp + 39], 1
        jne     .LBB24_5
.LBB24_4:
        mov     rax, qword ptr [rsp + 24]
        add     rsp, 40
        ret
.LBB24_5:
        jmp     .LBB24_4

core::option::Option<T>::or_else:
        sub     rsp, 40
        mov     qword ptr [rsp + 8], rsi
        mov     qword ptr [rsp + 16], rdi
        mov     byte ptr [rsp + 39], 1
        mov     rdx, qword ptr [rsp + 16]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB25_2
        mov     rdi, qword ptr [rsp + 8]
        mov     byte ptr [rsp + 39], 0
        call    qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}@GOTPCREL]
        mov     qword ptr [rsp + 24], rax
        jmp     .LBB25_3
.LBB25_2:
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 24], rax
.LBB25_3:
        test    byte ptr [rsp + 39], 1
        jne     .LBB25_5
.LBB25_4:
        mov     rax, qword ptr [rsp + 24]
        add     rsp, 40
        ret
.LBB25_5:
        jmp     .LBB25_4

core::result::Result<T,E>::expect:
        sub     rsp, 56
        mov     qword ptr [rsp + 8], rcx
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 24], rsi
        mov     al, dil
        mov     byte ptr [rsp + 38], al
        xor     eax, eax
        mov     ecx, 1
        cmp     byte ptr [rsp + 38], 2
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB26_2
        mov     al, byte ptr [rsp + 38]
        and     al, 1
        movzx   eax, al
        add     rsp, 56
        ret
.LBB26_2:
        mov     r8, qword ptr [rsp + 8]
        mov     rsi, qword ptr [rsp + 16]
        mov     rdi, qword ptr [rsp + 24]
        lea     rcx, [rip + .L__unnamed_7]
        mov     rax, qword ptr [rip + core::result::unwrap_failed@GOTPCREL]
        lea     rdx, [rsp + 39]
        call    rax
        jmp     .LBB26_5
.LBB26_3:
        mov     rdi, qword ptr [rsp + 40]
        call    _Unwind_Resume@PLT
        ud2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 40], rcx
        mov     dword ptr [rsp + 48], eax
        jmp     .LBB26_3
.LBB26_5:
        ud2

core::result::Result<T,E>::expect:
        sub     rsp, 56
        mov     qword ptr [rsp + 8], rcx
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 24], rsi
        mov     al, dil
        mov     byte ptr [rsp + 38], al
        xor     eax, eax
        mov     ecx, 1
        cmp     byte ptr [rsp + 38], 2
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB27_2
        mov     al, byte ptr [rsp + 38]
        and     al, 1
        movzx   eax, al
        add     rsp, 56
        ret
.LBB27_2:
        mov     r8, qword ptr [rsp + 8]
        mov     rsi, qword ptr [rsp + 16]
        mov     rdi, qword ptr [rsp + 24]
        lea     rcx, [rip + .L__unnamed_8]
        mov     rax, qword ptr [rip + core::result::unwrap_failed@GOTPCREL]
        lea     rdx, [rsp + 39]
        call    rax
        jmp     .LBB27_5
.LBB27_3:
        mov     rdi, qword ptr [rsp + 40]
        call    _Unwind_Resume@PLT
        ud2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 40], rcx
        mov     dword ptr [rsp + 48], eax
        jmp     .LBB27_3
.LBB27_5:
        ud2

core::result::Result<T,E>::expect:
        sub     rsp, 56
        mov     qword ptr [rsp + 8], rcx
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 24], rsi
        mov     al, dil
        mov     byte ptr [rsp + 38], al
        xor     eax, eax
        mov     ecx, 1
        cmp     byte ptr [rsp + 38], 3
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB28_2
        mov     al, byte ptr [rsp + 38]
        add     rsp, 56
        ret
.LBB28_2:
        mov     r8, qword ptr [rsp + 8]
        mov     rsi, qword ptr [rsp + 16]
        mov     rdi, qword ptr [rsp + 24]
        lea     rcx, [rip + .L__unnamed_8]
        mov     rax, qword ptr [rip + core::result::unwrap_failed@GOTPCREL]
        lea     rdx, [rsp + 39]
        call    rax
        jmp     .LBB28_5
.LBB28_3:
        mov     rdi, qword ptr [rsp + 40]
        call    _Unwind_Resume@PLT
        ud2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 40], rcx
        mov     dword ptr [rsp + 48], eax
        jmp     .LBB28_3
.LBB28_5:
        ud2

core::result::Result<T,E>::expect:
        sub     rsp, 72
        mov     qword ptr [rsp], r8
        mov     qword ptr [rsp + 8], rcx
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 24], rsi
        mov     qword ptr [rsp + 32], rdi
        mov     qword ptr [rsp + 40], rdi
        xor     eax, eax
        mov     ecx, 1
        cmp     qword ptr [rsi], 2
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB29_2
        mov     rsi, qword ptr [rsp + 24]
        mov     rdi, qword ptr [rsp + 32]
        mov     edx, 96
        call    memcpy@PLT
        mov     rax, qword ptr [rsp + 40]
        add     rsp, 72
        ret
.LBB29_2:
        mov     r8, qword ptr [rsp]
        mov     rsi, qword ptr [rsp + 8]
        mov     rdi, qword ptr [rsp + 16]
        mov     rax, qword ptr [rsp + 24]
        mov     rax, qword ptr [rax + 8]
        mov     qword ptr [rsp + 48], rax
        lea     rcx, [rip + .L__unnamed_9]
        mov     rax, qword ptr [rip + core::result::unwrap_failed@GOTPCREL]
        lea     rdx, [rsp + 48]
        call    rax
        jmp     .LBB29_5
.LBB29_3:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<std::io::error::Error>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB29_7
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 56], rcx
        mov     dword ptr [rsp + 64], eax
        jmp     .LBB29_3
.LBB29_5:
        ud2
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB29_7:
        mov     rdi, qword ptr [rsp + 56]
        call    _Unwind_Resume@PLT
        ud2

<F as core::future::into_future::IntoFuture>::into_future:
        mov     qword ptr [rsp - 16], rdi
        mov     rax, qword ptr [rsp - 16]
        mov     qword ptr [rsp - 24], rax
        mov     rax, qword ptr [rsp - 24]
        mov     qword ptr [rsp - 8], rax
        mov     rax, qword ptr [rsp - 8]
        ret

tokio::coop::with_budget::{{closure}}:
        sub     rsp, 88
        mov     qword ptr [rsp + 16], rsi
        mov     rax, rdi
        mov     rdi, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 24], rax
        mov     qword ptr [rsp + 32], rdi
        mov     byte ptr [rsp + 71], 0
        mov     byte ptr [rsp + 71], 1
        mov     rax, qword ptr [rip + core::cell::Cell<T>::get@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 46], dl
        mov     byte ptr [rsp + 47], al
        jmp     .LBB31_3
.LBB31_1:
        test    byte ptr [rsp + 71], 1
        jne     .LBB31_11
        jmp     .LBB31_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB31_1
.LBB31_3:
        mov     rdi, qword ptr [rsp + 32]
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 46]
        mov     dl, byte ptr [rsp + 47]
        mov     byte ptr [rsp + 14], dl
        mov     byte ptr [rsp + 15], cl
        movzx   esi, byte ptr [rax + 16]
        movzx   edx, byte ptr [rax + 17]
        mov     rax, qword ptr [rip + core::cell::Cell<T>::set@GOTPCREL]
        call    rax
        jmp     .LBB31_4
.LBB31_4:
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 15]
        mov     dl, byte ptr [rsp + 14]
        mov     rsi, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 48], rsi
        and     dl, 1
        mov     byte ptr [rsp + 56], dl
        mov     byte ptr [rsp + 57], cl
        mov     byte ptr [rsp + 71], 0
        mov     rdi, qword ptr [rax]
        mov     rsi, qword ptr [rax + 8]
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::block_on::{{closure}}@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 13], al
        jmp     .LBB31_7
.LBB31_5:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB31_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB31_5
.LBB31_7:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB31_8
.LBB31_8:
        mov     al, byte ptr [rsp + 13]
        add     rsp, 88
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB31_10:
        mov     rdi, qword ptr [rsp + 72]
        call    _Unwind_Resume@PLT
        ud2
.LBB31_11:
        jmp     .LBB31_10

tokio::coop::with_budget::{{closure}}:
        sub     rsp, 88
        mov     qword ptr [rsp + 16], rsi
        mov     rax, rdi
        mov     rdi, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 24], rax
        mov     qword ptr [rsp + 32], rdi
        mov     byte ptr [rsp + 71], 0
        mov     byte ptr [rsp + 71], 1
        mov     rax, qword ptr [rip + core::cell::Cell<T>::get@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 46], dl
        mov     byte ptr [rsp + 47], al
        jmp     .LBB32_3
.LBB32_1:
        test    byte ptr [rsp + 71], 1
        jne     .LBB32_11
        jmp     .LBB32_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB32_1
.LBB32_3:
        mov     rdi, qword ptr [rsp + 32]
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 46]
        mov     dl, byte ptr [rsp + 47]
        mov     byte ptr [rsp + 14], dl
        mov     byte ptr [rsp + 15], cl
        movzx   esi, byte ptr [rax + 16]
        movzx   edx, byte ptr [rax + 17]
        mov     rax, qword ptr [rip + core::cell::Cell<T>::set@GOTPCREL]
        call    rax
        jmp     .LBB32_4
.LBB32_4:
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 15]
        mov     dl, byte ptr [rsp + 14]
        mov     rsi, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 48], rsi
        and     dl, 1
        mov     byte ptr [rsp + 56], dl
        mov     byte ptr [rsp + 57], cl
        mov     byte ptr [rsp + 71], 0
        mov     rdi, qword ptr [rax]
        mov     rsi, qword ptr [rax + 8]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}::{{closure}}@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 13], al
        jmp     .LBB32_7
.LBB32_5:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB32_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB32_5
.LBB32_7:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB32_8
.LBB32_8:
        mov     al, byte ptr [rsp + 13]
        and     al, 1
        movzx   eax, al
        add     rsp, 88
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB32_10:
        mov     rdi, qword ptr [rsp + 72]
        call    _Unwind_Resume@PLT
        ud2
.LBB32_11:
        jmp     .LBB32_10

tokio::coop::with_budget::{{closure}}:
        sub     rsp, 88
        mov     qword ptr [rsp + 16], rsi
        mov     rax, rdi
        mov     rdi, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 24], rax
        mov     qword ptr [rsp + 32], rdi
        mov     byte ptr [rsp + 71], 0
        mov     byte ptr [rsp + 71], 1
        mov     rax, qword ptr [rip + core::cell::Cell<T>::get@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 46], dl
        mov     byte ptr [rsp + 47], al
        jmp     .LBB33_3
.LBB33_1:
        test    byte ptr [rsp + 71], 1
        jne     .LBB33_11
        jmp     .LBB33_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB33_1
.LBB33_3:
        mov     rdi, qword ptr [rsp + 32]
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 46]
        mov     dl, byte ptr [rsp + 47]
        mov     byte ptr [rsp + 14], dl
        mov     byte ptr [rsp + 15], cl
        movzx   esi, byte ptr [rax + 16]
        movzx   edx, byte ptr [rax + 17]
        mov     rax, qword ptr [rip + core::cell::Cell<T>::set@GOTPCREL]
        call    rax
        jmp     .LBB33_4
.LBB33_4:
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 15]
        mov     dl, byte ptr [rsp + 14]
        mov     rsi, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 48], rsi
        and     dl, 1
        mov     byte ptr [rsp + 56], dl
        mov     byte ptr [rsp + 57], cl
        mov     byte ptr [rsp + 71], 0
        mov     rdi, qword ptr [rax]
        mov     rsi, qword ptr [rax + 8]
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::block_on::{{closure}}@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 13], al
        jmp     .LBB33_7
.LBB33_5:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB33_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB33_5
.LBB33_7:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB33_8
.LBB33_8:
        mov     al, byte ptr [rsp + 13]
        and     al, 1
        movzx   eax, al
        add     rsp, 88
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB33_10:
        mov     rdi, qword ptr [rsp + 72]
        call    _Unwind_Resume@PLT
        ud2
.LBB33_11:
        jmp     .LBB33_10

tokio::coop::with_budget::{{closure}}:
        sub     rsp, 88
        mov     qword ptr [rsp + 16], rsi
        mov     rax, rdi
        mov     rdi, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 24], rax
        mov     qword ptr [rsp + 32], rdi
        mov     byte ptr [rsp + 71], 0
        mov     byte ptr [rsp + 71], 1
        mov     rax, qword ptr [rip + core::cell::Cell<T>::get@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 46], dl
        mov     byte ptr [rsp + 47], al
        jmp     .LBB34_3
.LBB34_1:
        test    byte ptr [rsp + 71], 1
        jne     .LBB34_11
        jmp     .LBB34_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB34_1
.LBB34_3:
        mov     rdi, qword ptr [rsp + 32]
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 46]
        mov     dl, byte ptr [rsp + 47]
        mov     byte ptr [rsp + 14], dl
        mov     byte ptr [rsp + 15], cl
        movzx   esi, byte ptr [rax + 8]
        movzx   edx, byte ptr [rax + 9]
        mov     rax, qword ptr [rip + core::cell::Cell<T>::set@GOTPCREL]
        call    rax
        jmp     .LBB34_4
.LBB34_4:
        mov     rax, qword ptr [rsp + 24]
        mov     cl, byte ptr [rsp + 15]
        mov     dl, byte ptr [rsp + 14]
        mov     rsi, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 48], rsi
        and     dl, 1
        mov     byte ptr [rsp + 56], dl
        mov     byte ptr [rsp + 57], cl
        mov     byte ptr [rsp + 71], 0
        mov     rdi, qword ptr [rax]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}@GOTPCREL]
        call    rax
        jmp     .LBB34_7
.LBB34_5:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB34_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB34_5
.LBB34_7:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::coop::with_budget::ResetGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB34_8
.LBB34_8:
        add     rsp, 88
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB34_10:
        mov     rdi, qword ptr [rsp + 72]
        call    _Unwind_Resume@PLT
        ud2
.LBB34_11:
        mov     rdi, qword ptr [rsp + 24]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>@GOTPCREL]
        call    rax
        jmp     .LBB34_10

tokio::coop::CURRENT::__getit:
        sub     rsp, 24
        mov     qword ptr [rsp + 16], rdi
        mov     rax, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 8], rax
        data16
        lea     rdi, [rip + tokio::coop::CURRENT::__getit::__KEY@TLSGD]
        data16
        data16
        rex64
        call    __tls_get_addr@PLT
        mov     rsi, qword ptr [rsp + 8]
        mov     rdi, rax
        mov     rax, qword ptr [rip + std::sys::common::thread_local::fast_local::Key<T>::get@GOTPCREL]
        call    rax
        add     rsp, 24
        ret

tokio::park::thread::CachedParkThread::block_on:
        sub     rsp, 296
        mov     qword ptr [rsp + 96], rdi
        mov     qword ptr [rsp + 104], rsi
        mov     qword ptr [rsp + 112], rdx
        mov     byte ptr [rsp + 223], 0
        mov     byte ptr [rsp + 223], 1
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::get_unpark@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 120], rax
        jmp     .LBB36_3
.LBB36_1:
        test    byte ptr [rsp + 223], 1
        jne     .LBB36_37
        jmp     .LBB36_36
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 224], rcx
        mov     dword ptr [rsp + 232], eax
        jmp     .LBB36_1
.LBB36_3:
        mov     rdi, qword ptr [rsp + 120]
        mov     rax, qword ptr [rip + <core::result::Result<T,E> as core::ops::try_trait::Try>::branch@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 88], rax
        jmp     .LBB36_4
.LBB36_4:
        mov     rax, qword ptr [rsp + 88]
        mov     qword ptr [rsp + 152], rax
        mov     rdx, qword ptr [rsp + 152]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB36_6
        mov     rdi, qword ptr [rsp + 152]
        mov     rax, qword ptr [rip + tokio::park::thread::UnparkThread::into_waker@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 72], rdx
        mov     qword ptr [rsp + 80], rax
        jmp     .LBB36_7
.LBB36_6:
        lea     rdi, [rip + .L__unnamed_10]
        mov     rax, qword ptr [rip + <core::result::Result<T,F> as core::ops::try_trait::FromResidual<core::result::Result<core::convert::Infallible,E>>>::from_residual@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 71], al
        jmp     .LBB36_33
.LBB36_7:
        mov     rax, qword ptr [rsp + 72]
        mov     rcx, qword ptr [rsp + 80]
        mov     qword ptr [rsp + 136], rcx
        mov     qword ptr [rsp + 144], rax
        lea     rdi, [rsp + 136]
        call    core::task::wake::Context::from_waker
        mov     qword ptr [rsp + 56], rax
        jmp     .LBB36_10
.LBB36_8:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::task::wake::Waker>@GOTPCREL]
        lea     rdi, [rsp + 136]
        call    rax
        jmp     .LBB36_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 224], rcx
        mov     dword ptr [rsp + 232], eax
        jmp     .LBB36_8
.LBB36_10:
        mov     rax, qword ptr [rsp + 112]
        mov     rcx, qword ptr [rsp + 104]
        mov     rdx, qword ptr [rsp + 56]
        mov     qword ptr [rsp + 160], rdx
        mov     byte ptr [rsp + 223], 0
        mov     qword ptr [rsp + 168], rcx
        mov     qword ptr [rsp + 176], rax
        lea     rax, [rsp + 168]
        mov     qword ptr [rsp + 240], rax
        mov     rax, qword ptr [rsp + 240]
        mov     qword ptr [rsp + 48], rax
        jmp     .LBB36_14
.LBB36_11:
        jmp     .LBB36_8
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 32], rcx
        mov     dword ptr [rsp + 44], eax
        jmp     .LBB36_13
.LBB36_13:
        mov     rcx, qword ptr [rsp + 32]
        mov     eax, dword ptr [rsp + 44]
        mov     qword ptr [rsp + 224], rcx
        mov     dword ptr [rsp + 232], eax
        jmp     .LBB36_11
.LBB36_14:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 184], rax
.LBB36_15:
        lea     rax, [rsp + 184]
        mov     qword ptr [rsp + 200], rax
        lea     rax, [rsp + 160]
        mov     qword ptr [rsp + 208], rax
        mov     rax, qword ptr [rsp + 200]
        mov     qword ptr [rsp + 8], rax
        mov     rax, qword ptr [rsp + 208]
        mov     qword ptr [rsp + 16], rax
        mov     byte ptr [rsp + 255], 0
        mov     byte ptr [rsp + 255], 1
        mov     rax, qword ptr [rip + tokio::coop::Budget::initial@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 30], dl
        mov     byte ptr [rsp + 31], al
        jmp     .LBB36_17
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 256], rcx
        mov     dword ptr [rsp + 264], eax
        test    byte ptr [rsp + 255], 1
        jne     .LBB36_19
        jmp     .LBB36_18
.LBB36_17:
        mov     rax, qword ptr [rsp + 16]
        mov     rcx, qword ptr [rsp + 8]
        mov     dl, byte ptr [rsp + 30]
        mov     sil, byte ptr [rsp + 31]
        mov     byte ptr [rsp + 255], 0
        and     sil, 1
        mov     byte ptr [rsp + 288], sil
        mov     byte ptr [rsp + 289], dl
        mov     qword ptr [rsp + 272], rcx
        mov     qword ptr [rsp + 280], rax
        lea     rdi, [rip + .L__unnamed_11]
        mov     rax, qword ptr [rip + std::thread::local::LocalKey<T>::with@GOTPCREL]
        lea     rsi, [rsp + 272]
        call    rax
        mov     byte ptr [rsp + 7], al
        jmp     .LBB36_20
.LBB36_18:
        mov     rcx, qword ptr [rsp + 256]
        mov     eax, dword ptr [rsp + 264]
        mov     qword ptr [rsp + 32], rcx
        mov     dword ptr [rsp + 44], eax
        jmp     .LBB36_13
.LBB36_19:
        jmp     .LBB36_18
.LBB36_20:
        jmp     .LBB36_21
.LBB36_21:
        mov     al, byte ptr [rsp + 7]
        mov     byte ptr [rsp + 199], al
        xor     eax, eax
        mov     ecx, 1
        cmp     byte ptr [rsp + 199], 2
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB36_23
        mov     al, byte ptr [rsp + 199]
        and     al, 1
        mov     byte ptr [rsp + 135], al
        jmp     .LBB36_24
.LBB36_23:
        jmp     .LBB36_25
.LBB36_24:
        jmp     .LBB36_30
.LBB36_25:
        mov     rdi, qword ptr [rsp + 96]
        mov     rax, qword ptr [rip + <tokio::park::thread::CachedParkThread as tokio::park::Park>::park@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 6], al
        jmp     .LBB36_26
.LBB36_26:
        mov     al, byte ptr [rsp + 6]
        movzx   edi, al
        and     edi, 1
        mov     rax, qword ptr [rip + <core::result::Result<T,E> as core::ops::try_trait::Try>::branch@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 5], al
        jmp     .LBB36_27
.LBB36_27:
        mov     al, byte ptr [rsp + 5]
        and     al, 1
        mov     byte ptr [rsp + 222], al
        mov     al, byte ptr [rsp + 222]
        and     al, 1
        movzx   eax, al
        cmp     rax, 0
        je      .LBB36_15
        lea     rdi, [rip + .L__unnamed_12]
        mov     rax, qword ptr [rip + <core::result::Result<T,F> as core::ops::try_trait::FromResidual<core::result::Result<core::convert::Infallible,E>>>::from_residual@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 4], al
        jmp     .LBB36_29
.LBB36_29:
        mov     al, byte ptr [rsp + 4]
        mov     byte ptr [rsp + 135], al
        jmp     .LBB36_24
.LBB36_30:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::task::wake::Waker>@GOTPCREL]
        lea     rdi, [rsp + 136]
        call    rax
        jmp     .LBB36_31
.LBB36_31:
        test    byte ptr [rsp + 223], 1
        jne     .LBB36_35
        jmp     .LBB36_34
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB36_33:
        mov     al, byte ptr [rsp + 71]
        mov     byte ptr [rsp + 135], al
        jmp     .LBB36_31
.LBB36_34:
        mov     al, byte ptr [rsp + 135]
        add     rsp, 296
        ret
.LBB36_35:
        jmp     .LBB36_34
.LBB36_36:
        mov     rdi, qword ptr [rsp + 224]
        call    _Unwind_Resume@PLT
        ud2
.LBB36_37:
        jmp     .LBB36_36

tokio::park::thread::CachedParkThread::block_on:
        sub     rsp, 312
        mov     qword ptr [rsp + 104], rdi
        mov     qword ptr [rsp + 112], rsi
        mov     byte ptr [rsp + 239], 0
        mov     byte ptr [rsp + 239], 1
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::get_unpark@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 120], rax
        jmp     .LBB37_3
.LBB37_1:
        test    byte ptr [rsp + 239], 1
        jne     .LBB37_37
        jmp     .LBB37_36
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 240], rcx
        mov     dword ptr [rsp + 248], eax
        jmp     .LBB37_1
.LBB37_3:
        mov     rdi, qword ptr [rsp + 120]
        mov     rax, qword ptr [rip + <core::result::Result<T,E> as core::ops::try_trait::Try>::branch@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 96], rax
        jmp     .LBB37_4
.LBB37_4:
        mov     rax, qword ptr [rsp + 96]
        mov     qword ptr [rsp + 152], rax
        mov     rdx, qword ptr [rsp + 152]
        xor     eax, eax
        mov     ecx, 1
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB37_6
        mov     rdi, qword ptr [rsp + 152]
        mov     rax, qword ptr [rip + tokio::park::thread::UnparkThread::into_waker@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 80], rdx
        mov     qword ptr [rsp + 88], rax
        jmp     .LBB37_7
.LBB37_6:
        lea     rdi, [rip + .L__unnamed_10]
        mov     rax, qword ptr [rip + <core::result::Result<T,F> as core::ops::try_trait::FromResidual<core::result::Result<core::convert::Infallible,E>>>::from_residual@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 79], al
        jmp     .LBB37_33
.LBB37_7:
        mov     rax, qword ptr [rsp + 80]
        mov     rcx, qword ptr [rsp + 88]
        mov     qword ptr [rsp + 136], rcx
        mov     qword ptr [rsp + 144], rax
        lea     rdi, [rsp + 136]
        call    core::task::wake::Context::from_waker
        mov     qword ptr [rsp + 64], rax
        jmp     .LBB37_10
.LBB37_8:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::task::wake::Waker>@GOTPCREL]
        lea     rdi, [rsp + 136]
        call    rax
        jmp     .LBB37_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 240], rcx
        mov     dword ptr [rsp + 248], eax
        jmp     .LBB37_8
.LBB37_10:
        mov     rax, qword ptr [rsp + 112]
        mov     rcx, qword ptr [rsp + 64]
        mov     qword ptr [rsp + 160], rcx
        mov     byte ptr [rsp + 239], 0
        mov     rcx, qword ptr [rax]
        mov     qword ptr [rsp + 168], rcx
        mov     rcx, qword ptr [rax + 8]
        mov     qword ptr [rsp + 176], rcx
        mov     rcx, qword ptr [rax + 16]
        mov     qword ptr [rsp + 184], rcx
        mov     rax, qword ptr [rax + 24]
        mov     qword ptr [rsp + 192], rax
        lea     rax, [rsp + 168]
        mov     qword ptr [rsp + 256], rax
        mov     rax, qword ptr [rsp + 256]
        mov     qword ptr [rsp + 56], rax
        jmp     .LBB37_14
.LBB37_11:
        jmp     .LBB37_8
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 40], rcx
        mov     dword ptr [rsp + 52], eax
        jmp     .LBB37_13
.LBB37_13:
        mov     rcx, qword ptr [rsp + 40]
        mov     eax, dword ptr [rsp + 52]
        mov     qword ptr [rsp + 240], rcx
        mov     dword ptr [rsp + 248], eax
        jmp     .LBB37_11
.LBB37_14:
        mov     rax, qword ptr [rsp + 56]
        mov     qword ptr [rsp + 200], rax
.LBB37_15:
        lea     rax, [rsp + 200]
        mov     qword ptr [rsp + 216], rax
        lea     rax, [rsp + 160]
        mov     qword ptr [rsp + 224], rax
        mov     rax, qword ptr [rsp + 216]
        mov     qword ptr [rsp + 16], rax
        mov     rax, qword ptr [rsp + 224]
        mov     qword ptr [rsp + 24], rax
        mov     byte ptr [rsp + 271], 0
        mov     byte ptr [rsp + 271], 1
        mov     rax, qword ptr [rip + tokio::coop::Budget::initial@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 38], dl
        mov     byte ptr [rsp + 39], al
        jmp     .LBB37_17
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 272], rcx
        mov     dword ptr [rsp + 280], eax
        test    byte ptr [rsp + 271], 1
        jne     .LBB37_19
        jmp     .LBB37_18
.LBB37_17:
        mov     rax, qword ptr [rsp + 24]
        mov     rcx, qword ptr [rsp + 16]
        mov     dl, byte ptr [rsp + 38]
        mov     sil, byte ptr [rsp + 39]
        mov     byte ptr [rsp + 271], 0
        and     sil, 1
        mov     byte ptr [rsp + 304], sil
        mov     byte ptr [rsp + 305], dl
        mov     qword ptr [rsp + 288], rcx
        mov     qword ptr [rsp + 296], rax
        lea     rdi, [rip + .L__unnamed_11]
        mov     rax, qword ptr [rip + std::thread::local::LocalKey<T>::with@GOTPCREL]
        lea     rsi, [rsp + 288]
        call    rax
        mov     byte ptr [rsp + 15], al
        jmp     .LBB37_20
.LBB37_18:
        mov     rcx, qword ptr [rsp + 272]
        mov     eax, dword ptr [rsp + 280]
        mov     qword ptr [rsp + 40], rcx
        mov     dword ptr [rsp + 52], eax
        jmp     .LBB37_13
.LBB37_19:
        jmp     .LBB37_18
.LBB37_20:
        jmp     .LBB37_21
.LBB37_21:
        mov     al, byte ptr [rsp + 15]
        and     al, 1
        mov     byte ptr [rsp + 215], al
        mov     al, byte ptr [rsp + 215]
        and     al, 1
        movzx   eax, al
        cmp     rax, 0
        jne     .LBB37_23
        mov     byte ptr [rsp + 135], 0
        jmp     .LBB37_24
.LBB37_23:
        jmp     .LBB37_25
.LBB37_24:
        jmp     .LBB37_30
.LBB37_25:
        mov     rdi, qword ptr [rsp + 104]
        mov     rax, qword ptr [rip + <tokio::park::thread::CachedParkThread as tokio::park::Park>::park@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 14], al
        jmp     .LBB37_26
.LBB37_26:
        mov     al, byte ptr [rsp + 14]
        movzx   edi, al
        and     edi, 1
        mov     rax, qword ptr [rip + <core::result::Result<T,E> as core::ops::try_trait::Try>::branch@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 13], al
        jmp     .LBB37_27
.LBB37_27:
        mov     al, byte ptr [rsp + 13]
        and     al, 1
        mov     byte ptr [rsp + 238], al
        mov     al, byte ptr [rsp + 238]
        and     al, 1
        movzx   eax, al
        cmp     rax, 0
        je      .LBB37_15
        lea     rdi, [rip + .L__unnamed_12]
        mov     rax, qword ptr [rip + <core::result::Result<T,F> as core::ops::try_trait::FromResidual<core::result::Result<core::convert::Infallible,E>>>::from_residual@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 12], al
        jmp     .LBB37_29
.LBB37_29:
        mov     al, byte ptr [rsp + 12]
        and     al, 1
        mov     byte ptr [rsp + 135], al
        jmp     .LBB37_24
.LBB37_30:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::task::wake::Waker>@GOTPCREL]
        lea     rdi, [rsp + 136]
        call    rax
        jmp     .LBB37_31
.LBB37_31:
        test    byte ptr [rsp + 239], 1
        jne     .LBB37_35
        jmp     .LBB37_34
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB37_33:
        mov     al, byte ptr [rsp + 79]
        and     al, 1
        mov     byte ptr [rsp + 135], al
        jmp     .LBB37_31
.LBB37_34:
        mov     al, byte ptr [rsp + 135]
        and     al, 1
        movzx   eax, al
        add     rsp, 312
        ret
.LBB37_35:
        jmp     .LBB37_34
.LBB37_36:
        mov     rdi, qword ptr [rsp + 240]
        call    _Unwind_Resume@PLT
        ud2
.LBB37_37:
        jmp     .LBB37_36

tokio::park::thread::CachedParkThread::block_on::{{closure}}:
        sub     rsp, 24
        mov     qword ptr [rsp], rdi
        mov     qword ptr [rsp + 8], rsi
        mov     rdi, qword ptr [rsp]
        call    qword ptr [rip + <&mut T as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     qword ptr [rsp + 16], rax
        mov     rdi, qword ptr [rsp + 16]
        mov     rsi, qword ptr [rsp + 8]
        call    example::main::{{closure}}
        and     al, 1
        movzx   eax, al
        add     rsp, 24
        ret

tokio::park::thread::CachedParkThread::block_on::{{closure}}:
        sub     rsp, 24
        mov     qword ptr [rsp], rdi
        mov     qword ptr [rsp + 8], rsi
        mov     rdi, qword ptr [rsp]
        call    qword ptr [rip + <&mut T as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     qword ptr [rsp + 16], rax
        mov     rdi, qword ptr [rsp + 16]
        mov     rsi, qword ptr [rsp + 8]
        call    qword ptr [rip + <tokio::future::poll_fn::PollFn<F> as core::future::future::Future>::poll@GOTPCREL]
        add     rsp, 24
        ret

tokio::future::poll_fn::poll_fn:
        mov     qword ptr [rsp - 16], rdi
        mov     qword ptr [rsp - 8], rsi
        mov     rax, qword ptr [rsp - 16]
        mov     rdx, qword ptr [rsp - 8]
        ret

tokio::macros::scoped_tls::ScopedKey<T>::set:
        sub     rsp, 120
        mov     qword ptr [rsp + 8], rdi
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 32], rsi
        mov     byte ptr [rsp + 103], 0
        mov     byte ptr [rsp + 103], 1
        mov     rdi, qword ptr [rdi]
        lea     rax, [rsp + 32]
        mov     qword ptr [rsp + 40], rax
        mov     rsi, qword ptr [rsp + 40]
        mov     rax, qword ptr [rip + std::thread::local::LocalKey<T>::with@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 24], rax
        jmp     .LBB41_3
.LBB41_1:
        test    byte ptr [rsp + 103], 1
        jne     .LBB41_10
        jmp     .LBB41_9
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 104], rcx
        mov     dword ptr [rsp + 112], eax
        jmp     .LBB41_1
.LBB41_3:
        mov     rax, qword ptr [rsp + 16]
        mov     rcx, qword ptr [rsp + 24]
        mov     rdx, qword ptr [rsp + 8]
        mov     rdx, qword ptr [rdx]
        mov     qword ptr [rsp + 48], rdx
        mov     qword ptr [rsp + 56], rcx
        mov     byte ptr [rsp + 103], 0
        mov     rcx, qword ptr [rax + 16]
        mov     qword ptr [rsp + 80], rcx
        movups  xmm0, xmmword ptr [rax]
        movaps  xmmword ptr [rsp + 64], xmm0
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::enter::{{closure}}@GOTPCREL]
        lea     rdi, [rsp + 64]
        call    rax
        mov     qword ptr [rsp], rax
        jmp     .LBB41_6
.LBB41_4:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::macros::scoped_tls::ScopedKey<T>::set::Reset>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB41_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 104], rcx
        mov     dword ptr [rsp + 112], eax
        jmp     .LBB41_4
.LBB41_6:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::macros::scoped_tls::ScopedKey<T>::set::Reset>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB41_7
.LBB41_7:
        mov     rax, qword ptr [rsp]
        add     rsp, 120
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB41_9:
        mov     rdi, qword ptr [rsp + 104]
        call    _Unwind_Resume@PLT
        ud2
.LBB41_10:
        mov     rdi, qword ptr [rsp + 16]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::enter<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}},()>::{{closure}}>@GOTPCREL]
        call    rax
        jmp     .LBB41_9

tokio::macros::scoped_tls::ScopedKey<T>::set::{{closure}}:
        sub     rsp, 40
        mov     qword ptr [rsp + 8], rsi
        mov     rax, rdi
        mov     rdi, qword ptr [rsp + 8]
        mov     qword ptr [rsp + 16], rdi
        mov     qword ptr [rsp + 32], rax
        call    qword ptr [rip + core::cell::Cell<T>::get@GOTPCREL]
        mov     rdi, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 24], rax
        mov     rax, qword ptr [rsp + 32]
        mov     rsi, qword ptr [rax]
        call    qword ptr [rip + core::cell::Cell<T>::set@GOTPCREL]
        mov     rax, qword ptr [rsp + 24]
        add     rsp, 40
        ret

tokio::runtime::thread_pool::ThreadPool::block_on:
        sub     rsp, 88
        mov     qword ptr [rsp + 16], rsi
        mov     byte ptr [rsp + 71], 0
        mov     byte ptr [rsp + 71], 1
        mov     rax, qword ptr [rip + tokio::runtime::enter::enter@GOTPCREL]
        mov     edi, 1
        call    rax
        jmp     .LBB43_3
.LBB43_1:
        test    byte ptr [rsp + 71], 1
        jne     .LBB43_11
        jmp     .LBB43_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB43_1
.LBB43_3:
        mov     rax, qword ptr [rsp + 16]
        mov     byte ptr [rsp + 71], 0
        movups  xmm0, xmmword ptr [rax]
        movups  xmm1, xmmword ptr [rax + 16]
        movaps  xmmword ptr [rsp + 48], xmm1
        movaps  xmmword ptr [rsp + 32], xmm0
        mov     rax, qword ptr [rip + tokio::runtime::enter::Enter::block_on@GOTPCREL]
        lea     rdi, [rsp + 31]
        lea     rsi, [rsp + 32]
        call    rax
        mov     byte ptr [rsp + 15], al
        jmp     .LBB43_6
.LBB43_4:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 31]
        call    rax
        jmp     .LBB43_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB43_4
.LBB43_6:
        mov     al, byte ptr [rsp + 15]
        movzx   edi, al
        and     edi, 1
        lea     rsi, [rip + .L__unnamed_13]
        lea     rcx, [rip + .L__unnamed_14]
        mov     rax, qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        mov     edx, 21
        call    rax
        jmp     .LBB43_7
.LBB43_7:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 31]
        call    rax
        jmp     .LBB43_8
.LBB43_8:
        add     rsp, 88
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB43_10:
        mov     rdi, qword ptr [rsp + 72]
        call    _Unwind_Resume@PLT
        ud2
.LBB43_11:
        jmp     .LBB43_10

tokio::runtime::basic_scheduler::BasicScheduler::block_on:
        sub     rsp, 376
        mov     qword ptr [rsp + 40], rdi
        mov     byte ptr [rsp + 342], 0
        mov     byte ptr [rsp + 343], 0
        mov     rax, qword ptr [rsi]
        mov     qword ptr [rsp + 56], rax
        mov     rax, qword ptr [rsi + 8]
        mov     qword ptr [rsp + 64], rax
        mov     rax, qword ptr [rsi + 16]
        mov     qword ptr [rsp + 72], rax
        mov     rax, qword ptr [rsi + 24]
        mov     qword ptr [rsp + 80], rax
        lea     rax, [rsp + 56]
        mov     qword ptr [rsp + 360], rax
        mov     rax, qword ptr [rsp + 360]
        mov     qword ptr [rsp + 48], rax
        jmp     .LBB44_3
.LBB44_1:
        mov     rdi, qword ptr [rsp + 344]
        call    _Unwind_Resume@PLT
        ud2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 344], rcx
        mov     dword ptr [rsp + 352], eax
        jmp     .LBB44_1
.LBB44_3:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 88], rax
.LBB44_4:
        mov     rsi, qword ptr [rsp + 40]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::BasicScheduler::take_core@GOTPCREL]
        lea     rdi, [rsp + 96]
        call    rax
        jmp     .LBB44_5
.LBB44_5:
        mov     byte ptr [rsp + 342], 1
        mov     rdx, qword ptr [rsp + 96]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 1
        jne     .LBB44_7
        mov     byte ptr [rsp + 342], 0
        movups  xmm0, xmmword ptr [rsp + 96]
        movups  xmm1, xmmword ptr [rsp + 112]
        movaps  xmmword ptr [rsp + 144], xmm1
        movaps  xmmword ptr [rsp + 128], xmm0
        mov     rsi, qword ptr [rsp + 88]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::block_on@GOTPCREL]
        lea     rdi, [rsp + 128]
        call    rax
        jmp     .LBB44_10
.LBB44_7:
        mov     rax, qword ptr [rip + tokio::runtime::enter::enter@GOTPCREL]
        xor     edi, edi
        call    rax
        jmp     .LBB44_12
.LBB44_8:
        mov     rdx, qword ptr [rsp + 96]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 1
        je      .LBB44_40
        jmp     .LBB44_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 344], rcx
        mov     dword ptr [rsp + 352], eax
        jmp     .LBB44_8
.LBB44_10:
        jmp     .LBB44_11
.LBB44_11:
        mov     rdx, qword ptr [rsp + 96]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 1
        je      .LBB44_30
        jmp     .LBB44_31
.LBB44_12:
        mov     rsi, qword ptr [rsp + 40]
        add     rsi, 32
        mov     rax, qword ptr [rip + tokio::sync::notify::Notify::notified@GOTPCREL]
        lea     rdi, [rsp + 176]
        call    rax
        jmp     .LBB44_15
.LBB44_13:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 175]
        call    rax
        jmp     .LBB44_8
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 344], rcx
        mov     dword ptr [rsp + 352], eax
        jmp     .LBB44_13
.LBB44_15:
        lea     rdi, [rsp + 240]
        lea     rsi, [rsp + 176]
        mov     edx, 64
        call    memcpy@PLT
        lea     rax, [rsp + 240]
        mov     qword ptr [rsp + 368], rax
        mov     rax, qword ptr [rsp + 368]
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB44_18
.LBB44_16:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::sync::notify::Notified>@GOTPCREL]
        lea     rdi, [rsp + 240]
        call    rax
        jmp     .LBB44_13
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 344], rcx
        mov     dword ptr [rsp + 352], eax
        jmp     .LBB44_16
.LBB44_18:
        mov     rax, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 304], rax
        lea     rax, [rsp + 304]
        mov     qword ptr [rsp + 320], rax
        lea     rax, [rsp + 88]
        mov     qword ptr [rsp + 328], rax
        mov     rdi, qword ptr [rsp + 320]
        mov     rsi, qword ptr [rsp + 328]
        mov     rax, qword ptr [rip + tokio::future::poll_fn::poll_fn@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 24], rax
        jmp     .LBB44_19
.LBB44_19:
        mov     rdx, qword ptr [rsp + 16]
        mov     rsi, qword ptr [rsp + 24]
        mov     rax, qword ptr [rip + tokio::runtime::enter::Enter::block_on@GOTPCREL]
        lea     rdi, [rsp + 175]
        call    rax
        mov     byte ptr [rsp + 15], al
        jmp     .LBB44_20
.LBB44_20:
        mov     al, byte ptr [rsp + 15]
        movzx   edi, al
        lea     rsi, [rip + .L__unnamed_15]
        lea     rcx, [rip + .L__unnamed_16]
        mov     rax, qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        mov     edx, 27
        call    rax
        mov     byte ptr [rsp + 14], al
        jmp     .LBB44_21
.LBB44_21:
        mov     al, byte ptr [rsp + 14]
        and     al, 1
        mov     byte ptr [rsp + 319], al
        mov     byte ptr [rsp + 343], 1
        mov     al, byte ptr [rsp + 319]
        and     al, 1
        movzx   eax, al
        cmp     rax, 1
        jne     .LBB44_23
        mov     byte ptr [rsp + 343], 0
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::sync::notify::Notified>@GOTPCREL]
        lea     rdi, [rsp + 240]
        call    rax
        jmp     .LBB44_26
.LBB44_23:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::sync::notify::Notified>@GOTPCREL]
        lea     rdi, [rsp + 240]
        call    rax
        jmp     .LBB44_33
.LBB44_24:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 175]
        call    rax
        jmp     .LBB44_27
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 344], rcx
        mov     dword ptr [rsp + 352], eax
        jmp     .LBB44_24
.LBB44_26:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 175]
        call    rax
        jmp     .LBB44_29
.LBB44_27:
        mov     al, byte ptr [rsp + 319]
        and     al, 1
        movzx   eax, al
        cmp     rax, 1
        je      .LBB44_38
        jmp     .LBB44_8
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 344], rcx
        mov     dword ptr [rsp + 352], eax
        jmp     .LBB44_27
.LBB44_29:
        mov     byte ptr [rsp + 343], 0
        jmp     .LBB44_11
.LBB44_30:
        test    byte ptr [rsp + 342], 1
        jne     .LBB44_32
.LBB44_31:
        mov     byte ptr [rsp + 342], 0
        add     rsp, 376
        ret
.LBB44_32:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard>@GOTPCREL]
        lea     rdi, [rsp + 96]
        call    rax
        jmp     .LBB44_31
.LBB44_33:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 175]
        call    rax
        jmp     .LBB44_34
.LBB44_34:
        jmp     .LBB44_35
.LBB44_35:
        mov     byte ptr [rsp + 343], 0
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<tokio::runtime::basic_scheduler::CoreGuard>>@GOTPCREL]
        lea     rdi, [rsp + 96]
        call    rax
        jmp     .LBB44_36
.LBB44_36:
        mov     byte ptr [rsp + 342], 0
        jmp     .LBB44_4
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB44_38:
        test    byte ptr [rsp + 343], 1
        je      .LBB44_8
        jmp     .LBB44_8
.LBB44_40:
        test    byte ptr [rsp + 342], 1
        je      .LBB44_1
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard>@GOTPCREL]
        lea     rdi, [rsp + 96]
        call    rax
        jmp     .LBB44_1

tokio::runtime::basic_scheduler::BasicScheduler::block_on::{{closure}}:
        sub     rsp, 40
        mov     qword ptr [rsp], rdi
        mov     qword ptr [rsp + 8], rsi
        mov     rdi, qword ptr [rdi]
        call    qword ptr [rip + <&mut T as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     rsi, qword ptr [rsp + 8]
        mov     qword ptr [rsp + 32], rax
        mov     rdi, qword ptr [rsp + 32]
        call    qword ptr [rip + <tokio::sync::notify::Notified as core::future::future::Future>::poll@GOTPCREL]
        and     al, 1
        mov     byte ptr [rsp + 20], al
        lea     rdi, [rsp + 20]
        call    qword ptr [rip + core::task::poll::Poll<T>::is_ready@GOTPCREL]
        test    al, 1
        jne     .LBB45_2
        mov     rax, qword ptr [rsp]
        mov     rdi, qword ptr [rax + 8]
        call    qword ptr [rip + <&mut T as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     rsi, qword ptr [rsp + 8]
        mov     qword ptr [rsp + 24], rax
        mov     rdi, qword ptr [rsp + 24]
        call    example::main::{{closure}}
        and     al, 1
        mov     byte ptr [rsp + 22], al
        mov     al, byte ptr [rsp + 22]
        and     al, 1
        movzx   eax, al
        cmp     rax, 0
        je      .LBB45_3
        jmp     .LBB45_4
.LBB45_2:
        mov     byte ptr [rsp + 21], 0
        mov     al, byte ptr [rsp + 21]
        and     al, 1
        mov     byte ptr [rsp + 19], al
        jmp     .LBB45_5
.LBB45_3:
        mov     byte ptr [rsp + 23], 1
        mov     al, byte ptr [rsp + 23]
        and     al, 1
        mov     byte ptr [rsp + 19], al
        jmp     .LBB45_5
.LBB45_4:
        mov     byte ptr [rsp + 19], 2
.LBB45_5:
        mov     al, byte ptr [rsp + 19]
        add     rsp, 40
        ret

tokio::runtime::basic_scheduler::Context::enter:
        sub     rsp, 184
        mov     qword ptr [rsp + 56], rdi
        mov     qword ptr [rsp + 64], rdx
        mov     qword ptr [rsp + 72], rcx
        mov     byte ptr [rsp + 167], 0
        mov     byte ptr [rsp + 166], 0
        mov     byte ptr [rsp + 167], 1
        mov     byte ptr [rsp + 166], 1
        mov     qword ptr [rsp + 112], rsi
        add     rdi, 8
        lea     rsi, [rip + .L__unnamed_17]
        mov     rax, qword ptr [rip + core::cell::RefCell<T>::borrow_mut@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 80], rdx
        mov     qword ptr [rsp + 88], rax
        jmp     .LBB46_3
.LBB46_1:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        lea     rdi, [rsp + 112]
        call    rax
        jmp     .LBB46_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 168], rcx
        mov     dword ptr [rsp + 176], eax
        jmp     .LBB46_1
.LBB46_3:
        mov     rax, qword ptr [rsp + 80]
        mov     rcx, qword ptr [rsp + 88]
        mov     qword ptr [rsp + 120], rcx
        mov     qword ptr [rsp + 128], rax
        mov     rax, qword ptr [rip + <core::cell::RefMut<T> as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        lea     rdi, [rsp + 120]
        call    rax
        mov     qword ptr [rsp + 48], rax
        jmp     .LBB46_6
.LBB46_4:
        test    byte ptr [rsp + 166], 1
        jne     .LBB46_27
        jmp     .LBB46_26
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 168], rcx
        mov     dword ptr [rsp + 176], eax
        jmp     .LBB46_4
.LBB46_6:
        mov     rdi, qword ptr [rsp + 48]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        call    rax
        jmp     .LBB46_9
.LBB46_7:
        mov     rax, qword ptr [rsp + 48]
        mov     byte ptr [rsp + 166], 0
        mov     rcx, qword ptr [rsp + 112]
        mov     qword ptr [rax], rcx
        jmp     .LBB46_4
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 168], rcx
        mov     dword ptr [rsp + 176], eax
        jmp     .LBB46_7
.LBB46_9:
        mov     rax, qword ptr [rsp + 48]
        mov     byte ptr [rsp + 166], 0
        mov     rcx, qword ptr [rsp + 112]
        mov     qword ptr [rax], rcx
        mov     byte ptr [rsp + 166], 0
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 120]
        call    rax
        jmp     .LBB46_12
.LBB46_10:
        test    byte ptr [rsp + 167], 1
        jne     .LBB46_29
        jmp     .LBB46_28
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 168], rcx
        mov     dword ptr [rsp + 176], eax
        jmp     .LBB46_10
.LBB46_12:
        mov     rsi, qword ptr [rsp + 72]
        mov     rdi, qword ptr [rsp + 64]
        mov     byte ptr [rsp + 167], 0
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 47], al
        jmp     .LBB46_13
.LBB46_13:
        mov     rdi, qword ptr [rsp + 56]
        add     rdi, 8
        lea     rsi, [rip + .L__unnamed_18]
        mov     rax, qword ptr [rip + core::cell::RefCell<T>::borrow_mut@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 24], rdx
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB46_16
.LBB46_14:
        jmp     .LBB46_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 168], rcx
        mov     dword ptr [rsp + 176], eax
        jmp     .LBB46_14
.LBB46_16:
        mov     rax, qword ptr [rsp + 24]
        mov     rcx, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 144], rcx
        mov     qword ptr [rsp + 152], rax
        mov     rax, qword ptr [rip + <core::cell::RefMut<T> as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        lea     rdi, [rsp + 144]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB46_19
.LBB46_17:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 144]
        call    rax
        jmp     .LBB46_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 168], rcx
        mov     dword ptr [rsp + 176], eax
        jmp     .LBB46_17
.LBB46_19:
        mov     rdi, qword ptr [rsp + 16]
        mov     rax, qword ptr [rip + core::option::Option<T>::take@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 8], rax
        jmp     .LBB46_20
.LBB46_20:
        mov     rdi, qword ptr [rsp + 8]
        lea     rsi, [rip + .L__unnamed_19]
        lea     rcx, [rip + .L__unnamed_20]
        mov     rax, qword ptr [rip + core::option::Option<T>::expect@GOTPCREL]
        mov     edx, 12
        call    rax
        mov     qword ptr [rsp], rax
        jmp     .LBB46_21
.LBB46_21:
        mov     rax, qword ptr [rsp]
        mov     qword ptr [rsp + 136], rax
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 144]
        call    rax
        jmp     .LBB46_24
.LBB46_22:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>@GOTPCREL]
        lea     rdi, [rsp + 136]
        call    rax
        jmp     .LBB46_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 168], rcx
        mov     dword ptr [rsp + 176], eax
        jmp     .LBB46_22
.LBB46_24:
        mov     al, byte ptr [rsp + 47]
        mov     rcx, qword ptr [rsp + 136]
        mov     qword ptr [rsp + 96], rcx
        and     al, 1
        mov     byte ptr [rsp + 104], al
        mov     rax, qword ptr [rsp + 96]
        mov     dl, byte ptr [rsp + 104]
        add     rsp, 184
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB46_26:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 120]
        call    rax
        jmp     .LBB46_10
.LBB46_27:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        lea     rdi, [rsp + 112]
        call    rax
        jmp     .LBB46_26
.LBB46_28:
        mov     rdi, qword ptr [rsp + 168]
        call    _Unwind_Resume@PLT
        ud2
.LBB46_29:
        jmp     .LBB46_28

tokio::runtime::basic_scheduler::Context::enter:
        sub     rsp, 168
        mov     qword ptr [rsp + 56], rdi
        mov     qword ptr [rsp + 80], rdx
        mov     byte ptr [rsp + 151], 0
        mov     byte ptr [rsp + 150], 0
        mov     byte ptr [rsp + 151], 1
        mov     byte ptr [rsp + 150], 1
        mov     qword ptr [rsp + 96], rsi
        add     rdi, 8
        lea     rsi, [rip + .L__unnamed_17]
        mov     rax, qword ptr [rip + core::cell::RefCell<T>::borrow_mut@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 64], rdx
        mov     qword ptr [rsp + 72], rax
        jmp     .LBB47_3
.LBB47_1:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        lea     rdi, [rsp + 96]
        call    rax
        jmp     .LBB47_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 152], rcx
        mov     dword ptr [rsp + 160], eax
        jmp     .LBB47_1
.LBB47_3:
        mov     rax, qword ptr [rsp + 64]
        mov     rcx, qword ptr [rsp + 72]
        mov     qword ptr [rsp + 104], rcx
        mov     qword ptr [rsp + 112], rax
        mov     rax, qword ptr [rip + <core::cell::RefMut<T> as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        lea     rdi, [rsp + 104]
        call    rax
        mov     qword ptr [rsp + 48], rax
        jmp     .LBB47_6
.LBB47_4:
        test    byte ptr [rsp + 150], 1
        jne     .LBB47_27
        jmp     .LBB47_26
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 152], rcx
        mov     dword ptr [rsp + 160], eax
        jmp     .LBB47_4
.LBB47_6:
        mov     rdi, qword ptr [rsp + 48]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        call    rax
        jmp     .LBB47_9
.LBB47_7:
        mov     rax, qword ptr [rsp + 48]
        mov     byte ptr [rsp + 150], 0
        mov     rcx, qword ptr [rsp + 96]
        mov     qword ptr [rax], rcx
        jmp     .LBB47_4
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 152], rcx
        mov     dword ptr [rsp + 160], eax
        jmp     .LBB47_7
.LBB47_9:
        mov     rax, qword ptr [rsp + 48]
        mov     byte ptr [rsp + 150], 0
        mov     rcx, qword ptr [rsp + 96]
        mov     qword ptr [rax], rcx
        mov     byte ptr [rsp + 150], 0
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 104]
        call    rax
        jmp     .LBB47_12
.LBB47_10:
        test    byte ptr [rsp + 151], 1
        jne     .LBB47_29
        jmp     .LBB47_28
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 152], rcx
        mov     dword ptr [rsp + 160], eax
        jmp     .LBB47_10
.LBB47_12:
        mov     byte ptr [rsp + 151], 0
        mov     rdi, qword ptr [rsp + 80]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Context::run_task::{{closure}}@GOTPCREL]
        call    rax
        jmp     .LBB47_13
.LBB47_13:
        mov     rdi, qword ptr [rsp + 56]
        add     rdi, 8
        lea     rsi, [rip + .L__unnamed_18]
        mov     rax, qword ptr [rip + core::cell::RefCell<T>::borrow_mut@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 32], rdx
        mov     qword ptr [rsp + 40], rax
        jmp     .LBB47_16
.LBB47_14:
        jmp     .LBB47_10
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 152], rcx
        mov     dword ptr [rsp + 160], eax
        jmp     .LBB47_14
.LBB47_16:
        mov     rax, qword ptr [rsp + 32]
        mov     rcx, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 128], rcx
        mov     qword ptr [rsp + 136], rax
        mov     rax, qword ptr [rip + <core::cell::RefMut<T> as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        lea     rdi, [rsp + 128]
        call    rax
        mov     qword ptr [rsp + 24], rax
        jmp     .LBB47_19
.LBB47_17:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 128]
        call    rax
        jmp     .LBB47_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 152], rcx
        mov     dword ptr [rsp + 160], eax
        jmp     .LBB47_17
.LBB47_19:
        mov     rdi, qword ptr [rsp + 24]
        mov     rax, qword ptr [rip + core::option::Option<T>::take@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB47_20
.LBB47_20:
        mov     rdi, qword ptr [rsp + 16]
        lea     rsi, [rip + .L__unnamed_19]
        lea     rcx, [rip + .L__unnamed_20]
        mov     rax, qword ptr [rip + core::option::Option<T>::expect@GOTPCREL]
        mov     edx, 12
        call    rax
        mov     qword ptr [rsp + 8], rax
        jmp     .LBB47_21
.LBB47_21:
        mov     rax, qword ptr [rsp + 8]
        mov     qword ptr [rsp + 120], rax
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 128]
        call    rax
        jmp     .LBB47_24
.LBB47_22:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>@GOTPCREL]
        lea     rdi, [rsp + 120]
        call    rax
        jmp     .LBB47_14
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 152], rcx
        mov     dword ptr [rsp + 160], eax
        jmp     .LBB47_22
.LBB47_24:
        mov     rax, qword ptr [rsp + 120]
        mov     qword ptr [rsp + 88], rax
        mov     rax, qword ptr [rsp + 88]
        add     rsp, 168
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB47_26:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 104]
        call    rax
        jmp     .LBB47_10
.LBB47_27:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        lea     rdi, [rsp + 96]
        call    rax
        jmp     .LBB47_26
.LBB47_28:
        mov     rdi, qword ptr [rsp + 152]
        call    _Unwind_Resume@PLT
        ud2
.LBB47_29:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::Context::run_task<(),tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>::{{closure}}>@GOTPCREL]
        lea     rdi, [rsp + 80]
        call    rax
        jmp     .LBB47_28

tokio::runtime::basic_scheduler::Context::run_task:
        sub     rsp, 72
        mov     qword ptr [rsp + 8], rdi
        mov     qword ptr [rsp + 24], rsi
        mov     qword ptr [rsp + 32], rdx
        mov     byte ptr [rsp + 55], 0
        mov     byte ptr [rsp + 54], 0
        mov     byte ptr [rsp + 55], 1
        mov     byte ptr [rsp + 54], 1
        mov     rax, qword ptr [rsp + 24]
        mov     qword ptr [rsp + 16], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB48_1
        jmp     .LBB48_2
.LBB48_1:
        mov     rdi, qword ptr [rsp + 16]
        mov     rax, qword ptr [rip + tokio::runtime::metrics::mock::MetricsBatch::incr_poll_count@GOTPCREL]
        call    rax
        jmp     .LBB48_5
.LBB48_2:
        mov     rsi, qword ptr [rsp + 16]
        lea     rdx, [rip + .L__unnamed_21]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB48_3:
        test    byte ptr [rsp + 54], 1
        jne     .LBB48_8
        jmp     .LBB48_7
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 56], rcx
        mov     dword ptr [rsp + 64], eax
        jmp     .LBB48_3
.LBB48_5:
        mov     rdi, qword ptr [rsp + 8]
        mov     byte ptr [rsp + 55], 0
        mov     rsi, qword ptr [rsp + 24]
        mov     byte ptr [rsp + 54], 0
        mov     rax, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 40], rax
        mov     rdx, qword ptr [rsp + 40]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Context::enter@GOTPCREL]
        call    rax
        mov     qword ptr [rsp], rax
        jmp     .LBB48_6
.LBB48_6:
        mov     rax, qword ptr [rsp]
        add     rsp, 72
        ret
.LBB48_7:
        test    byte ptr [rsp + 55], 1
        jne     .LBB48_11
        jmp     .LBB48_10
.LBB48_8:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>@GOTPCREL]
        lea     rdi, [rsp + 32]
        call    rax
        jmp     .LBB48_7
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB48_10:
        mov     rdi, qword ptr [rsp + 56]
        call    _Unwind_Resume@PLT
        ud2
.LBB48_11:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>@GOTPCREL]
        lea     rdi, [rsp + 24]
        call    rax
        jmp     .LBB48_10

tokio::runtime::basic_scheduler::Context::run_task::{{closure}}:
        sub     rsp, 56
        mov     qword ptr [rsp + 8], rdi
        mov     byte ptr [rsp + 23], 0
        mov     byte ptr [rsp + 23], 1
        mov     rax, qword ptr [rip + tokio::coop::Budget::initial@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 6], dl
        mov     byte ptr [rsp + 7], al
        jmp     .LBB49_2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 24], rcx
        mov     dword ptr [rsp + 32], eax
        test    byte ptr [rsp + 23], 1
        jne     .LBB49_4
        jmp     .LBB49_3
.LBB49_2:
        mov     cl, byte ptr [rsp + 6]
        mov     dl, byte ptr [rsp + 7]
        mov     byte ptr [rsp + 23], 0
        mov     rax, qword ptr [rsp + 8]
        and     dl, 1
        mov     byte ptr [rsp + 48], dl
        mov     byte ptr [rsp + 49], cl
        mov     qword ptr [rsp + 40], rax
        lea     rdi, [rip + .L__unnamed_11]
        mov     rax, qword ptr [rip + std::thread::local::LocalKey<T>::with@GOTPCREL]
        lea     rsi, [rsp + 40]
        call    rax
        jmp     .LBB49_6
.LBB49_3:
        mov     rdi, qword ptr [rsp + 24]
        call    _Unwind_Resume@PLT
        ud2
.LBB49_4:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard::block_on<core::pin::Pin<&mut example::main::{{closure}}>>::{{closure}}::{{closure}}>@GOTPCREL]
        lea     rdi, [rsp + 8]
        call    rax
        jmp     .LBB49_3
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB49_6:
        add     rsp, 56
        ret

tokio::runtime::basic_scheduler::CoreGuard::enter:
        sub     rsp, 200
        mov     qword ptr [rsp + 64], rdi
        mov     qword ptr [rsp + 72], rsi
        mov     byte ptr [rsp + 183], 0
        mov     byte ptr [rsp + 182], 0
        mov     byte ptr [rsp + 181], 0
        mov     byte ptr [rsp + 180], 0
        mov     byte ptr [rsp + 183], 1
        add     rdi, 8
        lea     rsi, [rip + .L__unnamed_22]
        mov     rax, qword ptr [rip + core::cell::RefCell<T>::borrow_mut@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 80], rdx
        mov     qword ptr [rsp + 88], rax
        jmp     .LBB50_3
.LBB50_1:
        test    byte ptr [rsp + 183], 1
        jne     .LBB50_31
        jmp     .LBB50_30
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 184], rcx
        mov     dword ptr [rsp + 192], eax
        jmp     .LBB50_1
.LBB50_3:
        mov     rax, qword ptr [rsp + 80]
        mov     rcx, qword ptr [rsp + 88]
        mov     qword ptr [rsp + 104], rcx
        mov     qword ptr [rsp + 112], rax
        mov     rax, qword ptr [rip + <core::cell::RefMut<T> as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        lea     rdi, [rsp + 104]
        call    rax
        mov     qword ptr [rsp + 56], rax
        jmp     .LBB50_6
.LBB50_4:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 104]
        call    rax
        jmp     .LBB50_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 184], rcx
        mov     dword ptr [rsp + 192], eax
        jmp     .LBB50_4
.LBB50_6:
        mov     rdi, qword ptr [rsp + 56]
        mov     rax, qword ptr [rip + core::option::Option<T>::take@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 48], rax
        jmp     .LBB50_7
.LBB50_7:
        mov     rdi, qword ptr [rsp + 48]
        lea     rsi, [rip + .L__unnamed_19]
        lea     rcx, [rip + .L__unnamed_23]
        mov     rax, qword ptr [rip + core::option::Option<T>::expect@GOTPCREL]
        mov     edx, 12
        call    rax
        mov     qword ptr [rsp + 40], rax
        jmp     .LBB50_8
.LBB50_8:
        mov     rax, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 96], rax
        mov     byte ptr [rsp + 182], 1
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 104]
        call    rax
        jmp     .LBB50_11
.LBB50_9:
        test    byte ptr [rsp + 182], 1
        jne     .LBB50_29
        jmp     .LBB50_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 184], rcx
        mov     dword ptr [rsp + 192], eax
        jmp     .LBB50_9
.LBB50_11:
        mov     rsi, qword ptr [rsp + 64]
        mov     rax, qword ptr [rsp + 72]
        mov     byte ptr [rsp + 183], 0
        mov     byte ptr [rsp + 182], 0
        mov     qword ptr [rsp + 128], rax
        mov     rax, qword ptr [rsp + 96]
        mov     qword ptr [rsp + 136], rax
        mov     qword ptr [rsp + 144], rsi
        mov     rdi, qword ptr [rip + tokio::runtime::basic_scheduler::CURRENT@GOTPCREL]
        mov     rax, qword ptr [rip + tokio::macros::scoped_tls::ScopedKey<T>::set@GOTPCREL]
        lea     rdx, [rsp + 128]
        call    rax
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB50_12
.LBB50_12:
        mov     rdi, qword ptr [rsp + 64]
        mov     rax, qword ptr [rsp + 32]
        mov     byte ptr [rsp + 181], 1
        mov     qword ptr [rsp + 120], rax
        mov     byte ptr [rsp + 181], 0
        mov     rax, qword ptr [rsp + 120]
        mov     byte ptr [rsp + 180], 1
        mov     qword ptr [rsp + 152], rax
        add     rdi, 8
        lea     rsi, [rip + .L__unnamed_24]
        mov     rax, qword ptr [rip + core::cell::RefCell<T>::borrow_mut@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 16], rdx
        mov     qword ptr [rsp + 24], rax
        jmp     .LBB50_15
.LBB50_13:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        lea     rdi, [rsp + 152]
        call    rax
        jmp     .LBB50_22
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 184], rcx
        mov     dword ptr [rsp + 192], eax
        jmp     .LBB50_13
.LBB50_15:
        mov     rax, qword ptr [rsp + 16]
        mov     rcx, qword ptr [rsp + 24]
        mov     qword ptr [rsp + 160], rcx
        mov     qword ptr [rsp + 168], rax
        mov     rax, qword ptr [rip + <core::cell::RefMut<T> as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        lea     rdi, [rsp + 160]
        call    rax
        mov     qword ptr [rsp + 8], rax
        jmp     .LBB50_18
.LBB50_16:
        test    byte ptr [rsp + 180], 1
        jne     .LBB50_26
        jmp     .LBB50_25
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 184], rcx
        mov     dword ptr [rsp + 192], eax
        jmp     .LBB50_16
.LBB50_18:
        mov     rdi, qword ptr [rsp + 8]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        call    rax
        jmp     .LBB50_21
.LBB50_19:
        mov     rax, qword ptr [rsp + 8]
        mov     byte ptr [rsp + 180], 0
        mov     rcx, qword ptr [rsp + 152]
        mov     qword ptr [rax], rcx
        jmp     .LBB50_16
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 184], rcx
        mov     dword ptr [rsp + 192], eax
        jmp     .LBB50_19
.LBB50_21:
        mov     rax, qword ptr [rsp + 8]
        mov     byte ptr [rsp + 180], 0
        mov     rcx, qword ptr [rsp + 152]
        mov     qword ptr [rax], rcx
        mov     byte ptr [rsp + 180], 0
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 160]
        call    rax
        jmp     .LBB50_24
.LBB50_22:
        test    byte ptr [rsp + 181], 1
        jne     .LBB50_28
        jmp     .LBB50_9
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 184], rcx
        mov     dword ptr [rsp + 192], eax
        jmp     .LBB50_22
.LBB50_24:
        mov     rdi, qword ptr [rsp + 64]
        mov     byte ptr [rsp + 181], 0
        mov     byte ptr [rsp + 182], 0
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard>@GOTPCREL]
        add     rsp, 200
        ret
.LBB50_25:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::cell::RefMut<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>>@GOTPCREL]
        lea     rdi, [rsp + 160]
        call    rax
        jmp     .LBB50_22
.LBB50_26:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>>@GOTPCREL]
        lea     rdi, [rsp + 152]
        call    rax
        jmp     .LBB50_25
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB50_28:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>@GOTPCREL]
        lea     rdi, [rsp + 120]
        call    rax
        jmp     .LBB50_9
.LBB50_29:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<alloc::boxed::Box<tokio::runtime::basic_scheduler::Core>>@GOTPCREL]
        lea     rdi, [rsp + 96]
        call    rax
        jmp     .LBB50_1
.LBB50_30:
        mov     rdi, qword ptr [rsp + 64]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::CoreGuard>@GOTPCREL]
        call    rax
        jmp     .LBB50_32
.LBB50_31:
        jmp     .LBB50_30
.LBB50_32:
        mov     rdi, qword ptr [rsp + 184]
        call    _Unwind_Resume@PLT
        ud2

tokio::runtime::basic_scheduler::CoreGuard::enter::{{closure}}:
        sub     rsp, 24
        mov     rax, rdi
        mov     rdi, qword ptr [rax]
        mov     rcx, qword ptr [rax + 8]
        mov     rax, qword ptr [rax + 16]
        mov     qword ptr [rsp + 8], rcx
        mov     qword ptr [rsp + 16], rax
        mov     rsi, qword ptr [rsp + 8]
        mov     rdx, qword ptr [rsp + 16]
        call    qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}@GOTPCREL]
        add     rsp, 24
        ret

tokio::runtime::basic_scheduler::CoreGuard::block_on:
        push    rax
        mov     qword ptr [rsp], rsi
        mov     rsi, qword ptr [rsp]
        call    qword ptr [rip + tokio::runtime::basic_scheduler::CoreGuard::enter@GOTPCREL]
        pop     rax
        ret

tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}:
        sub     rsp, 440
        mov     qword ptr [rsp + 232], rdx
        mov     qword ptr [rsp + 240], rdi
        mov     qword ptr [rsp + 248], rsi
        mov     byte ptr [rsp + 413], 0
        mov     byte ptr [rsp + 412], 0
        mov     byte ptr [rsp + 411], 0
        mov     byte ptr [rsp + 415], 0
        mov     byte ptr [rsp + 414], 0
        mov     byte ptr [rsp + 415], 1
        mov     byte ptr [rsp + 413], 1
        mov     byte ptr [rsp + 414], 1
        mov     rax, qword ptr [rip + tokio::runtime::enter::enter@GOTPCREL]
        xor     edi, edi
        call    rax
        jmp     .LBB53_3
.LBB53_1:
        test    byte ptr [rsp + 414], 1
        jne     .LBB53_66
        jmp     .LBB53_65
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 416], rcx
        mov     dword ptr [rsp + 424], eax
        jmp     .LBB53_1
.LBB53_3:
        mov     rdi, qword ptr [rsp + 232]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Spawner::waker_ref@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 216], rdx
        mov     qword ptr [rsp + 224], rax
        jmp     .LBB53_6
.LBB53_4:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 271]
        call    rax
        jmp     .LBB53_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 416], rcx
        mov     dword ptr [rsp + 424], eax
        jmp     .LBB53_4
.LBB53_6:
        mov     rax, qword ptr [rsp + 216]
        mov     rcx, qword ptr [rsp + 224]
        mov     qword ptr [rsp + 272], rcx
        mov     qword ptr [rsp + 280], rax
        mov     rax, qword ptr [rip + <tokio::util::wake::WakerRef as core::ops::deref::Deref>::deref@GOTPCREL]
        lea     rdi, [rsp + 272]
        call    rax
        mov     qword ptr [rsp + 208], rax
        jmp     .LBB53_7
.LBB53_7:
        mov     rdi, qword ptr [rsp + 208]
        call    core::task::wake::Context::from_waker
        mov     qword ptr [rsp + 200], rax
        jmp     .LBB53_8
.LBB53_8:
        mov     rax, qword ptr [rsp + 200]
        mov     qword ptr [rsp + 288], rax
        mov     byte ptr [rsp + 415], 0
        mov     rax, qword ptr [rsp + 240]
        mov     qword ptr [rsp + 296], rax
        lea     rax, [rsp + 296]
        mov     qword ptr [rsp + 432], rax
        mov     rax, qword ptr [rsp + 432]
        mov     qword ptr [rsp + 192], rax
        jmp     .LBB53_11
.LBB53_9:
        jmp     .LBB53_4
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 416], rcx
        mov     dword ptr [rsp + 424], eax
        jmp     .LBB53_9
.LBB53_11:
        mov     rax, qword ptr [rsp + 192]
        mov     qword ptr [rsp + 304], rax
.LBB53_12:
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 184], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_13
        jmp     .LBB53_14
.LBB53_13:
        mov     rdi, qword ptr [rsp + 184]
        add     rdi, 32
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Spawner::reset_woken@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 183], al
        jmp     .LBB53_15
.LBB53_14:
        mov     rsi, qword ptr [rsp + 184]
        lea     rdx, [rip + .L__unnamed_25]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_15:
        mov     al, byte ptr [rsp + 183]
        test    al, 1
        jne     .LBB53_17
        jmp     .LBB53_16
.LBB53_16:
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 168], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_24
        jmp     .LBB53_25
.LBB53_17:
        mov     rdi, qword ptr [rsp + 232]
        mov     byte ptr [rsp + 413], 0
        mov     byte ptr [rsp + 414], 0
        mov     rsi, qword ptr [rsp + 248]
        lea     rax, [rsp + 304]
        mov     qword ptr [rsp + 328], rax
        lea     rax, [rsp + 288]
        mov     qword ptr [rsp + 336], rax
        mov     rdx, qword ptr [rsp + 328]
        mov     rcx, qword ptr [rsp + 336]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Context::enter@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 159], dl
        mov     qword ptr [rsp + 160], rax
        jmp     .LBB53_18
.LBB53_18:
        mov     al, byte ptr [rsp + 159]
        mov     rcx, qword ptr [rsp + 160]
        mov     byte ptr [rsp + 412], 1
        mov     qword ptr [rsp + 312], rcx
        and     al, 1
        mov     byte ptr [rsp + 327], al
        mov     byte ptr [rsp + 412], 0
        mov     rax, qword ptr [rsp + 312]
        mov     byte ptr [rsp + 413], 1
        mov     byte ptr [rsp + 414], 1
        mov     qword ptr [rsp + 248], rax
        mov     al, byte ptr [rsp + 327]
        and     al, 1
        movzx   eax, al
        cmp     rax, 0
        jne     .LBB53_20
        mov     byte ptr [rsp + 413], 0
        mov     byte ptr [rsp + 414], 0
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 256], rax
        mov     byte ptr [rsp + 412], 0
        jmp     .LBB53_21
.LBB53_20:
        jmp     .LBB53_23
.LBB53_21:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::enter::Enter>@GOTPCREL]
        lea     rdi, [rsp + 271]
        call    rax
        jmp     .LBB53_22
.LBB53_22:
        mov     rax, qword ptr [rsp + 256]
        add     rsp, 440
        ret
.LBB53_23:
        mov     byte ptr [rsp + 412], 0
        jmp     .LBB53_16
.LBB53_24:
        mov     rax, qword ptr [rsp + 168]
        mov     eax, dword ptr [rax + 672]
        mov     dword ptr [rsp + 344], 0
        mov     dword ptr [rsp + 348], eax
        mov     edi, dword ptr [rsp + 344]
        mov     esi, dword ptr [rsp + 348]
        mov     rax, qword ptr [rip + <I as core::iter::traits::collect::IntoIterator>::into_iter@GOTPCREL]
        call    rax
        mov     dword ptr [rsp + 148], edx
        mov     dword ptr [rsp + 152], eax
        jmp     .LBB53_26
.LBB53_25:
        mov     rsi, qword ptr [rsp + 168]
        lea     rdx, [rip + .L__unnamed_26]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_26:
        mov     eax, dword ptr [rsp + 148]
        mov     ecx, dword ptr [rsp + 152]
        mov     dword ptr [rsp + 352], ecx
        mov     dword ptr [rsp + 356], eax
.LBB53_27:
        mov     rax, qword ptr [rip + core::iter::range::<impl core::iter::traits::iterator::Iterator for core::ops::range::Range<A>>::next@GOTPCREL]
        lea     rdi, [rsp + 352]
        call    rax
        mov     dword ptr [rsp + 140], edx
        mov     dword ptr [rsp + 144], eax
        jmp     .LBB53_28
.LBB53_28:
        mov     eax, dword ptr [rsp + 140]
        mov     ecx, dword ptr [rsp + 144]
        mov     dword ptr [rsp + 360], ecx
        mov     dword ptr [rsp + 364], eax
        mov     eax, dword ptr [rsp + 360]
        cmp     rax, 0
        jne     .LBB53_30
        mov     rdi, qword ptr [rsp + 232]
        mov     byte ptr [rsp + 413], 0
        mov     byte ptr [rsp + 414], 0
        mov     rsi, qword ptr [rsp + 248]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Context::park_yield@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 128], rax
        jmp     .LBB53_31
.LBB53_30:
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 120], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_32
        jmp     .LBB53_33
.LBB53_31:
        mov     rax, qword ptr [rsp + 128]
        mov     byte ptr [rsp + 413], 1
        mov     byte ptr [rsp + 414], 1
        mov     qword ptr [rsp + 248], rax
        jmp     .LBB53_12
.LBB53_32:
        mov     rax, qword ptr [rsp + 120]
        mov     eax, dword ptr [rax + 664]
        mov     dword ptr [rsp + 108], eax
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 112], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_34
        jmp     .LBB53_35
.LBB53_33:
        mov     rsi, qword ptr [rsp + 120]
        lea     rdx, [rip + .L__unnamed_27]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_34:
        mov     rax, qword ptr [rsp + 112]
        mov     eax, dword ptr [rax + 664]
        add     eax, 1
        mov     dword ptr [rsp + 104], eax
        jmp     .LBB53_36
.LBB53_35:
        mov     rsi, qword ptr [rsp + 112]
        lea     rdx, [rip + .L__unnamed_28]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_36:
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 96], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_37
        jmp     .LBB53_38
.LBB53_37:
        mov     rax, qword ptr [rsp + 96]
        mov     ecx, dword ptr [rsp + 104]
        mov     dword ptr [rax + 664], ecx
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 88], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_39
        jmp     .LBB53_40
.LBB53_38:
        mov     rsi, qword ptr [rsp + 96]
        lea     rdx, [rip + .L__unnamed_29]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_39:
        mov     rax, qword ptr [rsp + 88]
        mov     eax, dword ptr [rax + 668]
        mov     dword ptr [rsp + 84], eax
        cmp     eax, 0
        sete    al
        test    al, 1
        jne     .LBB53_42
        jmp     .LBB53_41
.LBB53_40:
        mov     rsi, qword ptr [rsp + 88]
        lea     rdx, [rip + .L__unnamed_30]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_41:
        mov     ecx, dword ptr [rsp + 84]
        mov     eax, dword ptr [rsp + 108]
        xor     edx, edx
        div     ecx
        cmp     edx, 0
        je      .LBB53_44
        jmp     .LBB53_45
.LBB53_42:
        lea     rdi, [rip + str.0]
        lea     rdx, [rip + .L__unnamed_31]
        mov     rax, qword ptr [rip + core::panicking::panic@GOTPCREL]
        mov     esi, 57
        call    rax
        jmp     .LBB53_43
.LBB53_43:
        ud2
.LBB53_44:
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 72], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_46
        jmp     .LBB53_47
.LBB53_45:
        mov     rax, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 64], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB53_51
        jmp     .LBB53_52
.LBB53_46:
        mov     rdi, qword ptr [rsp + 72]
        add     rdi, 32
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Spawner::pop@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 56], rax
        jmp     .LBB53_48
.LBB53_47:
        mov     rsi, qword ptr [rsp + 72]
        lea     rdx, [rip + .L__unnamed_32]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_48:
        mov     rdi, qword ptr [rsp + 56]
        lea     rax, [rsp + 248]
        mov     qword ptr [rsp + 376], rax
        mov     rsi, qword ptr [rsp + 376]
        mov     rax, qword ptr [rip + core::option::Option<T>::or_else@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 48], rax
        jmp     .LBB53_49
.LBB53_49:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 368], rax
.LBB53_50:
        mov     rdx, qword ptr [rsp + 368]
        mov     eax, 1
        xor     ecx, ecx
        cmp     rdx, 0
        cmove   rax, rcx
        cmp     rax, 0
        je      .LBB53_55
        jmp     .LBB53_56
.LBB53_51:
        mov     rdi, qword ptr [rsp + 64]
        mov     rax, qword ptr [rip + alloc::collections::vec_deque::VecDeque<T,A>::pop_front@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 40], rax
        jmp     .LBB53_53
.LBB53_52:
        mov     rsi, qword ptr [rsp + 64]
        lea     rdx, [rip + .L__unnamed_33]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2
.LBB53_53:
        mov     rdi, qword ptr [rsp + 40]
        lea     rax, [rsp + 248]
        mov     qword ptr [rsp + 384], rax
        mov     rsi, qword ptr [rsp + 384]
        mov     rax, qword ptr [rip + core::option::Option<T>::or_else@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB53_54
.LBB53_54:
        mov     rax, qword ptr [rsp + 32]
        mov     qword ptr [rsp + 368], rax
        jmp     .LBB53_50
.LBB53_55:
        mov     rdi, qword ptr [rsp + 232]
        mov     byte ptr [rsp + 413], 0
        mov     byte ptr [rsp + 414], 0
        mov     rsi, qword ptr [rsp + 248]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Context::park@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 24], rax
        jmp     .LBB53_57
.LBB53_56:
        mov     rdi, qword ptr [rsp + 232]
        mov     rax, qword ptr [rsp + 368]
        mov     byte ptr [rsp + 411], 1
        mov     qword ptr [rsp + 392], rax
        mov     rax, qword ptr [rip + <alloc::sync::Arc<T,A> as core::ops::deref::Deref>::deref@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB53_60
.LBB53_57:
        mov     rax, qword ptr [rsp + 24]
        mov     byte ptr [rsp + 413], 1
        mov     byte ptr [rsp + 414], 1
        mov     qword ptr [rsp + 248], rax
        mov     byte ptr [rsp + 411], 0
        jmp     .LBB53_12
.LBB53_58:
        test    byte ptr [rsp + 411], 1
        jne     .LBB53_63
        jmp     .LBB53_9
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 416], rcx
        mov     dword ptr [rsp + 424], eax
        jmp     .LBB53_58
.LBB53_60:
        mov     rdi, qword ptr [rsp + 16]
        sub     rdi, -128
        mov     byte ptr [rsp + 411], 0
        mov     rsi, qword ptr [rsp + 392]
        mov     rax, qword ptr [rip + tokio::runtime::task::list::OwnedTasks<S>::assert_owner@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 8], rax
        jmp     .LBB53_61
.LBB53_61:
        mov     rdi, qword ptr [rsp + 232]
        mov     rax, qword ptr [rsp + 8]
        mov     byte ptr [rsp + 413], 0
        mov     byte ptr [rsp + 414], 0
        mov     rsi, qword ptr [rsp + 248]
        mov     qword ptr [rsp + 400], rax
        mov     rdx, qword ptr [rsp + 400]
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::Context::run_task@GOTPCREL]
        call    rax
        mov     qword ptr [rsp], rax
        jmp     .LBB53_62
.LBB53_62:
        mov     rax, qword ptr [rsp]
        mov     byte ptr [rsp + 413], 1
        mov     byte ptr [rsp + 414], 1
        mov     qword ptr [rsp + 248], rax
        mov     byte ptr [rsp + 411], 0
        jmp     .LBB53_27
.LBB53_63:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::task::Notified<alloc::sync::Arc<tokio::runtime::basic_scheduler::Shared>>>@GOTPCREL]
        lea     rdi, [rsp + 392]
        call    rax
        jmp     .LBB53_9
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB53_65:
        test    byte ptr [rsp + 414], 1
        jne     .LBB53_68
        jmp     .LBB53_67
.LBB53_66:
        mov     rdi, qword ptr [rsp + 248]
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<alloc::collections::vec_deque::VecDeque<tokio::runtime::task::Notified<alloc::sync::Arc<tokio::runtime::basic_scheduler::Shared>>>>@GOTPCREL]
        call    rax
        jmp     .LBB53_65
.LBB53_67:
        test    byte ptr [rsp + 414], 1
        jne     .LBB53_70
        jmp     .LBB53_69
.LBB53_68:
        mov     rdi, qword ptr [rsp + 248]
        add     rdi, 32
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::basic_scheduler::Spawner>@GOTPCREL]
        call    rax
        jmp     .LBB53_67
.LBB53_69:
        test    byte ptr [rsp + 413], 1
        jne     .LBB53_72
        jmp     .LBB53_71
.LBB53_70:
        mov     rdi, qword ptr [rsp + 248]
        add     rdi, 40
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<core::option::Option<tokio::runtime::driver::Driver>>@GOTPCREL]
        call    rax
        jmp     .LBB53_69
.LBB53_71:
        test    byte ptr [rsp + 415], 1
        jne     .LBB53_75
        jmp     .LBB53_74
.LBB53_72:
        mov     byte ptr [rsp + 413], 0
        mov     rax, qword ptr [rip + <alloc::boxed::Box<T,A> as core::ops::drop::Drop>::drop@GOTPCREL]
        lea     rdi, [rsp + 248]
        call    rax
        jmp     .LBB53_73
.LBB53_73:
        jmp     .LBB53_71
.LBB53_74:
        mov     rdi, qword ptr [rsp + 416]
        call    _Unwind_Resume@PLT
        ud2
.LBB53_75:
        jmp     .LBB53_74

tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}:
        sub     rsp, 24
        mov     qword ptr [rsp + 16], rdi
        mov     rax, qword ptr [rsp + 16]
        mov     rax, qword ptr [rax]
        mov     qword ptr [rsp + 8], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB54_1
        jmp     .LBB54_2
.LBB54_1:
        mov     rdi, qword ptr [rsp + 8]
        add     rdi, 32
        call    qword ptr [rip + tokio::runtime::basic_scheduler::Spawner::pop@GOTPCREL]
        add     rsp, 24
        ret
.LBB54_2:
        mov     rsi, qword ptr [rsp + 8]
        lea     rdx, [rip + .L__unnamed_34]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2

tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}:
        sub     rsp, 120
        mov     qword ptr [rsp + 40], rdi
        mov     qword ptr [rsp + 48], rsi
        mov     rcx, qword ptr [rsp + 40]
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 56], rcx
        mov     qword ptr [rsp + 64], rax
        mov     rax, qword ptr [rsp + 56]
        mov     qword ptr [rsp + 16], rax
        mov     rax, qword ptr [rsp + 64]
        mov     qword ptr [rsp + 24], rax
        mov     byte ptr [rsp + 79], 0
        mov     byte ptr [rsp + 79], 1
        mov     rax, qword ptr [rip + tokio::coop::Budget::initial@GOTPCREL]
        call    rax
        mov     byte ptr [rsp + 38], dl
        mov     byte ptr [rsp + 39], al
        jmp     .LBB55_2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 80], rcx
        mov     dword ptr [rsp + 88], eax
        test    byte ptr [rsp + 79], 1
        jne     .LBB55_4
        jmp     .LBB55_3
.LBB55_2:
        mov     rax, qword ptr [rsp + 24]
        mov     rcx, qword ptr [rsp + 16]
        mov     dl, byte ptr [rsp + 38]
        mov     sil, byte ptr [rsp + 39]
        mov     byte ptr [rsp + 79], 0
        and     sil, 1
        mov     byte ptr [rsp + 112], sil
        mov     byte ptr [rsp + 113], dl
        mov     qword ptr [rsp + 96], rcx
        mov     qword ptr [rsp + 104], rax
        lea     rdi, [rip + .L__unnamed_11]
        mov     rax, qword ptr [rip + std::thread::local::LocalKey<T>::with@GOTPCREL]
        lea     rsi, [rsp + 96]
        call    rax
        mov     byte ptr [rsp + 15], al
        jmp     .LBB55_5
.LBB55_3:
        mov     rdi, qword ptr [rsp + 80]
        call    _Unwind_Resume@PLT
        ud2
.LBB55_4:
        jmp     .LBB55_3
.LBB55_5:
        mov     al, byte ptr [rsp + 15]
        and     al, 1
        movzx   eax, al
        add     rsp, 120
        ret

tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}:
        push    rax
        call    qword ptr [rip + tokio::runtime::task::LocalNotified<S>::run@GOTPCREL]
        pop     rax
        ret

tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}:
        sub     rsp, 24
        mov     qword ptr [rsp + 16], rdi
        mov     rax, qword ptr [rsp + 16]
        mov     rax, qword ptr [rax]
        mov     qword ptr [rsp + 8], rax
        and     rax, 7
        cmp     rax, 0
        sete    al
        test    al, 1
        jne     .LBB57_1
        jmp     .LBB57_2
.LBB57_1:
        mov     rdi, qword ptr [rsp + 8]
        call    qword ptr [rip + alloc::collections::vec_deque::VecDeque<T,A>::pop_front@GOTPCREL]
        add     rsp, 24
        ret
.LBB57_2:
        mov     rsi, qword ptr [rsp + 8]
        lea     rdx, [rip + .L__unnamed_35]
        mov     rax, qword ptr [rip + core::panicking::panic_misaligned_pointer_dereference@GOTPCREL]
        mov     edi, 8
        call    rax
        ud2

tokio::runtime::basic_scheduler::CoreGuard::block_on::{{closure}}::{{closure}}::{{closure}}:
        sub     rsp, 24
        mov     qword ptr [rsp], rdi
        mov     qword ptr [rsp + 8], rsi
        mov     rdi, qword ptr [rsp]
        call    qword ptr [rip + <&mut T as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     qword ptr [rsp + 16], rax
        mov     rdi, qword ptr [rsp + 16]
        mov     rsi, qword ptr [rsp + 8]
        call    qword ptr [rip + <core::pin::Pin<P> as core::future::future::Future>::poll@GOTPCREL]
        and     al, 1
        movzx   eax, al
        add     rsp, 24
        ret

tokio::runtime::task::Notified<S>::header:
        push    rax
        call    qword ptr [rip + tokio::runtime::task::Task<S>::header@GOTPCREL]
        pop     rcx
        ret

tokio::runtime::task::LocalNotified<S>::run:
        push    rax
        mov     qword ptr [rsp], rdi
        call    qword ptr [rip + core::mem::forget@GOTPCREL]
        mov     rdi, qword ptr [rsp]
        call    qword ptr [rip + tokio::runtime::task::raw::RawTask::poll@GOTPCREL]
        pop     rax
        ret

tokio::runtime::task::list::OwnedTasks<S>::assert_owner:
        sub     rsp, 152
        mov     qword ptr [rsp + 24], rdi
        mov     qword ptr [rsp + 40], rsi
        mov     rax, qword ptr [rip + tokio::runtime::task::Notified<S>::header@GOTPCREL]
        lea     rdi, [rsp + 40]
        call    rax
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB61_3
.LBB61_1:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::task::Notified<alloc::sync::Arc<tokio::runtime::basic_scheduler::Shared>>>@GOTPCREL]
        lea     rdi, [rsp + 40]
        call    rax
        jmp     .LBB61_9
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 136], rcx
        mov     dword ptr [rsp + 144], eax
        jmp     .LBB61_1
.LBB61_3:
        mov     rdi, qword ptr [rsp + 32]
        mov     rax, qword ptr [rip + tokio::runtime::task::core::Header::get_owner_id@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB61_4
.LBB61_4:
        mov     rax, qword ptr [rsp + 24]
        mov     rcx, qword ptr [rsp + 16]
        mov     qword ptr [rsp + 72], rcx
        add     rax, 32
        lea     rcx, [rsp + 72]
        mov     qword ptr [rsp + 56], rcx
        mov     qword ptr [rsp + 64], rax
        mov     rax, qword ptr [rsp + 56]
        mov     qword ptr [rsp], rax
        mov     rcx, qword ptr [rsp + 64]
        mov     qword ptr [rsp + 8], rcx
        mov     rax, qword ptr [rax]
        cmp     rax, qword ptr [rcx]
        sete    al
        xor     al, -1
        test    al, 1
        jne     .LBB61_6
        mov     rax, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 48], rax
        mov     rax, qword ptr [rsp + 48]
        add     rsp, 152
        ret
.LBB61_6:
        mov     rdx, qword ptr [rsp + 8]
        mov     rsi, qword ptr [rsp]
        mov     byte ptr [rsp + 87], 0
        mov     qword ptr [rsp + 88], 0
        movzx   edi, byte ptr [rsp + 87]
        lea     r8, [rip + .L__unnamed_36]
        mov     rax, qword ptr [rip + core::panicking::assert_failed@GOTPCREL]
        lea     rcx, [rsp + 88]
        call    rax
        jmp     .LBB61_7
.LBB61_7:
        ud2
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB61_9:
        mov     rdi, qword ptr [rsp + 136]
        call    _Unwind_Resume@PLT
        ud2

tokio::runtime::enter::Enter::block_on:
        sub     rsp, 56
        mov     qword ptr [rsp + 16], rsi
        mov     qword ptr [rsp + 24], rdx
        mov     byte ptr [rsp + 39], 0
        mov     byte ptr [rsp + 39], 1
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::new@GOTPCREL]
        call    rax
        jmp     .LBB62_3
.LBB62_1:
        test    byte ptr [rsp + 39], 1
        jne     .LBB62_6
        jmp     .LBB62_5
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 40], rcx
        mov     dword ptr [rsp + 48], eax
        jmp     .LBB62_1
.LBB62_3:
        mov     rdx, qword ptr [rsp + 24]
        mov     rsi, qword ptr [rsp + 16]
        mov     byte ptr [rsp + 39], 0
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::block_on@GOTPCREL]
        lea     rdi, [rsp + 38]
        call    rax
        mov     byte ptr [rsp + 15], al
        jmp     .LBB62_4
.LBB62_4:
        mov     al, byte ptr [rsp + 15]
        add     rsp, 56
        ret
.LBB62_5:
        mov     rdi, qword ptr [rsp + 40]
        call    _Unwind_Resume@PLT
        ud2
.LBB62_6:
        jmp     .LBB62_5

tokio::runtime::enter::Enter::block_on:
        sub     rsp, 88
        mov     qword ptr [rsp + 16], rsi
        mov     byte ptr [rsp + 71], 0
        mov     byte ptr [rsp + 71], 1
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::new@GOTPCREL]
        call    rax
        jmp     .LBB63_3
.LBB63_1:
        test    byte ptr [rsp + 71], 1
        jne     .LBB63_6
        jmp     .LBB63_5
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 72], rcx
        mov     dword ptr [rsp + 80], eax
        jmp     .LBB63_1
.LBB63_3:
        mov     rax, qword ptr [rsp + 16]
        mov     byte ptr [rsp + 71], 0
        movups  xmm0, xmmword ptr [rax]
        movups  xmm1, xmmword ptr [rax + 16]
        movaps  xmmword ptr [rsp + 48], xmm1
        movaps  xmmword ptr [rsp + 32], xmm0
        mov     rax, qword ptr [rip + tokio::park::thread::CachedParkThread::block_on@GOTPCREL]
        lea     rdi, [rsp + 31]
        lea     rsi, [rsp + 32]
        call    rax
        mov     byte ptr [rsp + 15], al
        jmp     .LBB63_4
.LBB63_4:
        mov     al, byte ptr [rsp + 15]
        and     al, 1
        movzx   eax, al
        add     rsp, 88
        ret
.LBB63_5:
        mov     rdi, qword ptr [rsp + 72]
        call    _Unwind_Resume@PLT
        ud2
.LBB63_6:
        jmp     .LBB63_5

tokio::runtime::Runtime::block_on:
        sub     rsp, 152
        mov     qword ptr [rsp + 16], rdi
        mov     qword ptr [rsp + 24], rsi
        mov     byte ptr [rsp + 135], 0
        mov     byte ptr [rsp + 135], 1
        mov     rax, qword ptr [rip + tokio::runtime::Runtime::enter@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 32], rdx
        mov     qword ptr [rsp + 40], rax
        jmp     .LBB64_3
.LBB64_1:
        test    byte ptr [rsp + 135], 1
        jne     .LBB64_14
        jmp     .LBB64_13
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 136], rcx
        mov     dword ptr [rsp + 144], eax
        jmp     .LBB64_1
.LBB64_3:
        mov     rdx, qword ptr [rsp + 16]
        mov     rax, qword ptr [rsp + 32]
        mov     rcx, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 48], rcx
        mov     qword ptr [rsp + 56], rax
        mov     rax, rdx
        add     rax, 16
        mov     qword ptr [rsp + 8], rax
        xor     eax, eax
        mov     ecx, 1
        cmp     qword ptr [rdx + 16], 4
        cmove   rax, rcx
        cmp     rax, 0
        jne     .LBB64_5
        mov     rdi, qword ptr [rsp + 8]
        mov     rax, qword ptr [rsp + 24]
        mov     byte ptr [rsp + 135], 0
        movups  xmm0, xmmword ptr [rax]
        movups  xmm1, xmmword ptr [rax + 16]
        movaps  xmmword ptr [rsp + 80], xmm1
        movaps  xmmword ptr [rsp + 64], xmm0
        mov     rax, qword ptr [rip + tokio::runtime::basic_scheduler::BasicScheduler::block_on@GOTPCREL]
        lea     rsi, [rsp + 64]
        call    rax
        jmp     .LBB64_8
.LBB64_5:
        mov     rax, qword ptr [rsp + 24]
        mov     rdi, qword ptr [rsp + 8]
        add     rdi, 8
        mov     byte ptr [rsp + 135], 0
        movups  xmm0, xmmword ptr [rax]
        movups  xmm1, xmmword ptr [rax + 16]
        movaps  xmmword ptr [rsp + 112], xmm1
        movaps  xmmword ptr [rsp + 96], xmm0
        mov     rax, qword ptr [rip + tokio::runtime::thread_pool::ThreadPool::block_on@GOTPCREL]
        lea     rsi, [rsp + 96]
        call    rax
        jmp     .LBB64_10
.LBB64_6:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::handle::EnterGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB64_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 136], rcx
        mov     dword ptr [rsp + 144], eax
        jmp     .LBB64_6
.LBB64_8:
        jmp     .LBB64_9
.LBB64_9:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::handle::EnterGuard>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB64_11
.LBB64_10:
        jmp     .LBB64_9
.LBB64_11:
        add     rsp, 152
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB64_13:
        mov     rdi, qword ptr [rsp + 136]
        call    _Unwind_Resume@PLT
        ud2
.LBB64_14:
        jmp     .LBB64_13

<&mut T as core::ops::deref::DerefMut>::deref_mut:
        mov     rax, qword ptr [rdi]
        ret

<&mut T as core::ops::deref::DerefMut>::deref_mut:
        mov     rax, qword ptr [rdi]
        ret

<&mut T as core::ops::deref::DerefMut>::deref_mut:
        mov     rax, qword ptr [rdi]
        ret

<&mut T as core::ops::deref::DerefMut>::deref_mut:
        mov     rax, qword ptr [rdi]
        ret

<core::pin::Pin<P> as core::ops::deref::DerefMut>::deref_mut:
        push    rax
        call    qword ptr [rip + <&mut T as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     qword ptr [rsp], rax
        mov     rax, qword ptr [rsp]
        pop     rcx
        ret

<core::pin::Pin<P> as core::future::future::Future>::poll:
        sub     rsp, 24
        mov     qword ptr [rsp], rsi
        mov     qword ptr [rsp + 8], rdi
        mov     rdi, qword ptr [rsp + 8]
        call    qword ptr [rip + <&mut T as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     rsi, qword ptr [rsp]
        mov     qword ptr [rsp + 16], rax
        mov     rdi, qword ptr [rsp + 16]
        call    example::main::{{closure}}
        and     al, 1
        movzx   eax, al
        add     rsp, 24
        ret

<tokio::future::poll_fn::PollFn<F> as core::future::future::Future>::poll:
        sub     rsp, 24
        mov     qword ptr [rsp], rsi
        mov     qword ptr [rsp + 8], rdi
        lea     rdi, [rsp + 8]
        call    qword ptr [rip + <core::pin::Pin<P> as core::ops::deref::DerefMut>::deref_mut@GOTPCREL]
        mov     rsi, qword ptr [rsp]
        mov     rdi, rax
        mov     qword ptr [rsp + 16], rsi
        mov     rsi, qword ptr [rsp + 16]
        call    qword ptr [rip + tokio::runtime::basic_scheduler::BasicScheduler::block_on::{{closure}}@GOTPCREL]
        add     rsp, 24
        ret

example::square:
        mov     dword ptr [rsp - 8], edi
        mov     byte ptr [rsp - 4], 0
        mov     rax, qword ptr [rsp - 8]
        ret

example::square::{{closure}}:
        sub     rsp, 40
        mov     qword ptr [rsp + 8], rdi
        mov     rax, qword ptr [rsp + 8]
        movzx   eax, byte ptr [rax + 4]
        mov     dword ptr [rsp + 4], eax
        test    eax, eax
        je      .LBB73_2
        jmp     .LBB73_12
.LBB73_12:
        mov     eax, dword ptr [rsp + 4]
        sub     eax, 1
        je      .LBB73_3
        jmp     .LBB73_13
.LBB73_13:
        jmp     .LBB73_4
        ud2
.LBB73_2:
        mov     rax, qword ptr [rsp + 8]
        mov     eax, dword ptr [rax]
        imul    eax, eax
        mov     dword ptr [rsp], eax
        seto    al
        test    al, 1
        jne     .LBB73_6
        jmp     .LBB73_5
.LBB73_3:
        xor     eax, eax
        test    al, 1
        jne     .LBB73_3
        jmp     .LBB73_10
.LBB73_4:
        xor     eax, eax
        test    al, 1
        jne     .LBB73_4
        jmp     .LBB73_11
.LBB73_5:
        mov     eax, dword ptr [rsp]
        mov     dword ptr [rsp + 20], eax
        mov     dword ptr [rsp + 16], 0
        mov     rax, qword ptr [rsp + 8]
        mov     byte ptr [rax + 4], 1
        mov     eax, dword ptr [rsp + 16]
        mov     edx, dword ptr [rsp + 20]
        add     rsp, 40
        ret
.LBB73_6:
        lea     rdi, [rip + str.1]
        lea     rdx, [rip + .L__unnamed_37]
        mov     rax, qword ptr [rip + core::panicking::panic@GOTPCREL]
        mov     esi, 33
        call    rax
        jmp     .LBB73_9
.LBB73_7:
        mov     rax, qword ptr [rsp + 8]
        mov     byte ptr [rax + 4], 2
        mov     rdi, qword ptr [rsp + 24]
        call    _Unwind_Resume@PLT
        ud2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 24], rcx
        mov     dword ptr [rsp + 32], eax
        jmp     .LBB73_7
.LBB73_9:
        ud2
.LBB73_10:
        lea     rdi, [rip + str.2]
        lea     rdx, [rip + .L__unnamed_38]
        mov     rax, qword ptr [rip + core::panicking::panic@GOTPCREL]
        mov     esi, 35
        call    rax
        ud2
.LBB73_11:
        lea     rdi, [rip + str.3]
        lea     rdx, [rip + .L__unnamed_38]
        mov     rax, qword ptr [rip + core::panicking::panic@GOTPCREL]
        mov     esi, 34
        call    rax
        ud2

example::square0:
        push    rax
        imul    edi, edi
        mov     dword ptr [rsp + 4], edi
        seto    al
        test    al, 1
        jne     .LBB74_2
        mov     eax, dword ptr [rsp + 4]
        pop     rcx
        ret
.LBB74_2:
        lea     rdi, [rip + str.1]
        lea     rdx, [rip + .L__unnamed_39]
        mov     rax, qword ptr [rip + core::panicking::panic@GOTPCREL]
        mov     esi, 33
        call    rax
        ud2

example::main:
        sub     rsp, 408
        mov     byte ptr [rsp + 40], 0
        mov     rax, qword ptr [rip + tokio::runtime::builder::Builder::new_multi_thread@GOTPCREL]
        lea     rdi, [rsp + 240]
        mov     qword ptr [rsp], rdi
        call    rax
        mov     rdi, qword ptr [rsp]
        mov     rax, qword ptr [rip + tokio::runtime::builder::Builder::enable_all@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 8], rax
        jmp     .LBB75_3
.LBB75_1:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::builder::Builder>@GOTPCREL]
        lea     rdi, [rsp + 240]
        call    rax
        jmp     .LBB75_11
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 392], rcx
        mov     dword ptr [rsp + 400], eax
        jmp     .LBB75_1
.LBB75_3:
        mov     rsi, qword ptr [rsp + 8]
        mov     rax, qword ptr [rip + tokio::runtime::builder::Builder::build@GOTPCREL]
        lea     rdi, [rsp + 144]
        call    rax
        jmp     .LBB75_4
.LBB75_4:
        lea     rdx, [rip + .L__unnamed_40]
        lea     r8, [rip + .L__unnamed_41]
        mov     rax, qword ptr [rip + core::result::Result<T,E>::expect@GOTPCREL]
        lea     rdi, [rsp + 48]
        lea     rsi, [rsp + 144]
        mov     ecx, 27
        call    rax
        jmp     .LBB75_5
.LBB75_5:
        lea     rdx, [rip + .L__unnamed_41]
        mov     rax, qword ptr [rip + tokio::runtime::Runtime::block_on@GOTPCREL]
        lea     rdi, [rsp + 48]
        lea     rsi, [rsp + 16]
        call    rax
        jmp     .LBB75_8
.LBB75_6:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::Runtime>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB75_1
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 392], rcx
        mov     dword ptr [rsp + 400], eax
        jmp     .LBB75_6
.LBB75_8:
        mov     rax, qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::Runtime>@GOTPCREL]
        lea     rdi, [rsp + 48]
        call    rax
        jmp     .LBB75_9
.LBB75_9:
        lea     rdi, [rsp + 240]
        call    qword ptr [rip + core::ptr::drop_in_place<tokio::runtime::builder::Builder>@GOTPCREL]
        add     rsp, 408
        ret
        mov     rax, qword ptr [rip + core::panicking::panic_cannot_unwind@GOTPCREL]
        call    rax
        ud2
.LBB75_11:
        mov     rdi, qword ptr [rsp + 392]
        call    _Unwind_Resume@PLT
        ud2

example::main::{{closure}}:
        sub     rsp, 248
        mov     qword ptr [rsp + 56], rsi
        mov     qword ptr [rsp + 72], rdi
        mov     rax, qword ptr [rsp + 72]
        movzx   eax, byte ptr [rax + 24]
        mov     qword ptr [rsp + 64], rax
        mov     rax, qword ptr [rsp + 64]
        lea     rcx, [rip + .LJTI76_0]
        movsxd  rax, dword ptr [rcx + 4*rax]
        add     rax, rcx
        jmp     rax
        ud2
.LBB76_2:
        mov     rax, qword ptr [rsp + 56]
        mov     qword ptr [rsp + 184], rax
        mov     rax, qword ptr [rsp + 72]
        lea     rcx, [rip + .L__unnamed_42]
        mov     qword ptr [rax], rcx
        mov     qword ptr [rax + 8], 2
        mov     rax, qword ptr [rip + example::square@GOTPCREL]
        mov     edi, 2
        call    rax
        mov     qword ptr [rsp + 48], rax
        jmp     .LBB76_8
.LBB76_3:
        xor     eax, eax
        test    al, 1
        jne     .LBB76_3
        jmp     .LBB76_11
.LBB76_4:
        xor     eax, eax
        test    al, 1
        jne     .LBB76_4
        jmp     .LBB76_12
.LBB76_5:
        mov     rax, qword ptr [rsp + 56]
        mov     qword ptr [rsp + 184], rax
        jmp     .LBB76_10
.LBB76_6:
        mov     rax, qword ptr [rsp + 72]
        mov     byte ptr [rax + 24], 2
        mov     rdi, qword ptr [rsp + 192]
        call    _Unwind_Resume@PLT
        ud2
        mov     rcx, rax
        mov     eax, edx
        mov     qword ptr [rsp + 192], rcx
        mov     dword ptr [rsp + 200], eax
        jmp     .LBB76_6
.LBB76_8:
        mov     rax, qword ptr [rsp + 48]
        mov     qword ptr [rsp + 208], rax
        mov     rax, qword ptr [rsp + 208]
        mov     qword ptr [rsp + 168], rax
        mov     rdi, qword ptr [rsp + 168]
        mov     rax, qword ptr [rip + <F as core::future::into_future::IntoFuture>::into_future@GOTPCREL]
        call    rax
        mov     qword ptr [rsp + 40], rax
        jmp     .LBB76_9
.LBB76_9:
        mov     rax, qword ptr [rsp + 40]
        mov     qword ptr [rsp + 216], rax
        mov     rax, qword ptr [rsp + 216]
        mov     qword ptr [rsp + 160], rax
        mov     rax, qword ptr [rsp + 72]
        mov     rcx, qword ptr [rsp + 160]
        mov     qword ptr [rax + 16], rcx
.LBB76_10:
        mov     rax, qword ptr [rsp + 72]
        add     rax, 16
        mov     qword ptr [rsp + 240], rax
        mov     rax, qword ptr [rsp + 240]
        mov     qword ptr [rsp + 32], rax
        jmp     .LBB76_13
.LBB76_11:
        lea     rdi, [rip + str.2]
        lea     rdx, [rip + .L__unnamed_43]
        mov     rax, qword ptr [rip + core::panicking::panic@GOTPCREL]
        mov     esi, 35
        call    rax
        ud2
.LBB76_12:
        lea     rdi, [rip + str.3]
        lea     rdx, [rip + .L__unnamed_43]
        mov     rax, qword ptr [rip + core::panicking::panic@GOTPCREL]
        mov     esi, 34
        call    rax
        ud2
.LBB76_13:
        mov     rdi, qword ptr [rsp + 32]
        mov     rsi, qword ptr [rsp + 184]
        mov     rax, qword ptr [rip + example::square::{{closure}}@GOTPCREL]
        call    rax
        mov     dword ptr [rsp + 24], edx
        mov     dword ptr [rsp + 28], eax
        jmp     .LBB76_14
.LBB76_14:
        mov     eax, dword ptr [rsp + 24]
        mov     ecx, dword ptr [rsp + 28]
        mov     dword ptr [rsp + 176], ecx
        mov     dword ptr [rsp + 180], eax
        mov     eax, dword ptr [rsp + 176]
        cmp     rax, 0
        jne     .LBB76_16
        mov     eax, dword ptr [rsp + 180]
        mov     dword ptr [rsp + 156], eax
        lea     rax, [rsp + 156]
        mov     qword ptr [rsp + 224], rax
        mov     rax, qword ptr [rip + core::fmt::num::imp::<impl core::fmt::Display for i32>::fmt@GOTPCREL]
        mov     qword ptr [rsp + 232], rax
        mov     rax, qword ptr [rsp + 224]
        mov     qword ptr [rsp + 8], rax
        mov     rax, qword ptr [rsp + 232]
        mov     qword ptr [rsp + 16], rax
        jmp     .LBB76_17
.LBB76_16:
        mov     byte ptr [rsp + 87], 1
        mov     rax, qword ptr [rsp + 72]
        mov     byte ptr [rax + 24], 3
        mov     al, byte ptr [rsp + 87]
        and     al, 1
        movzx   eax, al
        add     rsp, 248
        ret
.LBB76_17:
        mov     rax, qword ptr [rsp + 16]
        mov     rcx, qword ptr [rsp + 8]
        mov     qword ptr [rsp + 136], rcx
        mov     qword ptr [rsp + 144], rax
        mov     rax, qword ptr [rsp + 72]
        mov     rsi, qword ptr [rax]
        mov     rdx, qword ptr [rax + 8]
        lea     rdi, [rsp + 88]
        lea     rcx, [rsp + 136]
        mov     r8d, 1
        call    core::fmt::Arguments::new_v1
        jmp     .LBB76_18
.LBB76_18:
        mov     rax, qword ptr [rip + std::io::stdio::_print@GOTPCREL]
        lea     rdi, [rsp + 88]
        call    rax
        jmp     .LBB76_19
.LBB76_19:
        mov     byte ptr [rsp + 87], 0
        mov     rax, qword ptr [rsp + 72]
        mov     byte ptr [rax + 24], 1
        mov     al, byte ptr [rsp + 87]
        and     al, 1
        movzx   eax, al
        add     rsp, 248
        ret
.LJTI76_0:
        .long   .LBB76_2-.LJTI76_0
        .long   .LBB76_3-.LJTI76_0
        .long   .LBB76_4-.LJTI76_0
        .long   .LBB76_5-.LJTI76_0

.L__unnamed_1:
        .ascii  "cannot access a Thread Local Storage value during or after destruction"

.L__unnamed_44:
        .ascii  "/rustc/cc66ad468955717ab92600c770da8c1601a4ff33/library/std/src/thread/local.rs"

.L__unnamed_2:
        .quad   .L__unnamed_44
        .asciz  "O\000\000\000\000\000\000\000\366\000\000\000\032\000\000"

.L__unnamed_3:
        .ascii  "()"

.L__unnamed_45:
        .ascii  "invalid args"

.L__unnamed_4:
        .quad   .L__unnamed_45
        .asciz  "\f\000\000\000\000\000\000"

.L__unnamed_5:

.L__unnamed_46:
        .ascii  "/rustc/cc66ad468955717ab92600c770da8c1601a4ff33/library/core/src/fmt/mod.rs"

.L__unnamed_6:
        .quad   .L__unnamed_46
        .asciz  "K\000\000\000\000\000\000\0005\001\000\000\r\000\000"

.L__unnamed_7:
        .quad   core::ptr::drop_in_place<()>
        .asciz  "\000\000\000\000\000\000\000\000\001\000\000\000\000\000\000"
        .quad   <() as core::fmt::Debug>::fmt

.L__unnamed_8:
        .quad   core::ptr::drop_in_place<std::thread::local::AccessError>
        .asciz  "\000\000\000\000\000\000\000\000\001\000\000\000\000\000\000"
        .quad   <std::thread::local::AccessError as core::fmt::Debug>::fmt

.L__unnamed_9:
        .quad   core::ptr::drop_in_place<std::io::error::Error>
        .asciz  "\b\000\000\000\000\000\000\000\b\000\000\000\000\000\000"
        .quad   <std::io::error::Error as core::fmt::Debug>::fmt

.L__unnamed_11:
        .quad   tokio::coop::CURRENT::__getit

.L__unnamed_47:
        .ascii  "/tmp/staging/a2fb4540-0f42-482c-bb27-922f30f3493b/crate_tokio_1.19.2/src/park/thread.rs"

.L__unnamed_12:
        .quad   .L__unnamed_47
        .asciz  "W\000\000\000\000\000\000\000\013\001\000\000\r\000\000"

.L__unnamed_10:
        .quad   .L__unnamed_47
        .asciz  "W\000\000\000\000\000\000\000\001\001\000\000\025\000\000"

.L__unnamed_13:
        .ascii  "failed to park thread"

.L__unnamed_48:
        .ascii  "/tmp/staging/a2fb4540-0f42-482c-bb27-922f30f3493b/crate_tokio_1.19.2/src/runtime/thread_pool/mod.rs"

.L__unnamed_14:
        .quad   .L__unnamed_48
        .asciz  "c\000\000\000\000\000\000\000Z\000\000\000 \000\000"

.L__unnamed_15:
        .ascii  "Failed to `Enter::block_on`"

.L__unnamed_49:
        .ascii  "/tmp/staging/a2fb4540-0f42-482c-bb27-922f30f3493b/crate_tokio_1.19.2/src/runtime/basic_scheduler.rs"

.L__unnamed_16:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\301\000\000\000\026\000\000"

.L__unnamed_17:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000g\001\000\000\024\000\000"

.L__unnamed_18:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000m\001\000\000\036\000\000"

.L__unnamed_19:
        .ascii  "core missing"

.L__unnamed_20:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000m\001\000\0002\000\000"

.L__unnamed_21:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000(\001\000\000\t\000\000"

.L__unnamed_22:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\0002\002\000\000&\000\000"

.L__unnamed_23:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\0002\002\000\000:\000\000"

.L__unnamed_24:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\0007\002\000\000\034\000\000"

.L__unnamed_25:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\372\001\000\000\024\000\000"

.L__unnamed_26:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\006\002\000\000\035\000\000"

.L__unnamed_27:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\b\002\000\000 \000\000"

.L__unnamed_28:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\t\002\000\000!\000\000"

.L__unnamed_29:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\t\002\000\000\025\000\000"

.L__unnamed_30:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\013\002\000\000+\000\000"

.L__unnamed_31:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\013\002\000\000$\000\000"

str.0:
        .ascii  "attempt to calculate the remainder with a divisor of zero"

.L__unnamed_32:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\f\002\000\000\031\000\000"

.L__unnamed_33:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\016\002\000\000\031\000\000"

.L__unnamed_34:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\016\002\000\000;\000\000"

.L__unnamed_35:
        .quad   .L__unnamed_49
        .asciz  "c\000\000\000\000\000\000\000\f\002\000\0007\000\000"

.L__unnamed_50:
        .ascii  "/tmp/staging/a2fb4540-0f42-482c-bb27-922f30f3493b/crate_tokio_1.19.2/src/runtime/task/list.rs"

.L__unnamed_36:
        .quad   .L__unnamed_50
        .asciz  "]\000\000\000\000\000\000\000v\000\000\000\t\000\000"

.L__unnamed_51:
        .ascii  "/app/example.rs"

.L__unnamed_37:
        .quad   .L__unnamed_51
        .asciz  "\017\000\000\000\000\000\000\000\003\000\000\000\005\000\000"

str.1:
        .ascii  "attempt to multiply with overflow"

.L__unnamed_38:
        .quad   .L__unnamed_51
        .asciz  "\017\000\000\000\000\000\000\000\002\000\000\000&\000\000"

str.2:
        .ascii  "`async fn` resumed after completion"

str.3:
        .ascii  "`async fn` resumed after panicking"

.L__unnamed_39:
        .quad   .L__unnamed_51
        .asciz  "\017\000\000\000\000\000\000\000\007\000\000\000\005\000\000"

.L__unnamed_40:
        .ascii  "Failed building the Runtime"

.L__unnamed_41:
        .quad   .L__unnamed_51
        .asciz  "\017\000\000\000\000\000\000\000\r\000\000\000$\000\000"

.L__unnamed_52:
        .byte   10

.L__unnamed_42:
        .quad   .L__unnamed_5
        .zero   8
        .quad   .L__unnamed_52
        .asciz  "\001\000\000\000\000\000\000"

.L__unnamed_43:
        .quad   .L__unnamed_51
        .asciz  "\017\000\000\000\000\000\000\000\013\000\000\000\001\000\000"

DW.ref.rust_eh_personality:
        .quad   rust_eh_personality
```