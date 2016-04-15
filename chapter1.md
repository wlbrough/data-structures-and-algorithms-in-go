# Minimum Viable Go

> Go is an open source programming language that makes it easy to build simple, reliable, and efficient software.
> 
> [golang.org](golang.org)

A team at Google developed Go in 2007 and the language was released publicly in 2009. The language was originally developed as a systems programming language and has syntactic similarity to C-derived languages. While taking some syntax from C, Go also adopted conventions from dynamic languages to make the code easier to read and understand. Simplicity was a stated goal of the project. Go features built in concurrency, a native package manager, and an extensive standard library.

This chapter covers the basics of the language to get started with the material. New pieces of the programming language are introduced as they are needed throughout the text.

## Getting set up

Find the instructions to install and configure Go on the [official Go website](https://golang.org/doc/install).

I will point out that you should ensure that you have set your `GOPATH` environment variable is set to your working directory.

As stated in the introduction, I recommend [GitHub's Atom](https://atom.io/) text editor if you do not already have a preferred text editor.

### Other resources

If you are looking for a guided tutorial or more detailed documentation, you can find it on the [Go documentation page](https://golang.org/doc/). In particular, check out the following resources:

* [A Tour of Go](https://tour.golang.org/) <- Guided tutorial
* [How to write Go code](https://golang.org/doc/code.html) <- Quick guidance on building packages, testing, etc.
* [Effective Go](https://golang.org/doc/effective_go.html) <- Guidance on writing idiomatic code and language details


## Packages

TODO: Add content

### package main

TODO: Add content

### Importing packages

TODO: Add content

### Installing third-party packages

TODO: Add content

### Writing packages

## Go Tool

TODO: Add content

### go fmt

TODO: Add content

### go doc

TODO: Add content

## Types and data structures

Primitive data types and data structures are the basic building blocks in any programming language. Go has a simple - but flexible - type system. Go is statically typed, so once a variable is declared its type cannot be changed.

### Primitives

Go has integer and floating point number types, a string type, and a boolean type. The number types can be declared with a memory allocation, but it is generally easier to let Go manage the memory allocation.

#### Integers

Integers are numbers without a decimal component or "round numbers". Go integers can be unsigned (i.e. positive only) like `uint8`, `uint16`, `uint32`, or `uint64` or signed (positive or negative) like `int8`, `int16`, `int32`, `int64`. The numbers in those type declarations represent the number of bits allocated for the number.

For simplicity, Go has integer types that are allocated based on machine architecture: `int`, `uint`, and `uintptr`. `int` and `uint` will be either 32 or 64 bits depending on architecture. `uintptr` is an integer pointer.

For the purposes of this book, integers will always be declared as `int`.

### Arrays

TODO: Add content

### Slices

TODO: Add content

### Maps

TODO: Add content

## Control structures

TODO: Add content

## Functions

TODO: Add content

## Scope and closures

TODO: Add content

## Error handling

TODO: Add content

## Structs

TODO: Add content

## Type composition

TODO: Add content

