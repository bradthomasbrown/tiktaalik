1. Define the core concepts and features of your language.
	1. Ability to switch between languages. JSX lets you "switch" between JavaScript and HTML in the same space, the language should allow one to switch languages *generally*. Oumn can be augmented with other languages, iteratively and potentially dynamically.
	2. Haskell provides very powerful type checking. TypeScript provides type checking as a superset of JavaScript. The language should be capable of being iteratively and/or dynamically augmented so that type checking can be at any level, as needed. If more advanced type checking is required, it should be straightforward how one can provide an augment.
	3. A "polyglotic" language at heart, implementations and use may involve one or more languages. It should be allowed for the lexer/parser/compiler/interpreter/engine/language service to consist of potentially many concurrently running programs in potentially many languages. The goal will be to try and do so in a resource-aware and conservative way, while using the flexibility to take advantage of the strengths of any accessible language.
	4. Machine code is king. All languages end up at machine code one way or another. It should be treated with much more respect and less "obscuring and burying". JUMPs are a necessary and fundamental part of current machines. We can build on that, but we shouldn't be afraid or ashamed of that. Instead of generalizing "it's dangerous/potentially confusing", encourage documentation and learning. Machines offer powerful features, their code should be loved. Tooling and support should handle machine code intuitively.
	5. Good DX is highly prioritized. Right now, Deno's engine with TypeScript is extremely satisfying to use. Installation is easy, extremely fast, not messy, hardly any dependencies, modules are easily accessible, one can write in TypeScript and run it virtually instantly with no compilation needed, the language server is a good step.
	6. Metrics are extremely important. It should not be difficult or practically impossible to determine, at any desired granularity, metrics for a program. There should be some way to "switch" and/or "filter", such that one can see metrics for programs, modules, blocks, or expressions. Performance metrics are a pain point. An inverse example is TypeScript and how it handles recursion depth and instantiation count. There are limits and if you exceed them you will receive an error. You will not know the limits, you will not know which rule you broke, you will not know why the rules were broken, you will not know where in your code the rules were broken. This is not ideal.
	7. There is no superior language style. Imperative, Functional, Logic, Aspect, Object, etc. It should be possible and ideally straightforward for one to use one or more styles and switch as needed in order to use what's needed.
	8. The language itself should be straightforward to augment. It should be possible and straightforward for modules and similar structures to be made and used.
	9. Don't make the EVM mistake. There will be other languages, perhaps nearly clones. We will want to work with them, not pretend we are the only one.
2. Create a basic specification or formal description of your language.
3. Implement a simple interpreter or compiler in a language you're comfortable with.
4. Identify components that could benefit from being implemented in different languages.
5. Gradually refine and expand your implementation, replacing components as needed.

## thought experiments

1. a good first goal is a minimal working program of any kind, then we want to minimally achieve our language concepts and features.
	1. hello world is the goto, isn't it? one could say then that "our language is already written", and pick "TypeScript" as the switch and Deno as an engine (might want to add concepts to the ontology, like "engine"). `console.log("hello world")` is then our minimally working program.
	2. but if we wanted to write "hello " in one language and "world" in another, how might we do that?
	   `hello.ts`: `await Deno.stdout.write(new TextEncoder().encode("hello "))`
	   `world.py`: `print("world")`
	   `deno run hello.ts & py world.py`
	   pretty straightforward, now we just have to generalize that and get to the point where we run one command and have one file. that's gonna be the hard part we guess.
	   oh. we got it down to one command, but two files.
`hello.ts`
```ts
await Deno.stdout.write(new TextEncoder().encode("hello "));
const proc = new Deno.Command("py", { args: ["world.py"] });
proc.spawn();
```
`world.py`
```python
print("world")
```
`deno run --allow-run hello.ts # hello world`

```
1. run("py", "world.py")
2. run("py")("world.py")
3. pyMachine = run("py")
4. pyMachine("world.py") # world
```

https://en.wikipedia.org/wiki/Microcode
https://en.wikipedia.org/wiki/Abstract_machine
`Dependent Types: Languages like Idris and Agda explore very expressive type systems.`

2. TS syntax blocks, TS type blocks, new syntax blocks, new type blocks (or inspired from Coq/Idris/Agda or straight type theory). A framework around blocks. Deno is an engine. Deno uses the TypeScript compiler. We'd need a compiler that could work with blocks. One could logically organize blocks how they saw fit. One could share blocks or logically organized blocks. One could take shared blocks or logically organized blocks and straightforwardly add, remove, or modify. These blocks wouldn't be limited to TS or type theory. We may even want computation blocks, such that we can emulate a Turing machine, finite state machine, classic modern computer (abstract machine?), or even more exotic computers like cellular automata. There's also language servers. We'd need one that works with blocks. These should be as reusable as possible, such that blocks given to the compiler and the language server may be the same, or perhaps subblocks could be derived from larger blocks and delivered to each. We need to then figure out how to make a compiler.
3. extend starting with blocks from assembly. this should necessarily not be problematic because all languages end up there.
https://www.nasm.us/