# Functional Swift Conference 2014
## The Functional Way - @natashatherobot

### Value types
> All types in Swift are value types. Classes are the exception rather than the rule
- error handling example from @nomothetis

```
enum Result {
   case Success(AnyObject)
   case Failure(NSError) 
}

// use pattern matching
switch result {
    ...
}
```

### Currying
Haskell only allows one parameter, which enforces using currying for everything

```
func add(x: Int) -> Int -> Int {
   return { y in return x + y } 
}

let partialAdd = add(2)
let sum = partialAdd(3)

// useful for passing in to map
let arr = [1,2,3]
let inc = arr.map(partialAdd)

add(6)(4)

// you can name parameters
// (not sure about the syntax here)
func add($x: Int) -> (y: Int) -> Int {
   return { y in return x + y } 
}

add(x: 2)(y: 3)
```

- curried log function example from @drewag
- example: you have a bunch of very similar functions in a class (e.g. differing by a single parameter)
    - partially applying parameters greatly simplifies the implementation of these functions

### Type-driven design

- typify all the things!
- no more inscrutable `Int`s running around

> "designing the right types for a problem is a great way to help the compiler debug your program" - @wouterswierstra

- alternative to `typealias` = wrap it in a `struct`

### Resources

- Functional Swift Book
- An Introduction to Haskell - Skills Matter
- Edx FP101x 
- swiftnews.curated.co (Natasha's newsletter)







