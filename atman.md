let's see how much we can unwind:

- why are we stuck? note, this is a phase i have used in the past a lot, although i haven't used it recently
- [17867](https://github.com/denoland/deno/issues/17867)
- this link is long, i'd like to shorten and alias it like we can in telegram
- googled `vscode view and edit in markdown`, went to [some reddit post](https://www.reddit.com/r/vscode/comments/11otish/how_to_edit_mardown_visually/)
noted someone told the OP to use obsidian, which gpt also recommended
- something is greatly bothering me about needing two different applications
obsidian for not-code and vscode for code. maybe it shouldn't bother me. jupyter seems cool, and there's a deno kernel for it made by deno
what's worse? using one application for two purposes, one it doesn't support, or using two applications for two purposes, both supported?
seems more obvious what the right choice is there, huh
obsidian is free, just try it out

aha, obsidian is pretty neat. we can make links, and it's the same shortcut as telegram.
ah, the squiggle. we're annoyed by it, but we have an inkling

that the problem is how we organize concepts
the squiggle is due to an absolute import that doesn't need to be there. but it's there to be
stylistically consistent with another absolute import, where that import is very useful.

the absolute import is useful to shorten the length of imports in one area of `kaaos` from another area of `kaaos`
maybe these two areas need to be separated in a stronger way, end result being that each of those two areas has its own deno.json
- i want obsidian to regularly git add and git commit this vault. i think it would be highly interesting to have a version-controlled "stream of consciousness". maybe we'll use this to make our own LLM. maybe someone else will
- there's a plugin that claims it can do this, but it seems dodgy, and it *shouldn't* be too hard to make our own
also, why `kaaos`? i needed a name that was shorter than (`interacting with evms with deno typescript`) and it fit the theme of some other things i have, like `dizzyhavoc` and `vertigo`. however, could we not split `kaaos` into something more intuitive?
###### `deno/evm`

it is certainly more concise. there's an idea tumbling around, specifically since we've been reading about interpreters (why?) and part of that being [BNF](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form). can we create a grammar for directory organization of our code? we already accidentally created a very rudimentary version of this with some loosely-followed rules:
- folders are "concepts" or "kinds". code goes under it's specific "kind". a "kind" is something like `lib`, `types`, `schemas`. that evolved and we added to it `tests`, `fixtures`, `templates`. (explain these?)
	- `lib` we're mostly writing libraries (are we?), so "real code" goes in here. classes, functions, etc.
	- `types` typescript types
	- `schemas` Zod schemas, sometimes we end up with a lot of these
	- `tests` 
	- `fixtures` if a test requires something that takes a lot of resources to produce can we can "save" it to make testing faster, put those here
	- `templates` we're writing something that will produce typescript modules, and a good way to make that easier is to have typescript template files. these are just typescript files with placeholders in them (we have figured out ways to have placeholders for imports, types, and expressions).
- "concepts" group a collection of code organized under kinds. a good rule of thumb is that if we see some word or string very frequently in a group of files, those files can probably be grouped into a concept by the same word or string. for instance, `solcOutput`, `solcList`, `solcRelease`, `solcBuild`, etc. should strongly indicate that a `solc` concept directory should exist. then, all of the `kind` files can be split amongst `solc/output`, `solc/list`, and `solc/release`
in Backus-Naur form, we may write something like
```ebnf
<filepath> ::= <concept> <delimiter> <kind> <delimiter> <file>
<concept> ::= <word> | <concept> <delimiter> <concept>
<delimiter> ::= "/"
<kind> ::= "lib" | "types" | "schemas" | "tests" | "fixtures" | "templates"
<file> ::= <word> "." <word>
<word> ::= <letter> | <letter> <word>
<letter> ::=   "a" | "b" | "c" | "d" | "e" | "f" | "g" | "h"
             | "i" | "j" | "k" | "l" | "m" | "n" | "o" | "p"
			 | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x"
			 | "y" | "z"
```
- is there a markdown language for Backus-Naur form? when googling, we amusingly get a lot of content about Backus-Naur forms for markdown language.

i'm going to give in and use the existing plugin *for now*, as it seems to have a huge amount of downloads
alright, it's pretty cool
EBNF is a supported language
we're going to enable vim for overtyping/replace mode, god have mercy 

if we extend our BNF for ???, then we may be able to solve the squiggle.
there's issue with the above definition, since it's not particularly possible to group files into a kind or kinds into a concept. there's also going to be an issue where the `<kind>`s under a `<concept>` can't be duplicate, and expanding the definition 

maybe we can use some divider, `lib/foo.x,bar.y,baz.z`
maybe make it look more like a function? `lib(foo.x,bar.y,bar.z)`
that looks nice, also accounts for `kind`s possibly having nothing in them, like `fixtures()`
`[John[, [whose [blue car]] [was [in [the garage]]],]] [walked [to [the [grocery store]]]]` [Context-free_grammar](https://en.wikipedia.org/wiki/Context-free_grammar)
a parser generator is a regex but context-free instead of regular (probably not completely accurate)
that above sentence interests me greatly.
- i wonder what the names are for each group

[denoland/std](https://github.com/denoland/std/tree/main)
```
repo(
	archive(),
	assert(),
	async(),
	bytes(),
	...
)
```

https://docs.deno.com/runtime/manual/basics/workspaces/
we should use this to solve the squiggle problem, it also has more categories for us to use
- package
- workspace (also known as a monorepo)

so far:
`workspace(package(kind(file,...),...),...)`
the `denoland/std` repo is has more logical groups however, and the `ethereum/solidity` repo has even more
`denoland/deno` is rust, from [rust glossary](https://doc.rust-lang.org/cargo/appendix/glossary.html)
`workspace(package(crate(module,...),...)->artifact, equiv. .ts, like bin or lib,...)`

[Paul Graham](https://en.wikipedia.org/wiki/Paul_Graham_(programmer) "Paul Graham (programmer)") wrote:[[8]](https://en.wikipedia.org/wiki/Design_Patterns#cite_note-Graham2002-8)
> When I see patterns in my programs, I consider it a sign of trouble. The shape of a program should reflect only the problem it needs to solve. Any other regularity in the code is a sign, to me at least, that I'm using abstractions that aren't powerful enough-- often that I'm generating by hand the expansions of some macro that I need to write.

- if a file needs some resource or import from something beyond a sibling or a kind sibling, is that an indicator that there needs to be two packages?
from the rust glossary:
`A workspace is a collection of one or more packages that share common dependency resolution`

say we theoretically made every package a repo, which we don't need to do because a workspace can be many packages.
we would end up with a huge amount of repos with possible name collisions, wouldn't we?
we could resolve that by prefixing names, but then we might end up with duplicated prefixes not logically organized

the problem seems to be that github only allows for a very limited "logical organization depth": `repository(code,...)`
deno also allows for a slightly less limited "logical organization depth":
`workspace(package(code,...),...)`

gpt seems to also believe there is no real existing concept or implementation of a system that allows for any amount of "logical organization depth"
we actually got into a disagreement with gpt, as it seems gpt says filesystems aren't logically organized. as long as there are no exact duplicates of code, we argue that they *are* logically organized. if there is a duplicate of code, then that is not logically organized, and the duplicated code should be coerced into a shared resource. when that is done, now the filesystem is logically organized. 
gpt also argued that that "the logic of a filesystem hierarchy depends entirely on the user's organization strategy, which may not always be intuitive or standardized. for example, a directory named `utils` might contain helper functions in one project but logging tools in another. the logic isn't inherent but imposed by the user".
we argue "the logic of a filesystem hierarchy is inherently logical. if we view the filesystem hierarchy as logical groupings of any depth, then it would be obvious that we cannot standardize names or even possible names for any specific depth. furthermore, the names at some depth may be relative to some lesser depth. a framework that views filesystem hierachy as inherently logical would say only say that logical groupings can be depth relative to other logical groupings, but the names for these depths is determined by the user".
to expand on the argument: "a reserved keyword metadata file for this framework could be placed in each logical grouping that declares names of depths relative to the logical grouping the metadata file is located in. in your example, the `utils` directory could mean two completely different things, since the name is just an alias for whatever depth `utils` appears in relative to some other logical grouping".
expanding more: "the metadata files that declare aliases for logical depths could declare aliases for any relative depth or combination of relative depths. for instance someone may have a `workspace` that's an alias for a depth 1 grouping. `workspace` might declare that the next depth levels are, in order: `package`, `crate`, `module`. it would then be expected/enforced that these are the aliases. however, a `workspace` might also declare only one next depth level: `package`. each package then may declare their own relative aliases." (this seems similar to haskell type declarations. possibly there could be parametric logical groupings? is that the right terminology?) (we also feel like this is similar to or encroaching on chomsky hierarchies, where github and deno are using the logical grouping equivalent of regular languages and what we are proposing a system that allows the logical grouping equivalent of context-free languages. we probably don't want to go past that, since that means we aren't a filesystem-like structure anymore, but maybe we could still do that considering symlinks are a thing)
this system would let us create something like github but much more powerful, since a user wouldn't have "repositories". a user would have a manifest, which could say `depth 1 - "repository"` in order to be logically equivalent to github. the manifest may even be created by github and imported by the user. then, github could know immediately whether or not it was compatible with and could display whatever the user has there.
JSR (Deno) would know and be compatible with a manifest that said "depth 1 - package" and could adapt to be compatible with a manifest that said "depth 1 - workspace, depth 2 - pacakge". Users who want their code on JSR would organize their code with a matching manifest or could import that manifest with their own.
the "thing like github but more powerful" wouldn't check for compatability to that extent, it would just check for valid manifests, then allow navigation according to the manifest. so a user might have "repositories", or they might have "workspaces", or really they could have any number of logical groupings with any names, each with their own possible number of logical groupings and names, etc.
for instance, we have ??? -> kind, where kind -> "types" | "lib" | "schemas" | etc., and we want to create new depths that can group ???s. with our system, we could easily do so, and we don't even need to come up with names, since names are just aliases of depths. we could say we have 0 -> kind and we want 0 -> 1 -> kind. a system like github that could handle this would display that just like that. it's not the most intuitive, but that's only because we haven't given aliases to 0 and 1. we could call 0 "workspace" and 1 "package", then we'd be a lot like deno: "workspace" -> "package" -> "kind"
"kind" would be a parametric logical organization, since "types" is expected to contain types, "lib" is expected to contain library functions, classes, values, or other concrete usable things, "schemas' is expected to contain zod schemas.
importing could possibly be altered to not be done by just paths, but also possibly by functions. instead of `../../../../foo.ts` we could have a function like `up(x)` where `x` is the amount we ascend from this depth, like `up(x)/foo.ts`. we could also have `root()`, which takes us to the root. one idea of what a root is could be that there is a global logical root `/` that contains ***everything*** if importing remotely from some supergithub or some env variable specified local logical root `/`. for the global supergithub, the root manifest may just declare one depth `id`. in order for people/groups/entities to put their code in the supergithub, they'd be required to claim some id. this could be usernames and passwords, but could also be something more robust, like the id is determined cryptographically, entities create "transactions" that interact with supergithub and sign the transactions, supergithub would then determine their id mathematically from the signature.
we could rewrite our code structure just like this, but we'd probably need some way, for now, to translate or crunch what we have to be compatible with JSR or github, since building supergithub would be a bit of a feat.

Bret:
`When you have variable depth repositories, are you treating them like multidimensional arrays so each element can be referenced as an array element and tracked alphanumerically?`

github is treating them like multidimensional arrays
```
   0  1  2  3
0 [a, b, c, d]
1 [i, j, k, l]
2 [n, m, o, p]
3 [v, x, y, z]

repo 0 thing 0 "a"
repo 1 thing 2 "k"
repo 2 thing 3 "p"
repo 3 thing 1 "x"
```

it should be treated like a tree   
```
languages -
    typescript -
    |   EVM -
    |   |   nodes
    |   |   solidity
    |   |   |   compiler
    |   |   |   output parser
    |   |   |   |   libraries
    |   |   |   |   types
    |   |   interface generator
    |   |   |   libraries
    |   |   |   types
    solidity
        uniswap
        |   smart contracts
        dizzyhavoc
        |   smart contracts
```

when we were playing with the code organization, we did run into instances where we thought "is this code _too_ organized? for exampe, solidity output schemas. the output is a large json object, made up of recursively smaller components, with a fairly significant recursion depth.
if one was to want to navigate this on something like github, to get to a "descriptor component" they'd need to navigate like `output/sources/contracts/contract/abi/descriptors/component`
which is a bit of a bitch. how would we reduce the import path size if we needed that?
we'd make a module file at `output/mod.ts` and in there we would put `export { component } from '.../component.ts'` .
in instances where that's acceptable, would it not also be equivalently acceptable to symlink to `component.ts` from `output`?
what about `sources` under `linkReferences`? there's already an `output/sources/`, so a symlink couldn't be created. however, we could resolve the name clash by symlinking `linkReferences` to `output`
we should probably prefix symlinks with a symbol to make it logically intuitive that the symlink is a symlink, so if we use something like github to navigate, we get an immediate and intuitive notion that when we see the symbol prefixing some file or directory, we know it's not immediately connceted with the parent logical group. note that we say "it's not immediately connected" rather than "it's deep within the parent group" because we could possibly be symlinking things from outside of the parent group. for instance, the solidity files needed to build the test environment to test vertigo would be convenient and logically intuitive to access under a directory called `vertigo`. however, if any other project needed some of these for some purpose not related to vertigo, it would make more sense to logically group those solidity files somewhere else, under a directory called `solidity` or similar. then, the files could be "imported" either by prespecifying some long relative path, using an import map to prespecify some long base relative path (if multiple things under the import map will be importing this), or, alternatively, we symlink, which is more from the perspective of the filesystem as a whole or from the root rather than from one of the specific points looking relative for some resource.

there is still some tradeoff in creating a perfectly logically organized system. a perfectly logically organized system should only have one file per folder (although possibly many directories).
it may be more accurate to describe what we want as a directed acyclic graph if we involve symlinks. actually, it may just be a directed graph. i think hardlinks are more appropriate for what i'm describing. however (of course), github doesn't respect hardlinks, and pushing a git repo with hardlinks will cause github to reinterpret the links as individual files. cloning will then create multiple files.
symlinks would work better with github at not duplicating code, hardlinks are more accurate to what we're imagining here.

we may need some preprocessing and postprocessing to go from filesystem -> github/jsr -> filesystem when using links, depending on how these things interact with the links

it's probably best to make more repos rather than fewer in terms of github, and more packages rather than fewer in terms of JSR

let's do a bit of reorganizing then.
what actively-used directories do we have at root?
- base64 (smart contracts for vertigo simulation)
- dizzyhavoc (smart contracts, deno/evm things, tests, deployment pipelines)
- docker (deno/docker? bindings?)
- ds-weth (smart contracts for vertigo simulation)
- exit-handlers (general deno helpfil thing)
- jra (needs to be reorganized)
- kaaos (rename to deno/evm?)
- openzeppelin-contracts  (smart contracts for vertigo simulation)
- permit2 (smart contracts for vertigo simulation)
- solidity-lib (smart contracts, not the original name)
- solmate (smart contracts for vertigo simulation)
- std (extends deno std)
- universal-router  (smart contracts for vertigo simulation)
- v2-core  (smart contracts for vertigo simulation)
- v3-core  (smart contracts for vertigo simulation)
- v3-periphery  (smart contracts for vertigo simulation)
- vertigo (contains all sorts of shit)
we have other actively-used directories not at root, like dizzyhavoc-web (common prefix)

we don't want to git init the user/ dir. why? there's a bunch of stuff in there that isn't relevant to ... ? some logical grouping of things (code things? we may want other things in here, whitepapers, etc. Although, didn't we just logically group code things and other things? aha, the filesystem should express exactly what you're thinking. it is logical, gpt get fucked)
if we're going to end up creating a huge amount of repos (flattening for github is our crunch method, prefixing with context to solve name collisions), but we also want the whole thing to be one huge repo, how do we do that?
submodules, right?

if all these smart contract directories are for vertigo, should we put them in vertigo?
we sort of know that they aren't specifically for vertigo, they're to help create a test environment for vertigo. they're a dependency of vertigo. they are definitely logically groupable into a new group for smart contracts. we're going to call them `smartks`, since apparently K is a well known abbreviation for contract (in the legal field, at least)

two things stumping us now:
- we submoduled the openzeppelin repo, but that repo's working branch is actually empty and has two branches with different versions. both versions are needed, but we had worktree'd the versions. we don't really like this, we'd prefer to just logically group the versions under openzeppelin.

[git-checkout](https://git-scm.com/docs/git-checkout)
`Updates files in the working tree to match the version in the index or the specified tree`
needed to `git fetch origin <branch>` to get the branches from the source local repo
https://git-scm.com/docs/git-checkout#_detached_head
is helpful looking
a lot of stackoverflow posts point to
https://git-scm.com/docs/git-worktree
being better
`git worktree add -d <path> creates a new worktree with a detached HEAD at the same commit as the current branch`
so `git worktree add -d v3.4.2 v3.4.2-solc-0.7-trim` should do what we want. possibly.
the trim branch isn't in the submodule, but should be fetched "but there does exist a tracking branch in exactly one remote"
"invalid reference"
prefix the commit-ish (last thing) with `origin/`, and it seems to have worked

what's the next thing stumping us then? dizzyhavoc/contracts. exists as a folder in another repo. we want to take that and make it dizzyhavoc, under the smartks folder
we've been adding everything as submodules so far, which we're not sure we want. we want to collapse everything into a large directed graph then, when we've done that, if there's some *thing* that should go on github, we should turn that thing in our graph into a submodule, create a repo for the submodule, then push the submodule. 
"A submodule is a repository embedded inside another repository"
we isolate a graph in order to use it as its own thing. this should be okay, in the grand scheme, shouldn't we have a ton of isolated graphs?
we're going to take a guess at the next command
(from code/smartks) `git fetch ~/dizzyhavoc`
this seems to have fetched that stuff into FETCH_HEAD, and the idea seems to be to merge these things
not sure if this is what we're supposed to do, but if we add a worktree `dizzyhavoc`, switch there, then merge FETCH_HEAD, we *should*(?) get the desired outcome
ah, we want to --orphan the worktree, so it's fresh
--orphan seems to go with checkout
ah, we need to update git
ahhh, we cannot easily do so. we either need to build git or backport from debian `testing`
we're going to try building it rather than backporting
maybe we don't need to do either. git says we can install it *via git* (weird), or we can add the git-core repo and install it
oh, nvm, that's for ubuntu, not debian
git cloned git, tried to build, fatal error "openssl/ssl.h: No such file or directory"
according to stack, try `apt-get install libssl-dev`
and also `apt-get install libz-dev`
ah, INSTALL does list dependencies, just never uses the word "dependency"
and libcurl4-openssl-dev (not sure here, libcurl4 is a "virtual" package and this one is a "flavor" (?))
and libexpat1-dev (maybe?)
sorta shitting in the wind here, but each time i add something, make seems to do some more stuff
hey, it didn't crash
make intall worked too, but it's in ~/bin, which is weird (that directory did not exist previously).
let's try the orphan worktree thing again, if it works, maybe we can uninstall the existing git and move everything new git put in ~/bin to /usr/bin? (location of which git)
works like a charm, no shit
`~/bin/git worktree add --orphan smartks/dizzyhavoc`
creates a worktree, but not a branch, and the commit is `0000...`
specifically, the specs say 'unborn branch'
we can cd to it and it seems to be fresh
so what we want to do from here is repeat `git fetch ~/dizzyhavoc`
then `git merge FETCH_HEAD`
that actually worked pretty well
so now dizzyhavoc is a worktree, which is like a submodule, but not. submodule points to another repo. worktree is another repo living alongside your original one. we should combine these
seems there's an easier way to do what we are doing, but it is still possible
maybe we don't want to _combine_ them, but worktrees are nice
\-------- 
\--------
\--------
let's try something else
`cd code`
`rm -rf -- .[!.]* *` 
`git init`
`touch INIT`
`mkdir -p smartks/openzeppelin/3.4.2`
`git add .`
`git commit -m 'INIT'`
(can now use `git reset --hard :/INIT --` to go back)
`git ls-remote -b ~/openzeppelin-contracts/`
`git fetch ~/openzeppelin-contracts/ refs/heads/v3.4.2-solc-0.7-trim`
`git merge --allow-unrelated-histories -s ours --no-commit FETCH_HEAD`
`git read-tree --prefix=smartks/openzeppelin/3.4.2/ -u FETCH_HEAD`
that seems to absorb nicely

let's do dizzyhavoc
that was easy and fun

when we get to trying to put stuff onto github and JSR, what if, instead of submodules or whatever it may be, we create logical groups "github" and "JSR", under each of those "repositories" and "packages" respectively, then just hardlink things to there? then the requirements of those services shouldn't have any impact on our structure.

lets get all of the uniswap contracts
lots of organizing. good.
we need to absorb vertigo and dizzyhavoc and then we can start descending into the worktree and causing all sorts of chaos
vertigo is a part of dizzyhavoc
the dizzyhavoc directory consists of some helper ts apps, some helper ts libraries (evm and non-evm), some pipeline scripts for evms and dizzyhavoc contracts, and some "tests". it had contracts, but we ripped those out
we probably shouldn't do symlinks or hardlinks across units that will be on github or any other collaborative similar thing. if links are respected and a contributor makes a contribution, when we pull that the links would force changes to happen. might be unpleasant to deal with.
keep links within things that will be a unit on something like github and it _should_ be okay but something says maybe it won't be.