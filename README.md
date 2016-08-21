Spero Language

Spero is a new compiled, statically typed language that I've taken to creating to learn more about modern type 
systems, the process of compilation, and more.


The Spero project also contains three sub-projects: speroc, Spark, and vs-spero

    speroc - Spero reference compiler. Unknown implementation language

    Spark - Spero build/dependency manager. Initial development will be done in Rust
    
    vs-spero - VS Code extension that adds Spero support


## Current Todo List:

    1) Fix the dot-flipping/indexing syntax issue
    2) Settle on the syntax for declaring functions with arguments
    3) Work on the module import syntax and semantics
    4) Collect all current contexts and keywords in a list
    5) Figure out how arrays will be handled
        - Slice/view versus array as the language intrinsic
        - Syntax for array literals and function arguments
        - Determine if I should allow variable arguments
    6) Work on OOP syntax and type relationships
    7) Look into parametric semantics and syntax
        - Dependent typing (yes/no)?
        - What are the possibilities in parametrics?
        - Parametrics as implicit first argument?
    8) Make some quick metaprogramming doodles

## Icon at https://www.iconfinder.com/icons/606025/ancient_antique_historic_roman_rome_helmet_vintage_warrior_icon