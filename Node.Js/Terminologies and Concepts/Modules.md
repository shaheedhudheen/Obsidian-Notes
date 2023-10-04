## What are Modules?

_Modules_ are reusable pieces of code in a file that can be exported and then imported for use in another file. A _modular_ program is one whose components can be separated, used individually, and recombined to create a complex system.![[modular-program-diagram.svg]]

This modular strategy is sometimes called _separation of concerns_ and is useful for several reasons.

By isolating code into separate files, called modules

- find, fix, and debug code more easily.
- reuse and recycle defined logic in different parts of your application.
- keep information private and protected from other modules.
- prevent pollution of the global namespace and potential naming collisions, by cautiously selecting variables and behavior we load into a program.


## Node.js vs ES6

multiple ways of implementing modules depending on the _runtime environment_ in which your code is executed

1. The [Node](https://nodejs.org/en/about/) runtime environment and the `module.exports` and `require()` syntax.
2. The browser’s runtime environment and the [ES6](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) `import`/`export` syntax.

## Modules in Node

Every JavaScript file that runs in a Node environment is treated as a distinct module. The functions and data defined within each module can be used by any other module, as long as those resources are properly _exported_ and _imported_

