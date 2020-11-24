# Basics

## Structure of Sircle Source

A Sircle source file consists a sequence of global bindings. For example:

!!! example
    ```
    type Foo = { "x": Double, "y": Double }

    def point: Foo = { "x" -> 1.0, "y" -> 2.0 }

    def printFoo = p: Foo => {
        print "("
        print (p."x")
        print ", "
        print (p."y")
        println ")\n"
    }
    ```

The above source example binds three names in the top level: `Foo`, `point`, and `printFoo`. There are two types of global bindings:

- Type binding. Example: `type Foo = { "x": Double, "y": Double }`. It is similar to type aliasing in other languages.
- Value binding. Example: `def point: Foo = ...` and `def printFoo = ...`. It binds a value to a name in the top level.

## Basic Datatypes

### Primitive Types

| Type | C++ Type | Scala Type | Haksell Type |
| :--- | :---------- | :--------- | :--------- |
| `Int` | `int` | `Int` | `Int` |
| `Double` | `double` | `Double` | `Double` |
| `String` | `std::string` | `String` | `Data.Text` |
| `Boolean` | `bool` | `Boolean` | `Boolean` |
| `Unit` |  | `Unit` | `()` |
| `Any` |  | `Unit` | `forall a. a` |

_Any_ value of _Any_ type can be assumed a value of type `Any`.

### `List` Type

`List` in Sircle is similar to `list` in Python, which can contain values of different types. Therefore, `List` type is not parameterized, and any `List` value has the same `List` type.

We can construct a list in Sircle by using list lexemes. For instance,

    def xs = [1, "2", False]

We can access list elements using its index.

    xs.1
    // => "2"

The `cons` built-in function can be used to prepend a value to a list.

    cons 1 [2, 3]
    // => [1, 2, 3]

Additionally, we can concat two lists simply using the `+` operator.

    [1, 2, 3] + ["4", "5", "6"]
    // => [1, 2, 3, "4", "5", "6"]

Some library functions are defined in Sircle Prelude to manipulate list values.

    map show [1, 2, 3]
    // => ["1", "2", "3"]

    foldl (x => y => x * y) 1 [1, 2, 3]
    // => 6

    zipWith (x => y => show x + show y) [1, 2, 3] [True, False, True]
    // => ["1True", "2False", "3True"]

### `Tuple` Type

### `Mapping` Type

### `Lambda` Type
