# Swift Network Programming (with Monads)
- John Gallagher (@nerdyjkg) (Big Nerd Ranch)

## What is a Monad?
- "A monad is just a monoid in the category of endofunctors" (Categories for the Working Mathematician)
- Optional is a Monad
- `bind`
- `map`

## `Result` and Error Handling
```
protocol ErrorType: Printable {
}

enum Result<T> {
    case Success(T)
    case Failure(ErrorType)
}
// doesn't compile
```
- See [LlamaKit](https://github.com/LlamaKit/LlamaKit)
- "Result Train Tracks" image
    + http://fsharpforfunandprofit.com/posts/recipe-part2
    + "railway-oriented programming"
        + if anything fails, skip straight to failure case

## `Deferred`
- Asynchronous library inspired by OCaml library
- Similar to promises/futures

## `DefferedTCPSocket`

- Why is this better?
- No need for error handling ifs or result switches
    - "All we need to write is the happy path"
- Less code
- Type system handles errors

## Conclusions
- Steal ideas from other languages
- Use functional techniques when it makes sense
- Say goodbye to `NSError **`
- https://github.com/bignerdranch/Result
- https://github.com/bignerdranch/Deferred
- https://github.com/bignerdranch/DeferredTCPSocket
- https://realworldocaml.org

## Questions
- explain `@autoclosure`
- how do you avoid rightward drift of nesting?
    + you can define separate functions, but that spreads out code and loses the logical order
