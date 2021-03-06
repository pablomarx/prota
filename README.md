# Prota

An implementation of NewtonScript

I wrote this in 1997. It got to this point before I got distracted by other
things. :) I originally called it "Proto" and got about halfway through changing
it to "Prota".

It implements

* The basic NewtonScript object model
* A NewtonScript interpreter (missing floating point and a few other niceties)
* A package stream reader (no writer)
* A printer

It does *not* implement

* A NewtonScript compiler (I used NTK to compile the initial objects and the
interpreter test programs, which is why you'll see NTK files here.)
* An object store
* A UI system
* Any other Newton technology :)

I used the Boehm conservative garbage collection library for memory management
rather than the error-prone `RefVar` system used for precise GC in the Newton
OS. There might be a nicer way to do this in C++ now, but I haven't written any
serious C++ in this century. :)

This was last compiled in MS Visual C++ in 1997. I have it working on OS X (clang)
in 2017. At least, it compiles and does *something*. :)

BTW, this is pretty close to what the original NewtonScript source code looks
like. My style didn't change much in six years.

## Build instructions

    # required once
    git clone https://github.com/ivmai/bdwgc.git
    cd bdwgc
    git clone git://github.com/ivmai/libatomic_ops.git
    make -f Makefile.direct ABI_FLAG=-m32
    cd ..

    # then
    make
    cd test
    ../build/nstest
