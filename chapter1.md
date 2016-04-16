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

## Go Tool

Once you have Go installed, you can verify the installation by typing:

```sh
go version
```

The current version is 1.6 at the time I an writing this. You will see a result like the following:

```sh
go version go1.6 linux/amd64
```

In addition to the compiler, Go installs a suite of tools under the `go` command. You can see the full listing of commands by running `go help`. 

## Types and data structures

Primitive data types and data structures are the basic building blocks in any programming language. Go has a simple - but flexible - type system. Go is statically typed, so once a variable is declared its type cannot be changed.

### Primitives

Go has integer and floating point number types, a string type, and a boolean type. The number types can be declared with a memory allocation, but it is generally easier to let Go manage the memory allocation.

#### Integers

Integers are numbers without a decimal component or "round numbers". Go integers can be unsigned (i.e. positive only) like `uint8`, `uint16`, `uint32`, or `uint64` or signed (positive or negative) like `int8`, `int16`, `int32`, `int64`. The numbers in those type declarations represent the number of bits allocated for the number.

For simplicity, Go has integer types that are allocated based on machine architecture: `int`, `uint`, and `uintptr`. `int` and `uint` will be either 32 or 64 bits depending on architecture. `uintptr` is an integer pointer.

For the purposes of this book, integers will always be declared as `int`.

Example:
```go
package main

import "fmt"

func main() {
  var one int = 1
  var two int = 2
  fmt.Println("1 + 2 =", one + two)
}
```

#### Floating point numbers

Floating point numbers are numbers with a decimal component. Floating point numbers are inexact which can cause strange errors when using comparison operators in your programs.

Go has two floating point types: `float32` and `float64`. Unless there are memory concerns, `float64` is generally used. Go also has types for complex numbers `complex64` and `complex128` which are composed of two `float32`s or two `float64`s respectively.

Example:
```go
package main

import "fmt"

func main() {
  var seven float64 = 7.
  var twoandahalf float64 = 2.5
  fmt.Println("7 / 2.5 =", seven / twoandahalf)
}
```

#### Strings

Strings are composed of letters and numbers and have the type `string`. They can be defined using double quotes `"Go is awesome!"` or backticks ``Go is awesome!``. Strings created with double quotes allow the use of escape characters like `\n` and `\t`, while strings created with backticks allow ignored newlines.

#### Booleans

Booleans are either true or false and have the type `bool`. There are three logical operators used with booleans:

* `&&` for and
* `||` for or
* `!` for not

Example:
```go
package main

import "fmt"

func main() {
  var isTrue bool = true
  fmt.Println("isTrue is", isTrue)
}
```

### Arrays

Go arrays have a fixed size and a single type. Like most other programming languages, arrays are zero indexed. A new array variable is defined like this:

```go
var arr [10]string
```

This creates an array with 10 string elements. An array can also be initialized with an array literal:

```go
var arr [5]int{ 1, 2, 3, 4, 5 }
```

Arrays are fixed in size, so trying to add a sixth element to the previously defined `int` array will cause an error:

```go
arr[5] = 6 //Causes an error at compile time
```

### Slices

A slice can be thought of as a dynamic array. Slices have elements of a single type like arrays, but can grow to accommodate new elements. Slices are defined like this:

```go
var x []int
```

This creates a 0 length slice that accepts `int` elements. To initialize the slice with a length, but defining no elements, the `make` function is used:

```go
var x = make([]int, 5)
```

Slices can also take elements from an array segment:

```go
var arr = [5]int{ 1, 2, 3, 4, 5 }
x := arr[2:5] // x == [3, 4, 5]
```

### Maps

A map is an unordered key-value collection. In other languages this is called an associative array, hash, or dictionary. Maps are declared with the key type and the value type:

```go
var x map[string]float64
```

The map `x` has `string`-type keys and `float64`-type values. For example `x["apple"] = 0.99`.

One caveat is that maps must be initialized before they are used, so in practice the above example will be declared as:

```go
x := make(map[string]float64)
```

## Variables

The section on types and data structues presented two ways to declare a variable: the `var` keyword and the `:=` operator. With the `var` keyword, you must declare the type for the variable. The `:=` operator infers the type based on the value provided, but the type remains fixed after declaration. For example, the following variable declations are equivalent:

```go
var x int = 7
x := 7
```

### Variable naming

Variable names in go must start with a letter and can contain letters, numbers, and the `_` underscore character. In practice, multi-word variable names should be `camelCased` rather than `snake_cased`. Names should be terse, but descriptive.

### Variable scope

According to the Go docs "Go is lexically scoped using blocks". This means that variables declared inside a set of curly braces (`{ }`) cannot be accessed outside of that block. For example:

```go
package main

import "fmt"

func other() {
  var x int = 5
  fmt.Println("x =", x)
}

func main() {
  x := 8
  fmt.Println("x =", x)
  other()
}
```

If you run this program, the output will be:

```sh
8
5
```

`if` and `for` blocks also have their own scope, so variables defined in those blocks will be limited to use inside that block.

### Constants

Constants are immutable variables that are defined with the `const` keyword:

```go
const message string = "All hail Flying Spaghetti Monster!"
message = "Hello world!" // Throws compile error
```

## Control structures

TODO: Add content

## Functions

TODO: Add content

## Error handling

TODO: Add content

## Structs

TODO: Add content

## Type composition

TODO: Add content

