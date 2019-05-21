This directory contains the core source code for Empirical. Broadly speaking, the Empirical compiler emits bytecode for the Vector Virtual Machine (`VVM/`). This process follows a common compiler pipeline:

 - `parse.cpp`: analyzes user code according to Empirical's concrete syntax definition (`Empirical.g4`) and emits an abstract syntax tree (`AST.asdl`)
 - `sema.cpp`: checks types and resolves identifiers to emit the high-level intermediary representation (`HIR.asdl`)
 - `codegen.cpp`: generates bytecode for VVM

The pipeline is driven by `main.cpp` and is supported by these headers:

 - `empirical.hpp`: function declarations that represent the above stages of the compiler
 - `linenoise.hpp`: wrapper to antirez's *linenoise* library
 - `string_helpers.hpp`: some text-handling routines

Any Empirical header file that ends with `.h` is generated by either ANTLR or ASDL and will be found in `build/`.