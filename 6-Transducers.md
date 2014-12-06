# Transducers
## Brandon Williams @mbrandonw (Kickstarter)

## Tenets of FP
- Function composition (the most important thing)
- Immutability
- Statelessness

## Function composition
- Swift methods are not composable
- We should do everything we can to promote composition
- problems
    + less efficient

## Transducers fix composability problems
- make array operations highly composable
- reduce # of traversals on arrays
- Begins with a beautiful idea:
    + reduce is "universal" among all functions that operate on arrays
- map, filter, take, and flatten can be written with `reduce`
- `reduce` can help us make things more composable

- A **reducer** is a function for the type A of the form (C, A) -> C for some type C
- A **transducer** takes a reducer and returns a reducer
- Transducers want to be fed reducers

## The mapping transducer
- lifts any function A -> B to a transducer from B to A
    - look up contravariance