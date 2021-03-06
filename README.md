# LLVM slicer

## Introduction
This is a static slicer based on the Mark Weiser's algorithm in [1]. It is
augmented to perform an inter-procedural analysis. The initial criteria
considered here are all assert_fail function calls (which is effectively every
place where an assert is in the code).

## HOWTO
```bash
$ git clone https://github.com/Justme0/LLVMSlicer.git
$ cd LLVMSlicer
$ make
$ cd test
$ ./test.rb --file example.c
```

IR files are example.ll and example_sliced.ll.

Or you can run slicing manually. Basically, what one needs to do to slice src.o LLVM code into dst.o is:
```bash
$ opt -load LLVMSlicer.so -create-hammock-cfg -slice-inter src.o -o dst.o
```

Both create-hammock-cfg and slice-inter are defined in this project. If you are
having troubles with running opt, you are likely not loading the proper library.
Of course, you have to make sure that the library is in a path where dynamic
libraries are looked for (or add the path where the library is to
LD_LIBRARY_PATH).

## Bug reports
Use github for reports and pull requests, please.

## Contacts
Justme0 <jiangg2012@hotmail.com>
http://justme0.com

Jiri Slaby <jirislaby@gmail.com>
https://github.com/jirislaby/LLVMSlicer

## References
[1] M. Weiser. "Program slicing". Proceedings of the 5th International
Conference on Software Engineering, pages 439–449, IEEE Computer Society Press,
March 1981.
