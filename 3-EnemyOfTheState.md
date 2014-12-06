# Enemy of the State
## Justin Spahr-Summers
- [slides](https://github.com/jspahrsummers/enemy-of-the-state)

| "State is the single biggest source of complexity in software development"
| "We want to be using the best possible abstractions"

- State: your stored values at any given time
- Mutation: the act of updating some state in place
- State is easy
- but easy and simple are not the same
    - Rich Hickey talk: Simple Made Easy
    - Easy: familiar or approachable
    - Simple: fewer concepts and concerns
- Complexity: mixing ("complecting") conepts or concerns
- State is familiar (but complex)
- All systems have *essential complexity*, but state adds `incidental complexity`
    - See "Out of the Tar Pit" (Moseley and Marks)
- **State is exponentially complex**
- **State is just a glorified cache**
    - "There are only two hard problems: cache invalidation and naming things" - Phil Karlton
- Table views as a cache
    - see Andy Matuschak's post, "Mutability, aliasing, and the caches you didn't know you had"
    - table view can become inconsistent with its data source and crash
- **State is unpredictable**
    - race conditions
    - it's very hard to prove that code is free from race conditions
    - State is spooky action at a distance
- **State is hard to test**
    - tests verify expected outputs for certain inputs
    - state is implicit input that can change unexpectedly
- It's impossible to avoid all state
    - Preferences, open documents, in-memory or on-disk caches, UI

- 3 techniques to avoid state
    - Values
    - Purity
    - Isolation

### Values
- Convert mutable objects into immutable values
- Value types are immutable in Swift
- In Swift, use `struct`s and `enum`s
    - Classes are reference types
    - Copied (not shared)
    - Value types are *immutable* in Swift
- Variables are mutable, but values never change
    - variables can change what value they have stored in them, but the values themselves can't change
- "Mutating" functions
    - `inout` keyword (look into this)
- **Values are automatically thread-safe**
    - Variables need to be synchronized
- **Values are automatically predictable**

### Purity
- Same inputs always yield the same result
- Must not have *observable* side effects
- is `array.count` pure?
    - yes, only depends on its hidden input of `self`
- **Impure functions are surprising**
- "Insanity is doing the same the over and over again but expecting different results"
- **Pure functions are easily tested**

### Isolation
- "Objects should have only one reason to change"
    - Isolate unrelated pieces of state
- Stateless core, stateful shell
    - keep domain logic in completely immutable value types
    - add stateful shell objects with mutable references to immutable data
    - see Gary Berhardt's talk, "Boundaries"
- MVVM > MVC
    - omniscient controller -> less omniscient view model
    - helps avoid scary action at a distance
- "Globals: just say no"
    - globals get mixed into every part of your program
    - Isolation reduces complexity, globals compound it
    - Singletons are global state
    - Let's just pass instances around instead

- Example: Singleton networking
    - problematic because you don't know all the places the singleton is being used.
    - to change this: just remove the singleton accessor and force the consumer to create an instance
    - Easily testable
    - Explicit dependencies
    - More flexible

- tl;dr: Minimize state -> Minimize complexity

### Further reading
- Rich Hickey talk: Simple Made Easy
- Andy Matuschak's post, "Mutability, aliasing, and the caches you didn't know you had"
- Gary Berhardt's talk, "Boundaries"
- WWDC 2014: Advanced iOS Application Architecture and PAtterns
- [Haskell](book.realworldhaskell.org)
- [Elm](elm-lang.org)

### Questions
- Use `struct`s over classes wherever possible
- if you put a `var` in a struct, that's not inherently a bad thing because you still have an immutable struct
- How do you coordinate changes between models?
    - hierarchy (parent-child view models)
    - avoid having multiple sources of state (caches, things that alias each other)










