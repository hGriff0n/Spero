Spero Language

Spero is a new compiled, statically typed language that I've taken to creating to learn more about modern type 
systems, the process of compilation, and more.


The Spero project also contains three sub-projects: speroc, Spark, and vs-spero

    speroc - Spero reference compiler. Unknown implementation language

    Spark - Spero build/dependency manager. Initial development will be done in Rust
    
    vs-spero - VS Code extension that adds Spero support


## Current Todo List:

    1) Work on the module import syntax and semantics
    2) Collect all current contexts and keywords in a list
    3) Determine if I should allow variable arguments
    4) Work on the type system
    5) Decide on concurrency support
        - Do I want to go full event-based (wouldn't need main then)
    6) Start working on implementation details


## Some example programs

    # Hello World (main might be unnecessary)
    def main = () -> "Hello World!".println


Icon at ww.iconfinder.com/icons/606025/ancient_antique_historic_roman_rome_helmet_vintage_warrior_icon