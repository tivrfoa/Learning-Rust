
```
│  > 0x7ffff7c9f820 <__aio_write>            endbr64
│    0x7ffff7c9f824 <__aio_write+4>          sub    $0x8,%rsp
│    0x7ffff7c9f828 <__aio_write+8>          mov    $0x1,%esi
│    0x7ffff7c9f82d <__aio_write+13>         call   0x7ffff7c9e7b0 <__aio_enqueue_request>
│    0x7ffff7c9f832 <__aio_write+18>         cmp    $0x1,%rax
│    0x7ffff7c9f836 <__aio_write+22>         sbb    %eax,%eax
│    0x7ffff7c9f838 <__aio_write+24>         add    $0x8,%rsp
│    0x7ffff7c9f83c <__aio_write+28>         ret
│    0x7ffff7c9f83d                          nopl   (%rax)
│    0x7ffff7c9f840 <lio_listio_internal>    push   %rbp
│    0x7ffff7c9f841 <lio_listio_internal+1>  mov    %rsp,%rbp
│    0x7ffff7c9f844 <lio_listio_internal+4>  push   %r15
│    0x7ffff7c9f846 <lio_listio_internal+6>  mov    %rsi,%r15
│    0x7ffff7c9f849 <lio_listio_internal+9>  push   %r14
│    0x7ffff7c9f84b <lio_listio_internal+11> push   %r13
│    0x7ffff7c9f84d <lio_listio_internal+13> push   %r12
│    0x7ffff7c9f84f <lio_listio_internal+15> movslq %edx,%r12
│    0x7ffff7c9f852 <lio_listio_internal+18> push   %rbx
│    0x7ffff7c9f853 <lio_listio_internal+19> sub    $0x88,%rsp
│    0x7ffff7c9f85a <lio_listio_internal+26> mov    %edx,-0xa4(%rbp)
│    0x7ffff7c9f860 <lio_listio_internal+32> mov    %edi,-0xa8(%rbp)
│    0x7ffff7c9f866 <lio_listio_internal+38> mov    %rsp,%rsi
```

# aio_enqueue_request



