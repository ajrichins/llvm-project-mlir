# Testing generalization of peephole optimizations in MLIR

experimenting in test branch using either tablegen DRR or the pdl dialect to generalize peephole optimizations in various mlir dialects. Mostly looking into arith and affine dialects, but open to others with the goal of greater impact on MLIR use cases.



# BUILD AND TESTING (kinda)

from mlir getting started page kept here for convienince

cd llvm-project-mlir/build
cmake -G Ninja ../llvm \
   -DLLVM_ENABLE_PROJECTS=mlir \
   -DLLVM_BUILD_EXAMPLES=ON \
   -DLLVM_TARGETS_TO_BUILD="Native;NVPTX;AMDGPU" \
   -DCMAKE_BUILD_TYPE=Release \
   -DLLVM_ENABLE_ASSERTIONS=ON
   
Using clang and lld speeds up the build, we recommend adding:
-DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++ -DLLVM_ENABLE_LLD=ON
CCache can drastically speed up further rebuilds, try adding:
-DLLVM_CCACHE_BUILD=ON
Optionally, using ASAN/UBSAN can find bugs early in development, enable with:
-DLLVM_USE_SANITIZER="Address;Undefined" 
Optionally, enabling integration tests as well
-DMLIR_INCLUDE_INTEGRATION_TESTS=ON

cmake --build . --target check-mlir





# The LLVM Compiler Infrastructure

Welcome to the LLVM project!

This repository contains the source code for LLVM, a toolkit for the
construction of highly optimized compilers, optimizers, and run-time
environments.

The LLVM project has multiple components. The core of the project is
itself called "LLVM". This contains all of the tools, libraries, and header
files needed to process intermediate representations and convert them into
object files. Tools include an assembler, disassembler, bitcode analyzer, and
bitcode optimizer.

C-like languages use the [Clang](http://clang.llvm.org/) frontend. This
component compiles C, C++, Objective-C, and Objective-C++ code into LLVM bitcode
-- and from there into object files, using LLVM.

Other components include:
the [libc++ C++ standard library](https://libcxx.llvm.org),
the [LLD linker](https://lld.llvm.org), and more.

## Getting the Source Code and Building LLVM

Consult the
[Getting Started with LLVM](https://llvm.org/docs/GettingStarted.html#getting-the-source-code-and-building-llvm)
page for information on building and running LLVM.

For information on how to contribute to the LLVM project, please take a look at
the [Contributing to LLVM](https://llvm.org/docs/Contributing.html) guide.

## Getting in touch

Join the [LLVM Discourse forums](https://discourse.llvm.org/), [Discord
chat](https://discord.gg/xS7Z362), or #llvm IRC channel on
[OFTC](https://oftc.net/).

The LLVM project has adopted a [code of conduct](https://llvm.org/docs/CodeOfConduct.html) for
participants to all modes of communication within the project.
