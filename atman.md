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
```
<???> ::= // some combination of the below
<concept> ::= <allowedUnixFilenameChars>
<kind> ::= "lib" | "types" | "schemas" | "tests" | "fixtures" | "templates"
```
- is there a markdown language for Backus-Naur form? when googling, we amusingly get a lot of content about Backus-Naur forms for markdown language.

i'm going to give in and use the existing plugin *for now*, as it seems to have a huge amount of downloads