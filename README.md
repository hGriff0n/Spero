# Spero Language

Spero is a simple, statically typed systmes-level programming language that aims to provide performant and flexible coding within a framework that minimizes cognitive load. It is a multi-paradigm language that places particular emphasis on encouraging the use of functional and OOP styles.

The development of Spero began as an effort to better understand modern type systems (particularly type inference) and the entire process of compilation, from source to assembly. It quickly morphed into a much bigger project requiring the design of a standard library, a build/dependency manager, etc.

So here's Hello World!

    def main = () -> "Hello World!".std:io:println

## What's Unique with Spero

Spero provides no special syntax for definining functions, and only a little extra with types, instead relying entirely on type inference and literals.

Inspirations: C++, Rust, Scala, Haskell, Python

### What thinks do I need to introduce?

    0) What's unique about Spero
    1) Assignment syntax is the same for functions, types, anything
    2) Visibility keywords
    3) Mutability restrictions
    4) Basic control flow
    5) OOP dot-flipping
    6) References
    7) Custom Types (including ADT)
    8) Pattern Matching
    9) Generics (Dependent Types)
    10) Some interesting things we can do with Spero


The Spero project also contains four sub-projects: speroc, spero-std, Spark, and vs-spero

    speroc - Spero reference compiler, currently implemented in C++
    spero-std - Spero-only code for the spero standard library (non-compiler intrinsics)
    Spark - Spero build/dependency manager. Initial development will be done in Rust
    vs-spero - VS Code extension that adds Spero support


## Current Todo List:

    1) Create executables with speroc
    2) Designing the type system
    3) Deciding on concurrency model
    4) Formalizing language documentation
    5) Figure out how modules will be implemented
    6) Planning out the standard library
    



Icon at www.iconfinder.com/icons/606025/ancient_antique_historic_roman_rome_helmet_vintage_warrior_icon