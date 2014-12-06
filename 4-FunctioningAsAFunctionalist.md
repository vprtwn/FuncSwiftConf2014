# Functioning as a Functionalist
#### Andy Matuschak @andy_matuschak

- [WWDC2014 talk #229](https://developer.apple.com/videos/wwdc/2014/) - Advanced iOS Application Architecture and Patterns
    - [ASCIIWWDC](http://asciiwwdc.com/2014/sessions/229)
- Formerly worked on UIKit at Apple, now leads mobile engineering at Khan Academy
- Swift suggests that functional programming is the way forward
    - huge opportunity, but also a culture clash
        - "Machine Translation": translating ObjC to Swift
        - "SwifttML": turning Swift into a functional language
    - We need a significant fraction of the community to understand functional paradigms
    - Easy vs. Simple
- Objects are not simple.
- The learning curve is steep
- Concepts have a cost
    - e.g. the delegate pattern is ingrained
- "You can't answer a question that hasn't been asked"
- Proposal: exploit pain
    - JSON is painful
    - when proposing an approach, there's always a cost/benefit (now & in the uture)
    - need visible benefits of functional programming
    - Example: `optional.map`
- Incremental integration
    - "Zone of proximal development"
    - keep people at the edge of their interest, ability, and knowledge
- Provide opportunities for lightweight introductions ot concepts

### The Value Layer Game
- Friendly introduction
- Arrays are reference types in ObjC, but value types in Swift
    - Value types are copied on assignment, have a single owner
    - REference types are shared on assignment, have multiple owners
- 1 `class` in the Swift stdlib, but a lot of `struct`s and `enum`s
- The 3 I's of Value Types
    + 1. Inert
    + 2. Isolated
    + 3. Interchangeable

#### 1. Inert
- Value types don't "behave"
- Objects "behave"

### 2. Isolated
- Objects have implicit dependencies to every other reference to that object
- Every time you pass a reference around, you create an implicit dependency

### 3. Interchangeable
- You can't tell the difference between 2 instances of the same value type that have the same data

- Mocking isn't necessary if you use value types
    - You can just create data for inputs

#### What about objects?
- "The essence of the interactive medium is that the objects we create within it behave and respond" - Bret Victor
- But values are dead
- Example: Zootrope
    - images on the outside are values
    - moving reflected image in the middle creates a living identity
- example: `currentDrawing`
    - State: an identity's value at some time
    - the canvas's value at a single time
- Objects
    + represent identity
    + manage state transitions
    + perform side effects
- Two layers:
    + Object layer
        * interacts with UIKit
    + Value layer
        * all the interesting stuff
- "Separate logic from action" - key adage in OO-programming

- Making a drawing feature
    1. Incorporate touch into Drawing
        - object layer (update currentDrawing)
    2. Estimate touch velocity
        - value layer
    3. Smooth touch sample curves
        - value layer
    4. Compute stroke geometry
        - value layer
    5. Render stroke
        - object layer (update CAShapeLayer)

#### Further reading
- Rob Rix's blog post about hiding imperative stuff behind value-oriented APIs

