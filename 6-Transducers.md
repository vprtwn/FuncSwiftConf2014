# Transducers
- Brandon Williams @mbrandonw (Kickstarter)

- Brandon moved fast and did a lot of live-coding in a playground, so my notes for this talk aren't great. 
- Check out his [transducers playground](https://github.com/mbrandonw/learn-transducers-playground) on github

## Tenets of FP
- **Function composition**
- Immutability
- Statelessness

## Function composition
- Swift methods are not composable
- We should do everything we can to promote composition
- Demo
    - writing more composable versions of `map`, `reduce`, and `filter`
    - using these to find all the primes in (x^2 + 1) for xs = 1...100
- In the demo, the composed implementation iterated over xs more than necessary, and it was impossible to further optimize the implementation because `reduce`'s interface was incompatible with `map`'s. (or something along those lines). Transducers to the rescue!

## Transducers fix composability problems
- make array operations highly composable
- reduce # of traversals on arrays
- It all begins with a beautiful idea:
    + reduce is "universal" among all functions that operate on arrays
- `map`, `filter`, `take`, and `flatten` can all be implemented using `reduce`
- `reduce` can help us make things more composable

- A **reducer** is a function for the type A of the form (C, A) -> C for some type C
- A **transducer** takes a reducer and returns a reducer

- Lots of emphasis on the fact that after you write the function signature for something like a transducer, the rest is easy because the type system only allows the one correct implementation.






