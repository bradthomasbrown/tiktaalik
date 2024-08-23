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

what are we doing today?
organizing! yay!
in dizzyhavoc, there's a dir `bin` with apps intended to be run. one of these takes a secret in stdin, then outputs the address for that secret. we can remove that
one is a very very prototype of what looks like a lexer for my own flavor of ethereum assembly. go figure, we called tokens `tokens`, without knowing that was the standard term or even what a lexer was. good job. we don't need this.
one of these downloads a geth binary given some version. this is probably useful, but not as a binary. keep. another generates a random private key from /dev/random. why not use crypto.getRandomValues and ditch the bash script?. remove
`crypto.getRandomValues(new Uint8Array(32)).reduce((p, c) => p + c.toString(16).padStart(2, '0'), '')`

two interesting things so far:
- aiq is a neat idea, but it was already made by deno in the standard library as an "async multiplexer". not sure if our implementation is more flexible, but we can most likely remove ours and use theirs to reduce code reuse.
- artifact is actually a very neat idea. like our current Cache, but specifically for cached assets that take significant resources to produce. what makes it special is that it orchestrates in case of "what if many requesters request a resource at the same time?" by only triggering one processing action by the first requester and forcing the rest to wait until that one is complete. that way, 10 things could request compilation results for some contract, if the results don't exist, we only compile it once for the first request encountered, the other 9 wait patiently, after given the signal they can check to make sure what they have is what they want, then they can be satisfied. 
	- we are extremely interested in making this system remote capable. say we have some microarchitecture application where two modularized services need some asset that takes significant resources to produce from a third modularized service. the two modularized services don't share a filesystem, so using mkdir to make a lock file won't work here. how can they coordinate? what do we do if one requester successfully claims a lock but then dies? ({ method: 'lock' }, no { method: 'unlock' } ever received)
	- does this have anything to do with database transactions? deno.kv? we think the way those things work is very related to what we want
	- orchestrator can require receipt of some sort of regular occurring signal to verify liveliness of a requester (socket?). if the signal dies, orchestrator can assume the requester died and can release the lock. doesn't have to be a socket at first ({ method: 'i_am_alive' }), but probably best to use one.
we should be able to get rid of gethup, since the deno evm node docker dir should contain something functionally equivalent. yep, it does

we're interested in the solc json input having a SolidityAST and EVMAssembly option for the input type. can we verify an assembly contract?

verify.ts should go in deno/evm/lib
getChainId gets a chainId from a json file, expected to come from a clone of that one repo with all the chain info. remove this for now (but we get why it might be there)
aiq and artifact should go in deno/stdplus, mark aiq as stale
deploy should go in deno/evm/lib
pipelines? those are the real meat of dizzyhavoc we suppose
we get the idea that dizzyhavoc should be a logical group under code, not within deno. it's a whole project (granted, using deno a **LOT**). one may argue that it shouldn't even be under code, since it should contain non-code things (assets, images, documents, etc.). 
sure the pipelines are code, but because they use abstractions of functionalities (which can be massively improved upon), the pipelines functionally are dizzyhavoc specific. _code_ implies code that isn't specific to one... ???
??? is what dizzyhavoc belongs to. it's some more concrete thing. is it a project? a goal?
time to dig deep. we know there's a very large telegram archive rocking around somewhere.
we found it. 
"Warning, this is a very large file (104.1 MB). This is the contents of the TangleCoin group chat up to 2021/09/19 around 12:30 AM EST."
the orbicular telegram seems to be lost to time, unfortunately. we wanted to see that the most, since that would let us where we started. we can maybe piece things together, however:

- Orbicular. We tried trading shitcoins and failed miserably. The last one we were interested in was XAMP, or "anti-Ampleforth". Their website is dead, but their twitter is still alive and CMC has a page for them with the token address. From their twitter:

>How will the free market behave? How will traders react to a constantly reducing supply? Who knows? What are the limits of our current concept of what a financial system is?
>While Ampleforth issues more tokens based on supply and demand, we constantly destroy it. Cryptocurrency was born on the concept of deflationary assets. Antiample takes this concept to the extreme.
>Antiample is an ERC20 token on the Ethereum blockchain. Unlike a regular ERC20 token, Antiample has a constantly reducing supply. Holders of Antiample own a portion of the total supply of the token rather than an amount of Antiample themselves. When the value of 1 Antiample token decreases, the supply is decreased by at least 1%. This causes each Antiample to be worth more.

