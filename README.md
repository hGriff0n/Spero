Spero Language

Spero is a new compiled, statically typed language that I've taken to creating to learn more about modern type 
systems, the process of compilation, and more.


The Spero project also contains four sub-projects: speroc, spero-std, Spark, and vs-spero

    speroc - Spero reference compiler. Unknown implementation language
    spero-std - The implementation for the spero standard library
    Spark - Spero build/dependency manager. Initial development will be done in Rust
    vs-spero - VS Code extension that adds Spero support


## Current Todo List:

    1) Create executables with speroc
    2) Designing the type system
    3) Deciding on concurrency model
    4) Formalizing language documentation
    5) Figure out how modules will be implemented
    6) Planning out the standard library
    

## Some example programs

    # Hello World
    def main = () -> "Hello World!".std:io:println


Icon at ww.iconfinder.com/icons/606025/ancient_antique_historic_roman_rome_helmet_vintage_warrior_icon