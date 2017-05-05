# Spero Language

Spero is a simple, statically typed systmes-level programming language that aims to provide performant and flexible coding within a framework that minimizes cognitive load. It is a multi-paradigm language that places particular emphasis on encouraging the use of functional and OOP styles.

The development of Spero began as an effort to better understand modern type systems (particularly type inference) and the entire process of compilation, from source to assembly. It quickly morphed into a much bigger project requiring the design of a standard library, a build/dependency manager, etc. The full projects are as follows:

    speroc - Spero reference compiler, currently implemented in C++ (TODO: Add in build status?)
    spero-std - Spero-only code for the spero standard library (non-compiler intrinsics)
    Spark - Spero build/dependency manager. Initial development will be done in Rust
    vs-spero - VS Code extension that adds Spero syntax highlighting

Spero started off as an attempt to take the style and benefits of Rust and Scala, two languages I admire and enjoy, and combine them with the flexibility of C++, the language I've used the most. My goal is to have the security of Rust with the syntax and type system of Scala, topped off with the power of C++. To that end, I've also taken some ideas and idioms from Ruby, Haskell, and even Coq, so long as they follow the Spero spirit.

    def main = () -> "Hello World!".std:io:println

# What's Unique with Spero

For the moment, much of what is unique in Spero lies in syntax, particularly in the focus taken to use as little as possible. Almost every character has its use and pain is taken to not duplicate these fields, or require extraneous information, where possible. This is most easily seen in the assignment syntax, how similar it is across functions, types, and almost any Spero construct.

    let Foo[T] = { ## ... ## }
    def bar = (f :: Foo[Int]) -> f.call + var
    static var[V] = 3.V

The compiler distinquishes between these three cases based on their context alone, no need for any special "fn" keyword, just use type inference. There is a small concession in the case of types due to some difficulties in acquiring the necessary context. The first letter of all types must be capitalized but as this is a common styling guide across many languages, I feel that this enforcement ultimately strengthens the code.

Spero also seeks to eliminate the duplication of keywords present in many functional languages that is a byproduct of having a single keyword for declaring variables. To combat this, Spero instead uses 3 keywords, although slightly tweaking their meaning: 'def' is publicly visible, 'let' is protected, and 'static' is, well, static. No more need for "public fn" or "public var", just code what feels right.

    let bar = 3
    # bar += 3      <- `bar` is immutable
    let bar = mut bar
    bar += 3        # Can now perform the mutation

At some level it is impractical for this to be carried out to all contexts, particularly once mutability is involved. Here Spero takes the standpoint that mutability is a property of the value and the type, not the variable, even to the point of not making all type members mutable when the type instance is. The 'mut' keyword, which signifies mutability, is placed to the right of the assignment, with the value, except in the specific case of pattern matching (by necessity). Nautrally, mutability is analyzed at every assignment to ensure that accidentally changing values is not possible.

## Control Flow

Spero makes special exception to allow for many imperative constructs, even though the language feel leans towards declarative styling. Basic keywords like <code>if, while, for, loop, break, return</code> are used to structure execution flow. The possibility for coroutine support exists through the <code>yield, wait</code> keywords, but I have some difficulty resolving the exact process for how these functions would work in all contexts.

    let arr = [ 1, 2, 34, 5 ]
    let i = mut 0
    while i < arr.len do
        "{}".println(i.arr)

While Spero takes a lot of influence from the functional programming realm, traditional OOP programming, where functions are called as "methods" on a value instance, plays a fundamental role in Spero code through a process I've taken to calling "dot-flipping" -though you may know it better as D and C++'s "Universal Call Syntax". Dot flipping allows for functions to be used in both OOP and function styles, but it is particularly important as a way for allowing types to be "extended" post-hoc, a characteristic normally reserved to the functional mode.

Taking a page from Ruby, Spero extends dot-flipping to several of the control flow keywords, where it makes sense to do so. This usage of dot-flipping allows for the control statement to come after its body of code, allowing for more intuitive readings (as is the goal in Ruby). The usage of the dot character serves to unify this syling into the wider language feel and (particularly for me) grammar.

## Type System

Given that Rust, Scala, and Coq are some of my influences with Spero, the type system plays a large and deep role in the language (though I haven't put a lot of work into it for the moment). Defining custom types is fairly trivial, type name and generics to the left, constructors and type body (scope) to the right of the '='. "Named constructors", special constructors that utilize "type names", are Spero's way of including Abstract Data Types (ADTs) within the system. These types are particularly useful for distinquishing instances and forcing error handling, etc. in connection with pattern matching.

    def Option[T+] = Some(T) | None {
        def get = self.match {
            case Some(t) -> t
        }
    }

Methods can still be defined on these ADT types, though they must use 'match statements' to access any of the hidden values. We can see a bit of Spero's generics system in this example and generics are probably the area where Spero takes its biggest step away from Rust and Scala (although it is partially motivated by C++). The basic type styling and capabilities largely follow directly from Scala's usage (with the syntax from Rust), going so far as to include specific variance annotations, but Spero aims to supplement these types with value generics, allowing for dependent typing and hopefully some interesting systems (like coeffects, etc.).

The actual capabilities are still somewhat up in the air, though the raw idea is largely settled. This is very unlike the current case for inheritance, for tying together the type system in a useful, polymorphic way. Currently Spero takes on a compromised position between standard OOP style inheritance and Rust's impl-composition, slightly favoring inheritance. However, I've been taking a bigger fancy towards Rust's style, particularly as a means of constraining and empowering dot-flip extensions, though this still represents an issue with abstraction and data-hiding.

    impl Serializable for Option[T :: Serializable] {
        def toStr = () -> self.match {
            case Some(t) -> "Some({t})"
            case None -> "None"
        }
    }

Metaprogramming techniques and capabilities are an area of Spero's design that presents some interesting possibilities, though little research has been done as of this moment. One of the original ideas for the language actually had types as first class values, allowing programmers to interact with them like any other value, though that is currently deprecated due to some difficulty with resolving some syntactical and semantical issues.

## Zero-cost Abstraction

To borrow the common catch phrase, Spero aims to provide all of these capabilities and abstraction at zero efficiency cost, to balance the question of developing fast code with producing safe and readable code. OOP semantics are supported through references which, though new and untested, provide a perfect avenue for many compiler optimizations for reducing copying costs and memory overhead. Spero even takes this "zero-cost" principle so far as to provide pointers as a library item, implemented entirely within Spero.

## Concurrency

TBD. Honestly, I haven't done too much with this yet, partially as I don't understand all the models out there.

# Getting Involved

Help is always appreciated. I'd say just jump in on the github projects, but the tracking of issues is very limited at the moment. Every project should have a "todo" or "plan" document somewhat outlining the current development direction and questions, but if you can't settle on what to work on, don't hesitate to email me at [ghooper96@gmail.com](ghooper96@gmail.com) (put [Spero] in the message line so I know what's up).

You can also look inside the "dev_work" and "docs" folders to get an idea for Spero's design and capabilities, though I do warn that many of those files are likely to be as out-of-date as they are "un-Spero" (I myself don't have a good idea of what's idiomatic or not). I highly encourage you writing out some pet programs yourself (though we'll need to collaborate on compilation for now) - this is the best way to fixing the language.

Some basic ideas for current project goals are as follows:

    Settling Language Design Questions and Proofs
        Ensuring type system works properly
        Deciding on a model for concurrency support
        Figuring out how modules, particularly importing, will work
    Creating x86 executables through speroc
        Possibly changing over to using llvm ir
        Removing dependence on Visual Studio/allow compilation on Linux
    Formalizing language documentation and tutorials (including project readme's)
        Adding a tutorial for learning Spero (and placing this on the website)
        Improving the information and usability of the website
    Planning out and implementing the standard library (in Spero where possible)
        Just plain writing any Spero code is just as good