- bit of a flawed premise abusing the meaning of "value" and "worth", but hey, we didn't know much about economics (and still don't). To summarize, it was an experimental shitcoin that took a pre-existing tokenomic mechanic and did something interesting and new with it. In essence, that's what Orbicular was. We recall looking at Ampleforth to figure out exactly what it was and what it's purpose was, and we recall fixating on a section in the [whitepaper](https://whitepaper.io/document/585/ampleforth-whitepaper) :

> 4.2 Expansion As discussed in Section 3, during expansion there is a window in time where fast actors have an opportunity to sell after the supply increases but before any price correction occurs. As long as there are enough fast actors willing to sell, price will decrease. This could produce price and supply patterns like those below:

(we get the idea we should start archiving these contributors to what we're doing)
added antiample x posts and ampleforth whitepaper to this vault

- We recall specifically interpreting what they described in 4.2 as an "arbitrage event". `fast actors have an opportunity to sell after the supply increases but before any price correction occurs`. We recall getting an idea from that: 
## <u>Does altering the supply like this really cause market behavior to happen?</u>
  
- Orbicular was then my "experiment" to test this theory. The execution was simple and I'll toot my own horn here and say it was pretty clever: Cyclically alter the supply over time, in steps. We recall now that the goal of the experiment was that it would do one of two things. Either:
	- Actors do behave according to their expections.
	- Actors do not behave according to their expectations. In this case, Ampleforth is meaningless.
- If actors do behave according to their expectations, then a very large question comes to mind:
	- Where does the opportunity come from? For a "fast actor" to "have an opportunity", they are acquiring some value they did not previously have. 
- Unfortunately, Orbicular didn't perform how we expected it to, as an experiment. There was a bug in the implementation due to a misunderstanding of how Uniswap liquidity pools worked and, additionally, the value of Orbicular skyrocketed at some point, throwing any ability to measure the effect completely in chaos.
	- This was our fault. an amusingly significant gap in our implementation was simply "nobody knew Orbicular existed". We knew /biz/ had a lot of shitcoin threads, so we started our own to sort of bait people into the experiment. We unintentionally copied an OP to use as a framework for our own that included some statements about being sponsored by large companies (honest mistake, we were rushing and just changed the token name). This caused a rapid chain reaction where people believed this was some brand new token sponsored by large, real organizations (Oracle I think was one of them).
- The bug was twofold: If you reduce the supply of your token via a rebase, Uniswap gets confused about its liquidity pools and the token becomes untradeable until someone calls `sync()` on a V2Pair. If you increase the supply of your token via a rebase _and don't call sync()_, <strong><u>anyone can call `skim()` to just take the excess</u></strong>. Someone did indeed start doing this and slowly draining the liquidity pool.
- We created a special Rebaser contract with functions to perform the rebase and the synchronizations simultaneously. We also got a hunch why the Ampleforth premise was flawed: The "fast actor opportunity" comes from the liquidity pool. Sure the token's price relative to some other asset can be pushed to some arbitrary number, but it's being done at a cost, that cost comes from the liquidity pool.
- The concept of Tangle started to take root around here.
- We also got a more intruiging take on the experiment after asking: When the fast actors take their opportunity, what are they really doing? They're exchanging Ampleforth for ??? where ??? is some other asset and they're doing so because they know the rebasing mechanism will make the exchange back into Ampleforth profitable. Ampleforth is creating "arbitrage events", paid for by their own liquidity pool. In a twisted sense, it's a token that incentivized its own wash trading. 
- The idea was: Why should the fast actors leave the rebasing system at all? What if there was another system running alongside the original whose rebase schedule countered the original's? For actors, this should be doubly enticing and value should never leave our system.
- Suddenly though, we look at section 3 of their whitepaper:
  
	>Fast Actor (Expansion): Let’s imagine Bob is a fast actor. He checks in before expansion at state t0, again while the system is expanding at state t1, and finally after expansion at state t2.
  >- Bob at t0: 1 coin, worth $1.2/coin
  >- Bob at t1: 1.2 coins, worth $1.2/coin
  >- Bob at t2: 1.2 coins, worth $1/coin
	>At t1 there’s a limited opportunity for Bob to sell more units than he could have at t0 for the same price, before other fast actors restore the price to its equilibrium value.
  
- This was something we considered a bug in Orbicular and we fixed that bug (**!!!**) by creating OrbicularV2, which used the dedicated Rebaser contract to ensure the "bug" wouldn't happen again. In our cyclically time-based rebase schedule, someone was indeed taking advantage of every "limited opportunity" to sell more units than they could have, before other fast actors. When we called `sync()` via the Rebaser contract, we removed the "Bob at t1: 1.2 coins, worth $1.2/coin" step completely. This destroyed the "arbitrage event".
- In other words, Ampleforth's "limited opportunity" for "fast actors" is a flaw that allows anyone to skim from the liquidity pool.
- OrbicularV2's rebasing schedule, after "fixing the bug", resulted in what we could describe as a "purely cosmetic" effect. Since there was no arbitrage event, the whole system had no value.
- Despite this, I was still interested in the whole "incentivizing people to wash trade" thing.
- Tangle was my next project that kept this "thing" and introduced a few similar things:
>Rewardable Events
> Tangle incentivizes its own attractiveness by taxing certain contract interactions and then allocating those taxes as rewards for specific and desirable actions. The rewardable actions can be summed up in three different categories: 
> 	1. Market Making 
> 	2. Distributing 
> 	3. Staking
> When a rewardable action is performed by a user in any of the three categories, they receive a “point” in that category known as a Rewardable Event. These Rewardable Events are one factor used to determine the quantity of rewards received by that user whenever they choose to redeem rewards.
- On top of that system, Tangle incorporated a novel "reflection" system, where taxable contract interactions distributed value to every Tangle holder instantly via rebases.
- The taxes could all have different rates, and where the taxes went could all have different distributions.
- A long-term vision in the whitepaper was that TNGL was going to be a governance token that could be used to alter individual tax rates and distribution policies. When TNGL was spent on governance proposals and votes, it too would be distributed into the incentives system.
> <u>The flow of tokens through Tangle is then best described by its own name.</u>
- TangleV1 and TangleV2 seem to have had some unfixable issues, so a V3 was made.
- A new long-term vision of a decentralized prediction platform spawned, Forutsi.
- Small idea for an NFT collection made up of ethereum addresses. Image data pulled from trust wallet would mean that anyone could claim then buy, sell, transfer, trade, auction token logos as NFTs (as a part of "owning the address") (facebook stole our name lmao)
- Cross-chain decentralized exchange concept spawned because we wanted a bridge for Tangle, but without a mint function, 1:1 swaps couldn't be implemented, there needed to be an exchange rate between chains
- metrics dashboard
- Tangle seems to the experimental offshoot of the Orbicular experiment with the central theme "what can we do with the ability to incentivize smart contract interactions (of any kind)", although i don't think we ever got that general with it
ah, it appears the tangle archive i have was to basically cover up the spiciness, split the channel in two, one "secret" channel where people could speak their minds and one "public" channel that's more sanitized. clever
- XDEX was the centralized cross chain exchange for TNGL. it put a lot of the business logic of uniswap into a plain database. a centralized authority (me) would relay swap info from a chain to a database, get the results, as if the database were the smart contract, then tokens would be transferred in accordance to the results. the tokens were sent to a locker contract that acted as the database's "wallet". anyone could "add to the liquidity pool" via a smart contract function
- "there will be no V4, but rather a "final version", an upgradeable Tangle contract similar to how Uniswap's routers can be upgraded.
- a bug in V3 was found, necessitating the "final" tangle (late september). 
- weird concept, context: (that brings up an issue that still may be valid): if everyone bridged from one chain to the other, the bridge wallet would run out of native coins (right now we figure we'd sell "phantom-minted" tokens if we got close to running out). we'd need to bridge some native coins with a "real bridge" to replenish the system.
- the solution: the bridge you pay on is chosen pseudo-randomly with a cost that's a multiplier of the gas cost the bridge needs. "To clarify, the XDEX chooses which chain you will be paying on."
- if i'm not mistaken, our current solution has that capability, we just haven't thought about it explicitly: the "phantom-minted" tokens can be viewed as existing on any chain. so X->Y burns on X, the burned amount is "phantom-minted", if Z is about to run out of funds, we can mint on Z.
- started using ethers late 21/09
- catastrophe early 21/10
- was able to recover more lost TNGL from locked liquidity
- NFTs for those that were part of the cataclysm?
- refactoring XDEX with a flowchart (we did this for vertigo)
- intentionally took a programming course to become better, must have realized I was a bit out of my depth
- new job (the big one)
- new philosophy for XDEX: try to incentivize someone to make the exchange, their reward would be the funds on the origin chain. how would the blockchain on the origin chain know who/when to award? we put a blockchain in the origin chain smart contract that the trader locked their assets in. not proof of work? "the simulated block can only become real in the smart contract if a real block is produced. gas fees cover the cost of producing a real block. in some sense, gas fees (native coins) are equivalent to work. to send a block to the simulated blockchain, the gas cost required to send that block can be considered work.
	- (is that valid?)
- To make that work, we could make Tangle an NFT (my guess is specifically the kind with a non-1 supply). Tangle (batches?) can be tagged with the block with information that ties that Tangle to which block it came from. eventually, (honesty assumption) the length of the honest chain not including some bad block will exceed a dishonest chain (which does include some bad block). "merchants can wait for a certain number of (simulated) chain confirmations before disbursing a product.
- we then tried to figure out what consensus protocol we would use for the blockchain, which is odd because it almost sounded like we didn't need one at all. it was thought as "gas fees are you just paying for the work done, gas fees = work, gas is the consensus". PoG? you'd need to incentivize miners, miners would get paid somehow. there's also a major issue: what if it's concretely economically advantageous to lie about oneself being the fulfiller of another chain? say $0.10 in gas to submit a block and there's assets locked up worth $100 for some trade, you'd for sure lie to turn $0.10 into $100. the math (i think) says anyone could lie to turn $100 into $100 in that scenario, so if mining didn't give you $100, you'd have more liars.
	- metaphor/compare to BTC: say it's very little work to mine a BTC (pretend it's long ago). it's also very little reward. you can mine 10 a day. someone is offering a car worth $5k for 10 BTC. you mine 10 BTC in a day. you acquire or have or can pay up to $5k worth of capital that allows you to revert BTC the number of blocks the car seller will wait in confirmations. it's always profitable or even for you to send BTC to the car seller, get the car, then rewrite chain so the sell never happened (you start a fork where you send BTC to some other wallet controlled by yourself, then pump out blocks to prevent anyone from including your valid purchase in any future honest chain). every extra confirmation the seller requires exponentionally adds to the cost of this kind of attack.
	- could we not tie the confirmations required to release assets to some roughly estimated value of the assets? so the unlocker won't unlock unless your block is X blocks deep in the current longest chain?
	- this would mean that it takes longer to transfer larger sums of assets (not to mention someone on the other side is less likely to fulfill, so doubly longer)
- we seemed set on adding a proof-of-stake-like selection method, where there are 256 "buckets" (you are put into bucket log 2 X where X is what you've staked), we get a pseudorandom value to pick the validator bucket and the actual validator from the bucket
- not too long after, we hate proof of stake.
	- jesus christ: "Anyone who has the capability of acquiring money in any dishonest way can easily subvert a proof-of-stake blockchain. An extreme example is a government with a fiat monetary system printing money and using it to stake. They could do that instantly. They cannot produce a massive amount of cryptographically-verified work instantly."
	- similarly, any blockchain-within-a-blockchain cannot be trusted if the parent blockchain is not a proof-of-work chain
- a cool idea: traders can specify some "suspicion parameters" that, if met, could cancel, delay, or alter a trade. an idea would be "if the amount of work being done skyrockets, require a lot more work (the suspicion being that someone is attacking a PoW chain. if it's not an attack, then it'll just take a bit longer. if it is, then maybe an attack was just thwarted). 22/03
- hash list + using nodes as data storage: "you store the hashes of data in the smart contract storage and since the inputs are broadcast on the blockchain, you don't need any external storage for the contents of the hashed data, you just query any EVM node".
- customizable, generalized, abstract user interface generator for any smart contract.
	- (that sounds similar to the generalized, abstract, typescript module generator for any smart contract ABI)
- distracted by a side project
	- guess what it was? customizable, generalized, abstract EVM chain generator. fucking hell
	- even complete with "click to boot up a chain. click to add a dex (costs to maintain the web interface if opted into), click to add a bridge, click to add an explorer"
- did you just make a algorithmic short coin? (take the most liquid USD stable to native coin pair, positive rebases not affecting liquidity pool in proportion the drops in native coin price to usd). AKA, ETH goes down, shitcoin goes up. (AKA Ampleforth but instead of supply changes being arbitrary by some authority, we use on-chain data)
- open source block explorer blockscout is bad (monetize)
- starting to get into the BTC-like economic theory we think: "theoretically, the value of the reward token will equal the cost it takes to get the reward token" (at first, then the cost will equal the value). rewards for mining in whatever cross-chain system can be determined by looking at the token : native price and tracking the gas spent in whatever on-chain processes happen.
- ADISA (22/08) big gap to 22/12, supposedly keep rewriting, this time trying to test
  
>The end-game of the Simulator will involve many simulated users, miners, and attackers spread out amongst several development blockchains, all interacting with Tangle in real time

- genetic algo for finding trades to mine
- 23/02 new token
- very nice looking ui 23/03
- and we're caught up!
	- "what if the trader didn't specify the difficulty needed to move their funds?"
	- "what if the trader didn't create an "object" representing their funds locked by a puzzle, to be broken by miners and (hopefully) moved according to expectations?"
	- "what if the trader explicitly burns their funds with the expectation that honest miners will satisfy trade requests, with the burned funds funding a reward pool?"
	- "what if miners mined that reward pool and not any specific trade?"
	- "what if the miners just declared who should receive what amount of the mined rewards in order to fulfill trades?"
	- "what if we had a smart contract that allowed recipients to claim the rewards miners have declared for them given some X number of confirmations and pseudo-chain data?"
- responses:
	- what if there's no matching trade? honest miners before could just recreate the trade object to "refresh" it and destroy attacker work. hm. they did that because otherwise there's nothing for them to mine and so would leave trades to be attacked. here though, we eliminate that entirely, because miners mine a pool which never goes away. miners will ALWAYS be mining, they also don't need to switch or prioritize trades, which was a massive problem. Interesting proposal.


MASSIVE TL:DR

- orbicular was an experiment to prove an assumption made by ampleforth.
- (a bridge was wanted)
- a long-term vision arose from orbicular that saw a real and valuable purpose (on-chain zero-consensus flexible prediction market).
- tangle was an experimental project to see what could be done by incentivizing on-chain behavior.
- (we learn it is much easier to take on new ideas with an upgradeable smart contract)
- (a new web3 library respecting cross-chain activity was wanted)
- a long-term vision arose from tangle that saw a real and valuable purpose (cross-chain decentralized exchange).
- dizzyhavoc is a project intended to realize the goal of the cross-chain decentralized exchange.
- a long-term vision arose from dizzyhavoc that saw a real and valuable purpose (on-chain ERCs and an efficient contract deployer and manager service)

we think it is becoming more clear with organizing.
why are dizzyhavoc smart contracts in code/smartks/dizzyhavoc?
dizzyhavoc's smart contracts are something that needs to be abstracted. the contracts should stay there, but references to the `dizzyhavoc` should be removed and addresses as well. (we've unintenionally helped this a lot with the library replacement technique)
dizzyhavoc graph should contain smart contracts that are only the bare minimum of what's needed from the abstracted and generalized ones.
a setup pipeline in the dizzyhavoc graph should describe what makes dizzyhavoc what it is. (point to on-chain ERC20, point to on-chain ERC?, use this name, these addresses for these abstracted purposes, etc.)

to summarize: make the new ERCs, then use them as on-chain ERCs

had to rebuild git, thought bin/ was all i needed but it dumped some other things i deleted without really checking.
setting PREFIX in the Makefile for install to usr/ seems to make a hell of a lot more sense than HOME

new thing to abstract, context
```typescript
const smartks = (path: string) => fromFileUrl(import.meta.resolve(`smartks/${}`))

export const params: Params = {
    targets: { 'ERC20.sol': ['ERC20'] },
    basePath: smartks('dizzyhavoc/ERC20')
}
```
some function that takes a path and returns `fromFileUrl(import.meta.resolve(path))` would be more concise: `fn(path)`.
an extra generalization would be some function that takes a prefix and returns `fn(path)` where the path is always given the prefix. so instead of `fn(foo/A), fn(foo/B), fn(foo/C)` we could `fn1 = fn0(foo); fn1(A), fn1(B), fn1(C)`
check `denoland/std` to see if this exists

`format`?
import as fmt
`fn = (base) => format({ dir: foo, base }); fn(A), fn(B), fn(C)`
nah, needs path, we have fileUrl
hmm. it seems one cannot wrap import.meta.url with a function, then import that function from another module and use it so that the wrapped import.meta.url sees the module using the wrapped function as the "current" one
we don't think it's possible, so import.meta will need to be passed to this function
can use tag function thing for more concisesness:
`` const g = f(import.meta)`smartks` ``
`` g`A`, g`B`, g`C` ``
what is f? describe it
"a function `f` that takes import.meta and returns a string tag function `g` that expects one string in the first array. `g` returns a string tag function that also expects one string `path` in the first array. `g` will prepend a resolved prefix (relative to where g is created) as the dir of `path`"
uh
f = prefixer(ImportMeta)
g = prefix( \` string)
prefix might be too general, the prefix is import.meta.resolve'd.
import.meta.resolve - `A function that returns resolved specifier as if it would be imported using import(specifier)`
but we don't want a `specifier`, we want a path.
"A curried function that takes a path and prefixes it with a resolved path given some ImportMeta"
`(ImportMeta) -> pathToResolve -> somePath -> somePathRelativeToResolvedPathToResolve`
just rolls right off the tongue
`relativeFromResolved`

mixing currying and imperative functions can get very weird. given some function that ideally takes 3 inputs and returns one output, one could create a ton of functions that return other functions that eventually return the same sort of output, but every other function takes some unique combination of inputs

to figure out what we need, we know we want on output and we should note "for that output, what sets of inputs might i have", then we can create/derive the correct functions.
let's look at an example

given the top imperative function `iPR_f`, where `i`, `P`, `R` are inputs and `f` is an output.
we want `R_f`. We can then either create `iP_R_f`, `i_P_R_f`, or `P_i_R_f`. it'd probably make the most sense to choose the simplest imperative function, so we need to derive `iP_R_f`. we also notice that `i` and `P` internally combine such that we could make some new input `s` where `iP_s`. we don't necessarily need to do that, but that creates another set of possible functions. We also note more new inputs from internal transformations, such that `P_p` and `R_r`.
We also now want `R_R_f`. That's a bit weird and the derivation depends on what we're actually doing. Actually, it seems more accurate to say we want `iP_(R_f|R_(R_f|R_(R_f|R_(...))))`
imperatively, we want a function `j` that returns a string `f`, where `j.k` is a function that returns a new `j`, it may help then to derive some more inputs and functions.

`_j`, essentially, "a function that returns a `j` given no inputs". we know this is incorrect, but we don't know what the inputs should be yet.
we're fairly certain the outcome should look similar to below, with reasoning:
- `iP_R_f` should return some `j` equivalent to `iP_R_f` except `j.k` returns a new `j`
- `j.k` takes a new `R` `R1`, appends it to the original `R`, `R0` in some way, then returns the new `j`
  
```typescript
function _j() {
  const j = Object.assign(
    iP_R_f(i, P),
    { k: (R1: TemplateStringsArray) => _j(R0 + R1)}
  )
  return j
}
```

it's not a valid function, but it does return a `j` with `j.k` equaling a new `j` and appending `R1` to `R0`, so it's a good start.
to make it valid, we'll add `i`, `P` to `_j` and update it to `iPR_j`. the append doesn't exist for `R0` and `R1`, so we'll need to make that
we should change `R0` and `R1` to some other single char aliases. `A` and `B` we suppose
now we can make a function `AB_R`

woah, buncha weird realizations and things we were doing not so correctly:
There is no appending of two `R` types. We're making a new `j` from a new `R` type.
throw away `A`, `B`, and `AB_R`. `k` should be some `R` => `_j(R)`. this means we need to add `R` as an input to `_j` and more importantly means that `R` is some conditional input, since `_j` will only have an `R` if `j.k` is called

is that right?
let's back it up a bit, we were almost right but messed up, definitely.

- we want some `_j` that returns `R_f`.
- `j.k` should return some new `j`.
- the simplest function that returns `R_f` is `iP_R_f`, so we need at least `iP_j`

the new `j` should be created so that it's `P` is the previous `j`'s `P` with a new `R` appended, although this is a bit weird because `P` is really `[p]` and `R` is really `[r]` and we really want to append `r` to `p`, `P` and `R` are template string arrays, so the append doesn't quite exist.
also, `k` is now more of a `R_j` , so we'll change that name. abstractly, to append `R` to `P` we need some `(a -> a -> a) -> [a] -> [a] -> [a]` (given some function that appends the same type and two structures of that type, make a new structure of the same type where each element is the elements of the second structure appended to the elements of the first, respectively)
https://hackage.haskell.org/package/base-4.20.0.1/docs/Prelude.html#v:zipWith
we'll need to implement that.
done and tested
we did need to make an extra function to zip append two TemplateStringsArrays, since that is a special array with a `raw` property, which is another array
done

one last thing, `iP_j` doesn't particulary make sense since, in order for `P`, a TemplateStringsArray to be used, it must come first in a tag function. so this should be `i_P_j`

excellent, now the only thing is that we can see it being improved a bit more, so that `i_P_j` can also return a string
not possible, it cannot return something that acts as a string and a function. our guess is that primitives cannot ever be used as functions, even if we assign a function to one.
after some research, you cannot add, remove, or modify the "callability" of any object
even if we make a string, assign the string to a function, then set the prototype of the function to that of the string, we can't `a + b` to append, so it's fragile at best.
better to leave it as is then

what the fuck is it?
`i_P_j`, given an import.meta, returns `P_j`
`P_j`, given a path to resolve `P`, returns `j`
`j` is `iP_R_f(i, P) & { R_j }`
simplified, `j` is `R_f` with an optional `R_j` function property
`R_j`, given a relative path `R`, returns a new `j` as if `P_j` was given `resolve(P, R)`
`R_f`, given a relative path `R`, returns a resolved relative path

try more english:
`i_P_j` given an import.meta returns a function that can be used to resolve relative paths from base paths from the perspective of the location of import.meta
`P_j` is the same but the import.meta is "baked in". if exported to some other module, the importing module will be using the exporter's import.meta
`j` is the function with the "baked in" base path
`R_f` is `j`'s default function, which takes a relative path, resolves the base path with the import.meta (both are "baked in"), then resolves to the given relative path
`R_j` produces a new `j` whose "baked in" base path has been resolved to some relative path
in other words, you can create a `j` with a certain base path, then use that `j` to create new `j`'s with other base paths by relatively pathing using `R_j`
you can use any `j` to get a fully resolved path relative to that `j`'s base path

alright, what is this module generating thing?
code/deno/evm
yes
it is generalized deno evm code
what comes after that which would intuitively describe this?
right now we have contract/generate
"generates a deno evm contract"
does it do that?
is that what it should be?
we think so, in solidity you can say `contract.someFunction.selector` to get the selector
it does appear to not be well defined in the documentation. there are examples of accessing that selector member but no "one place" that says something like `function memebers: selector, etc.` despite that existing for errors and events. even weirder, using that in solidity works, but there is no type hinting for selector or for any other function memebers (are there any others?). if you hover over `selector` in `someFunction.selector` is just vaguely says `MemberAccess`.
We think contract/generate is right, but we also think we should find in the solidity source where this is. it'd probably be a very good resource for what else exists in a function (and a contract).
`deno/evm/contract/function`? where `deno/evm/contract/generate` uses something from the former? perhaps `function` contains something that can generate something else representing a contract function?

"https://paulgray.net/typeclasses-in-typescript/"
off track from finding function members, but we're suddenly curious how other languages handle overloads and overload-ish problems. apparently it's quite the issue.
we found a solidity issue open for **>6.5 years** and still open about how to get some specific overload. AKA we figure this out and our deno evm contracts will be more powerful than solidity contracts, which is a bit of a mind boggler

in rust, you can "overload the `+` operator with the `Add` trait". a number of operators that can be overloaded and their associated traits are in `std::ops`
"`traits` define the functionality a particular type has and can share with other types"
it's like a typeclass (haskell)
idea:

> what's the bare minimum needed to resolve a problem where the right overload cannot be determined? all one needs is the bare minimum of type assertions that can resolve whatever ambiguity exists. you don't need ALL the types, just the minimum that can resolve ambiguity

https://github.com/ethereum/solidity/blob/90c0fbb2eaafae95fae7785e4de5dfb43d5ddce3/libsolidity/ast/ASTAnnotations.h#L216
one of "slot", "offset", "length", "address", "selector" or empty

https://github.com/ethereum/solidity/blob/90c0fbb2eaafae95fae7785e4de5dfb43d5ddce3/libsolidity/analysis/TypeChecker.cpp#L850
variables of type function pointer only support "selector" and "address" suffix
only variables of type external function pointer support "selector" and "address"

functions are objects with `selector` and `address` properties. that's definitely not what we expected, but we kind of like that.

so, for any contract, if we want to use functions or get their selectors, we need a collection of function objects
interesting, someone put forward the idea of taking a common function name, `withdraw()`, finding a hash collision, putting that function `randomName` in the contract and changing `withdraw` to `Withdraw` in the contract. if you then distribute a bad ABI with `withdraw`, it'll call `randomName` and not `Withdraw`. if you were looking at the source and the bad ABI, it would be fairly hard to notice.
either way, it's a compilation error to have a selector collision.
interesting series of thoughts:
- ethers does `contract["fullSignature(foo bar baz etc)"](args)` and simplifies by having `contract.fullSignature` be the same as the former _if and only if_ there are no overloads for `fullSignature`. if there are overloads, `contract.fullSignature` doesn't exist at all and one needs to use the former.
- `contract["fullSignature"]["foo,bar,baz,etc"]` groups all overload signatures into one collection, then groups all functions into one collection (contract.fns or something)
- what if we have `c['f']['uint256']`, `c['f']['uint256,string']` (or `c.f.uint256_string`), and `c['f']['address']`? we'd want some way to be able to say `c.f(` and type hints would appear for the overloads. as we think of it now, we'd have `bigint;bigint,string;string` as the hints, let's make it harder: `bigint;bigint,string;bigint` where we change `c.f.address` to `c.f.uint8`. right now we're thinking either make the types be actual types `class UInt256` `class UInt8` style, or maybe there's some wildly magical and intuitive way to specify the bare minimum needed to disambiguate `c.f(3)`
- also remember "implicitly convertable to" and \_Generic.
- what if. what if
	- the generator created a \_Generic type switch
	- we made a list of typescript types and what solidity types they could be implicitly convertable to (`string` (if length and contents are right) implicitly convertable to `address`,  always to `string`, `bytes` (if length and contents are right), `bytesX` (if length and contents are right))
	- the generator created the full collection of functions as described above in `c.f.type0_type1` format
	- to populate the switch, we'd need to match the type of the expression with a case type. the type of the expression would be a collection of tuples, where every type has been substituted with the solidity types it can be implicitly converted to (so `c.f('0x...123)` would be a collection of tuples `[address],[bytes],[bytes20]` (one problem might be that `c.f(3)` would be `[uint8],[uint16],[uint24],...` which balloons quite a bit).
	  the case types would be tuples of the actual functions. say we had one `[address]` type. in that case, it would be trivial to pick the right one. but if our actual function types were `[address],[bytes20]`, then we couldn't resolve, although we would know precisely why. "arg 0 `0x...123` of c.f implicit conversion ambiguity with known c.f arg 0 types `[address],[bytes20]`". this is the minimal knowledge needed and would be true even if we implicitly derived `[address,uint256],[bytes20,uint256],[string,uint256]` and checked against `[address,uint256],[bytes20,uint256]`. it's the absolute bare minimum. "here's your bad arg, here's why it's bad (could be address or bytes20)", then suggest casting it. so `c.f(Address('0x...123'))`. if there's more than one arg? error would become quite large (also we [can't make custom invalid states](https://github.com/microsoft/TypeScript/issues/23689)), which sucks ass. also structs? `args: 0[1][3], 1[0], 2 implicit conversion ambiguity`. what if instead of `c.f('0x...123')` creating a collection of all the implicitly convertable tuples, it filtered the available ones?
	- what about precedence for implicit conversion? `0x...123` could be implicitly turned into `[address, bytes20, string]`. 
	- the most ideal system would provide a yellow squiggle warning `assuming arg0 0x...123 is address, could be bytes20,string. cast to remove ambiguity` if precedence could be assumed.
	- precedence of `uint8` vs `uint256` is a bit odd to think about, much less obvious than the address vs bytes20 vs string
	- let's think about `f(uint8)` and `f(uint16)`. our switch cases would be `[uint8]` and `[uint16]`. naively, we would say that the switch values could be `[bigint]` and `[bigint]`. \_Generic expects a match though, so we blow up the types to pick a match. this gives us: `[uint8],[uint16],[uint24],...` and `[uint8],[uint16],[uint24],...`
	- before we blow up the types, it's fairly obvious that we have two of the same thing: `[bigint]`.
	- hmm. new idea. what if we had class type objects `class UInt256`, started with the functions requiring those as its args, then reduced those to the simplified typescript types via some process, where if it was found that reducing would create ambiguity, then we simply just don't reduce? so `foo(uint,address)` and `foo(uint)` would become `foo(bigint,string)` and `foo(bigint)`, but `foo(uint8)` and foo`(uint)` would become `foo(UInt8)` and `foo(UInt)`?
	- that's kinda strange now we think about how solidity works. with `f0(uint8 x)` and `f0(uint16 x)` with both `internal`, when you make a new function and in it type `f0` you'll see two type hints. perfect, that's what we want.
	  
	-![[Pasted image 20240820190710.png]]
	
	- if you try `f0(3)`, you get an error. our solution would be to do `f0(uint16(3))`. this works. HOWEVER, `f0(uint8(3))` does not work. it doesn't work in solidity because it is implicitly convertable. if solidity was changed to make that work, then no `uint8` variable would ever be able to be plugged into a function that takes any `uintX` where X is greater than 8. honestly that doesn't sound so absurd. with our rules though, we reduce the specificity of x until reducing it further would introduce an ambiguity.
	- this is weird. in solidity, any `uintX` is implicitly convertable to any `uintY` where `Y > X`. what we're doing is very different. variables aren't ever implicitly convertable. however, function arguments are iteratively made "less specific" as long as doing so doesn't produce ambiguity.
	- imagine in solidity you type `function f0(uint16 x) internal {}` as the only function in a contract (useless, but bear with it). in order for the selector to not change, that type must not change. but somewhere in the background (the evaluator), the arg type allowed should disconnect with the defined function arg type as it iteratively makes it less specific. the selector would still use the defined function arg type, but whatever it puts in there (for arg validation, etc.) should depend on this new, disconnected type. we are poking around in the source code and have a hunch.
	- https://github.com/ethereum/solidity/blob/90c0fbb2eaafae95fae7785e4de5dfb43d5ddce3/libsolidity/analysis/TypeChecker.cpp#L3568
	- this is where the "No unique declaration" error text comes from. here, we start with an `_identifier`, we get an `annotation`, a property of the former, we check its `referencedDeclaration` property. if it exists, we get `overloadedDeclarations`, which equals `cleanOverloadedDeclarations`. we wonder what that function does. it errors if the overloads aren't function, event, or magic variable. it errors if !functionType. it errors if any parameter in parameterTypes or returnParameterTypes is false (these last two errors are real weird and seem to have never occurred from searching the text of those errors). `cleanOverloadedDeclarations` seems to only remove a declaration if it's parameters' types point to the exact same as what's already there, where type is a complex class that should be different between uint16 and uint8.
	- with those, it turns that into "candidates". `for each declaration, if variableDeclaration = dynamic_cast<decltype(variableDeclaration) then push declaration into candidates`. yes that is an = and not an \==, so we need to see what dynamic_cast and decltype do
	- let's say we have two overloads and only one arg.
	  to start off, we'd check if
	  `dynamic_cast<decltype(overload0Arg0)>(overload1Arg0) == nullptr
	  this has to be true, otherwise the two overloads would violate the "two functions with same parameter types" rule.
	  this is the "most specific"
	  next, we check if
	  `overload0Arg0->isImplicitlyConvertibleTo(overload1Arg0)` and
	  `overload1Arg0->isImplicitlyConvertibleTo(overload0Arg0)
	  if either is true, we have to use the more specific function. if both are false, we can now use this "less specific" function.
	  optionally, if this works, we could make it even less specific with `isExplicitlyConvertibleTo`
	- if we do this for all args of two overloads, we'll end up with a collection of functions which, if applied to the given args and each overload, will show one or zero overloads which can take the args. if one can take the args, we can add it to candidates.
	- we're wondering about three overloads. 
	- https://github.com/ethereum/solidity/blob/develop/libsolidity/ast/Types.cpp#L3390
	  functions have more member types, possibly
	- `f(uint8)` and `f(bytes1)` cannot implicitly convert into one another, so the least specific function is implicit conversion. 
	- so how would this work if we add `f(uint16)` and have 3 functions, and try to pass `0xff`. between `16` and `8`, the least specific is `dynamic`. between `8` and `1`, the least specific is `implicit`. between `16` and `2`, the least specific is `implicit`. it would then make sense to check the args against `16` and `8` with `dynamic`, `8` and `1` with `implicit`, and `16` and `1` with `implicit`. 
	- https://github.com/ethereum/solidity/blob/develop/libsolidity/ast/Types.h#L634
	- if we did this with `bytes2` and `0xffff`, we'd throw out `uint8` since we cannot implicitly convert to it. then, we'd use `implicit` against `16` and `2`, both would be candidates. we'd need to throw due to `no unique declaration`. we can cast to stop the throw, but we could do that before.
	- if we did this with `bytes2` and `0xff`, we'd throw out `2` since we cannot implicitly convert to it. then, we'd use `dynamic` against `8` and `16`. neither would be candidates, we'd need to throw due to `no matching declaration`. we now get the ability to cast like `uint8(0xff)` and it would not throw.
	- if we did this with `bytes1` and `0xff`, we couldn't throw any out. between `16` and `8` we use `dynamic`, neither are candidates. between `8` and `1` we use `implicit`, both are candidates. between `16` and `1` we use `implicit`, both are candidates. we feel like there are too many possibilities to chose now:
		  - do we throw `no matching declaration` on the first pair with no candidates?
		  - do we throw `no unique declaration` on the first pair with both candidates?
		  - do we discard overloads that aren't candidates if they are not a candidate at least once?
		  - do we add overloads to some pool if they are a candidate at least once?
	- it makes sense not to throw on the first pair because here `no matching declaration` is true for one pair and `no unique declaration` is true for another pair. it'd be not completely accurate to throw either of those. `no matching` is more like "no candidates in any pairs" and `no unique` is interesting. 
	- if we passed `uint8(0xff)`, in `16,8,d` we'd match with `8`. (we would probably return immediately because all `f` are `d`, so a match is a guarantee of the correct `f`). in `8,1,i` we'd match with `8`. in `16,1,i` we'd match with `16` (`8 (i)mplicitly 16`). here, it would make the most sense that we'd need to match with `8` only and preferably with some criteria that takes everything into account (later the immediate return would be introduced as an optimization). we'd discard overloads that were ever not a candidate.
	- elements A, B, C. pairs AB, BC, CA. maybe we need to look up about boolean algebra or ask GPT.
	- addresses and fixed bytes cannot be implicitly converted to one another. but if we had two overloads that took each of those `a` and `20`, the least specific function would then be `i`. if we passed `0x...123`, both would be candidates, it'd be an error.
	- https://en.cppreference.com/w/cpp/language/overload_resolution. go figure "pair-wise comparisons are applied to all viable functions"
	- "f1 is determined to be better than f2 if implicit conversions for all arguments of f1 are *not worse* than the implicit conversions for all arguments of F2, and there is at least one argument of f1 whose implicit conversion is _better_ than the corresponding implicit conversion for that argument of F2, or, if not that, \[100 other rules]". a _better_ implicit conversion is ranked, where exact matches are better than promotions which are better than conversions.
	- "If exactly one viable function is better than all others, overload resolution succeeds and this function is called. Otherwise, compilation fails."
	- https://en.cppreference.com/w/cpp/language/usual_arithmetic_conversions#Integer_conversion_rank

you're cracked, mate.
just solved general overload resolution without adding any syntax and adding a small amount of code. not sure what eldritch horrors that code creates, but we're fairly sure it's not too bad.
not only did we do that, but we did that when chriseth said he needed that years ago and he thought some new syntax was necessary.
we did that without syntax.
we did that with a fairly small amount of not very harmful (we hope) code that was just a bastardization of c++ overload resolution.
not only that, but we've never built solidity from source nor ever wrote anything in c++. you've also gone nearly 24 hours without eating, eat some fucking eggs you bozo.

now we have a new and weirder issue. two? one cannot `f.selector(uint, address)` although it would be really nice. why can one not do that?
- one: `f` : `No matching declaration found`. it makes sense, this is `f` with no args. actually, we hope it can be differentiated from `f` with no args since there's no parantheses. it should be the difference between `f` with no args and `f` whose args size is zero. if we can differentiate that, then we can match `f`.
- there's two places our error can be coming from. one is where were, and one is just above, and we don't quite understand it.
	- "if overloadedDeclarations.empty, fatal error"
	- "if overloadedDeclarations.size is 1, ref = ...begin"
	- "if !args block"
	- "if args block"
- so the question is: are we in the !args block or the args block? what is "annotation.arguments"? what is "annotation?" it's an "IdentifierAnnotation&" reference to IdentifierAnnotation. let's go visit the IdentifierAnnotation definition. it doesn't say anything about arguments, so let's see what it inherits: ExpressionAnnotation. it is optional and it is `Types and - if given - names of arguments if the expr. is a function that is called, used for overload resolution`. well it sorta says right there, "if is a function that is called".
- specifically: `std::optional<FuncCallArguments> arguments;`. messing around, noticed something probably very important: the message does in fact change with and without parantheses:
  `No matching declaration found after `<u>**variable**</u>` lookup.\n`. there's only one place that can be, and it's the weird place. it's !args block. our hunch was right. good job. the even have a comment there:
  `// The identifier should be a public state variable shadowing other functions`
  we want to add to this: `or a variable without arguments for selector lookup`.
  it seems the !args block is assuming you have some `uint x` shadowing some `function x`, and it's going through every declaration of overloadedDeclarations (every possible thing the identifier could be referring to) and filtering it to variable declarations only. not a fan of that.
  "a public state variable", which is sort of a function
  - the more we think about, the less that makes sense. the only overloadable identifiers are functions and events. a public state variable should never have overloaded declarations. either it has the same identifier as something else, but in a different scope, or if you try to make it have the same identifier as something else, you'll get an "identifier already declared" error.
  - in fact, if one googles "no unique declaration", they'll see a bunch of stuff about errors. if you then add `-dependent` to the search, ALL of the errors disappear. that error is not possible. that comment is not possible.
  - No matching declaration found after variable lookup with solc_release
  - now we get no unique after variable lookup, which is perfect.
  - TypeChecker.cpp#3586, we don't want an error here (at least not immediately), we think we want to check for selector access.
  `ast/ASTUtils.cpp:100):Type requested but not present`
  there we go, due to
  !\_expression.annotation().type where Expression::annotation is initAnnotation\<ExpressionAnnotation>. m_annotation is missing from ExpressionAnnotation
  what if instead of returning true we returned false?
- the problem is: we end up at the type checker for an identifier which needs a reference to a declaration-by-name like a variable or a function. we're there because we said `uint y = f` and `f` is an overloaded function.  IdentifierAnnotation is the type of the referenceDeclaration we need to return. not particularly true. IdentifierAnnotation is \_identifier.annotation which is passed into TypeChecker\<Identifier>.
- gcc takes a long ass time to compile. why did we compile gcc?
  we needed evmone to run the solidity compiler tests. why did we need to do that?
  we need to make sure that our changes don't break something or otherwise have some impact outside of our scope.
  why did evmone necessitate the compilation of gcc?
  evmone depends on libevmone.so, which requires the linker to be able to find GLIBCXX_3.4.32
  we're pretty sure this is g++, but a version that we don't we have
  not only do we not have it, but it's not something you can get from the package manager of a stable debian build.
  so, either we need an unstable debian build (which we also made some progress towards when realizing how long compiling gcc takes), or we need to compile a new version of gcc from source.
  supposedly, we can now set LD_LIBRARY_PATH to the path where the new libstdc++.so.6 is located within the gcc build
  ldd, given some thing (`libevmone.so`), tells us requirements. before, it told us
  `` version `GLIBCXX_3.4.32' not found ``
  now, it after setting LD_LIBRARY_PATH it does not tell us that
  so let's try test/soltest
  god damn, didn't work because it expects a lower version
  we got that lower version, now it says "running 8919 test cases". fun!
  oddly, it says "no errors detected"
  - there was no status or anything between running and done, so i'm not sure what it did
  - now we want to go back and fix our other overload resolution thing, but we may not do that, since we're more interested in the idea of a new "OverloadsType" representing function overloads similar to how we intuitively put similarly named and typed ABI elements into groups.
  - we want to save or record what we've done so far so we don't have to rewrite the logic from scratch.
  - we make a new branch with our modifications, go back to the develop branch, rebase hard to before our modifications, then make a new branch for our implementation of the new type.
  - we think it may be a composite type, like a struct or an array or a mapping
  - a composite type is just a type but with a fullDecomposition function and a decomposition function. these create lists of non-composite types from the composite type (roughly).
  - a tuple type looks nice, we may use that as the baseline. honestly we just copied it and changed the names, but that may be correct for now
  - now we think we should try and see how overloadedDeclarations gets populated. the idea is that we will find the source of this and alter its behavior so that whatever concept led to "annotation.overloadedDeclarations" existing for Identifier simply doesn't exist. (also check the other thing, member access). that comes from candidateDeclarations
  - `ReferencesResolver::vist(Identifier` 
    `auto declarations = m_resolver.nameFromCurrentScope(_identifier.name());`
    it seems that declarations will be the name from the current scope if it exists, or the name(s) from the closest parent scope. so if we try to access an overload, it fails to find name from current scope, checks parent scope, finds 3 names or something similar. if it finds 3 names, it adds all to identifier.annotation().candidateDeclarations
- it may be best to remove candidateDeclarations from ever being assigned to, then. we want to destroy the concept of identifier.candidateDeclarations. we think the next issue may be that ReferencesResolver is even visiting the Identifier type at all, preferably this should be our Overloads type.
- `libsolidity/parsing/Parser.cpp`, `parseContractDefinition`, checks token values, then does some `parseX` function. we're interested in `parseVariableDeclaration`. whoa, tried to recreate an error in the Parser so it'd show in Remix so we knew we where we were, but got a different error that led us to some completely other area. `test/libsolidity/` `SolidityParser.cpp` and `StandardCompiler.cpp`. no idea what these are. ah, wrappers to how users interact, this just uses `liblangutil/ParserBase`.
- we figured out how to recreate the error, but not entirely sure why it does that. error in question is if you put `function () {}` into a contract, you get `Expected a state variable declaration`. ahhh. if token is `function` and next token is not `(` (or if token is `constructor`, `receive`, or `fallback`), then it's a function declaration. otherwise, it's a variable declaration. in `parseVariableDeclaration`, if the type is `FunctionTypeName`, we have a variable declaration (`_options.kind == VarDeclKind::State`), and next token is `{`, then we throw that error.
  `function (uint) x;` is valid in a contract but i have no idea what that is or how one would use that.
  this is valid:
  ```solidity
  function () returns (uint) x;
  uint y = x();
  ```
  it seems here `x` is an uninitialized function type, so while that's valid, it reverts on deploy. the call `x()` reverts. debugging shows it sloads 0 (tries to get the function that's there), which indicates it tries to use that function (but fails because slot 0 is missing function info where function info would be, packed tightly, an address and a selector). it seems difficult to initialize since it "expects a primary expression" and we're not sure how to make one that returns a function type or if that's even possible.
 - there's two ways to get to our problem, either as a variable definition `uint x = f.selector;` or as a function definition `function foo() { f.selector; } 
   in parseVarDecl, if next token is Assign, value = parseExpression
   in parseFunctionDefinition, block = parseBlock
   in parseBlock, we continually parseStatement
   in parseStatement, if token is Identifier, parseSimpleStatement
   in parseSimpleStatement (for our purposes) it looks like we get parseVariableDeclarationStatement or parseExpressionStatement
 - at this point, we think `parseExpression` is where we want to be.
   actually this just returns `expression` (`ASTPointer<Expression>`)
   so for an `ASTPointer<VariableDeclaration>`, it's value is just `ASTPointer<Expression>`.
  - back up a bit. `std::tie(statementType, iap) = tryParseIndexAccessedPath();`
  - `expressionFromIndexAccessStructure
  - `typeNameFromIndexAccessStructure`
  - so far we think this all makes sense, but what happens after parsing?
    `interface/CompilerStack` `source.ast = parser.parse(`
    `parseAndAnalyze` (`imports`, `scopesetting`, `syntaxCheck`, `referenceResolving`, `typechecking`, `staticAnalysis`).
   - `CompilerStack::analyze()`
     resolveImports, assignScopes, checkSyntax, registerDeclarations, performImports, warnHomonymDeclarations, parseDocStrings, resolveNamesAndTypes, analyzeExperimental | analyzeLegacy
   - `libsolidity/analysis/ReferencesResolver` `visit(Identifier`
     nameFromCurrentScope
     `NameAndTypeResolver` `nameFromCurrentScope`
    
   
   
  