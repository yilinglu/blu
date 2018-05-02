## What does bind(), apply() and call() do?

### bind()
The bind() function creates a new bound function with its `this` keyword always bound
to the first argument passed to bind().

bind() accepts multiple optional argumnets after the first argument, all of which will be prepended to 
the list of arguments provided to the new bound function. 

bind() is a mechanism of "hard binding" an object to a function's `this` keyword.

### apply() & call()
apply() and call() both invoke a function with `this` being explicitly bound
to the first argument passed to apply() or call().
like the following:
```
func.apply(thisArg, [argsArray])
func.call(thisArg, arg1, arg2, ...)
``` 

The difference is that after the first argument, call() accepts an optional argument list, while apply() accepts an optional array-like object.


## What does this output? const a = (a, b) => b % a; const f = a.bind(null, 2); [1,2,3,4,5,6,7].filter(f)
It outputs [ 1, 3, 5, 7 ]


## Explain JavaScript Closures - give an example to back up your explanation
Closure is the ability of a function maintains access to its lexical scope when the function is executed 
outside that lexical scope.

In the example below, the function named 'greet' closes over its lexical scope varialbe 'message'. In a future time when
function greet is executed (`demo` is called) outside the lexical scope of `greet`, `greet` still prints out the value of variable message.
```
function demo() {
    var message = 'Hello World';

    setTimeout(function greet() {
        console.log(message);
    }, 200)
}

demo();
```

## What's the difference between a Merge and Rebase?

(We will explain in the context of a feature branch and master branch)

Merge replays changes on a feature branch since it diverged from master on top of master,
git then creates a new merge commit that has two parent commits: one is the latest on master, the other on feature branch.

Rebase, however, can produce a linear cleaner history by not creating a merge commit that has two parent commits.

Rebase pulls in all the latest changes from master, apply feature commits on top of them by changing the parent commit of feature
branch commits.

Rebase also affords us to do interactive rebase which merge cannot do.


## What TDD/BDD tools have you used?
1. Unit testing with Jest, Mocha.
1. End to end testing with Cypress.
1. Assertion library: Chai

## If you've experimented with Monads, please tell us about what you did
I implemented a simple Monad utility while refactoring an Node.js application that drives an electronic card reader. 

The application had a ~600 line function with deeply nested if-else statement for
implementing card reader business logic. This function was hard to test, hard to do safe change and hard to debug.

I analyzed the busienss logics and workflow, implemented small and individual business logic with pure functions and used the Monad utility to compose multiple pure functions to build more complicated logics.

By doing so, I made the application easy to understand, easy to test, friendly to changes, more robust (because Monads helped eliminate all intermediary states the previous monolithic function had maintained).




