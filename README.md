# Koxx
Koxx is a programming language that focuses on consistency and readability. It's designed on top of and is interoperable with Kotlin.

## Etymology
**K**otlin + The Brown F**oxx** (me) = **Koxx**

## Syntax
Koxx is supposed to be just like Kotlin, but with some changes to improve consistency and readability.

### Hello, world!
```
main {
    printLine "Hello, world!"
}
```

### No abbreviations
In Kotlin, some types and keywords are abbreviated, e.g., `Int`, `Char`, `fun`, while others are not, e.g., `Boolean`. A lot of these don't really make the language less readable; I'm pretty sure every programmer knows what an `Int` is. However, this makes the language very inconsistent.

I know that a lot of these came from Java, but Kotlin could've used the opportunity to fix these inconsistencies. You might argue that this makes typing these keywords harder, but no one codes in a text editor with no code completion.

#### Here are some of the renames:

Keywords
- `fun` → `function`
- `val` → `define`
- `var` → `declare`
- `enum` → `enumeration`
- `vararg` → `variable`

Classes
- `Int` → `Integer`
- `Char` → `Character`

### Functions
The main function does not need the main keyword
```
main {
    // your code goes here
}
```

Function declarations do not require parentheses if they have no parameters.
```
function getRandomInt {
    return Random.nextInt()
}
```

Functions with only one parameter, even if the parameter has variable arguments, can be called without the parentheses.
```
define numbers = listOf 1, 2, 3, 4 // valid
define letters = listOf('A', 'B', 'C') // still valid

printLine numbers // valid
printLine(letters) // still valid
```

All functions with more than one parameter require you to name the parameters when called. This is to prevent you from mixing up your parameters.
```
function getSpeed(distanceInMeters: Double, timeInSeconds: Double) {
    return distance / time
}

main {
    printLine getSpeed(distanceInMeters = 2.0, timeInSeconds = 3.0) // valid
    printLine getSpeed(2.0, 3.0) // invalid
}
```

All functions with a receiver and one parameter allow infix notation
```
printLine("Lando|Carlos|Charles" split '|') // valid
printLine("Lando|Carlos|Charles".split('|')) // still valid

printLine("Lando/Carlos|Charles split '|', '/') // valid
printLine("Lando/Carlos|Charles.split('|', '/')) // still valid
```

There is no distinction between functions and lambdas.
```
function greet {
    printLine "Hello, world!"
}

main {
    run(greet) // valid
    run(::greet) // no longer valid
}
```

### Collections
I'm not really sure why Kotlin removed the `type[]` declaration syntax for arrays, but I like it, so I am reintroducting it with some tweaks. I also included shorthands for sets and maps, inspired by Dart.
```
// The explicit type declarations are unnecessary and for demonstration only
define list: [Int] = [1, 2, 3, 4] // List<Int>, not Array<Int>
define set: {Int} = {1, 2, 3, 4} // Set<Int>
define map: {Int: String} = {1: "Hi", 2: "Hello} // Map<Int, String>
```

## Implementation
Right now, Koxx has no implementation; it's just a proposal. I'm thinking of making a proof of concept with a compiler written in Kotlin to compile `.koxx` files into valid Kotlin files, but I don't know yet if I'd just be wasting my time. If anyone has any ideas, shares my vision with Koxx, or is interested in making this a reality, please make an issue in this repository.
