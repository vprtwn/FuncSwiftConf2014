# Functional Programming in Swift
### Brian Gesiak (@modocache)
- wrote Quick (Swift + ObjC unit testing framework)
- works on core systems at Facebook (shared libraries in FB apps)

## Testing
- Testing involves manipulating state
    - arrange (create state) 
    - act (modify state) 
    - assert (make sure state changed appropriately)
### What's different in FP? 
- no mutated state in the functions you're testing
- spend less time worrying about state
- less setup -> act step is less important
- xUnit and xSpec are out of date in the functional world
    - setup and teardown are less important in functional testing
- *How do you test all the cases?*
    - **propert-based testing**
    - QuickCheck framework in Haskell
        - **don't write tests, generate them**
        - equivalent in Swift = [Fox](https://github.com/jeffh/Fox)
- Example: github/Archimedes
    - testing  `NSStringfromMEDEdgeInsets`
    - Fox finds the **minimum viable failing case**, not just the first encountered
- Concept from the functional landscape, but still useful in the imperative world

### Testing state
- Fox can also help test stateful code
- create *state* and *transitions*
- Fox can assert that *propertes* are true after a random series of state transitions
- More powerful than example-based tests

### Questions
- QuickCheck in Erlang has crazy time-based assertions
    - In one talk, John Hughes live codes an elevator system with a UI and QuickCheck tests
    - **Check out Erlang / ^ talk**
    - Not implemented in `Fox` yet

