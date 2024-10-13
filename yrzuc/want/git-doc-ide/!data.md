we want some sort of unified system for producing documentation, taking notes, and functioning as an IDE

a huge order, for sure, especially since we want it to be somewhat web-accessible or web-exportable.

some of the features of the ideal system
- we can take notes like obsidian, an extensible system that natively has markdown rendering
	- but perhaps we could have other types of rendering, like TeX systems (which obsidian has a plugin for)
	- or perhaps much more flexible types of rendering, where rendering is controlled by programs (obsidian might have this for JavaScript, we haven't looked too far into it, but we wonder what the limits can be)
- we can do what we think one can do with Jupyter notebooks, where we essentially have little program blocks that can be run as the programs the code within them represents (we think this is what it does). this works off of an extensible "kernel".
	- something we don't think that can do though, is "export" a code block and its results along with some of the features of a language server, such that we can "bake" a code block and put it in some web-accessible format, where someone could then see the code block and "hover" over parts of it and see hinting and popups like it were code in an IDE with a language server
- VSCode allows ctrl-click jumping for definitions and multidefinitions or implementations of things or symbols, and we want as a feature the ability to do this and similar things but arbitrarily according to some given rules. for instance, if we're writing mathematical documentation, it would be extremely neat if we could hover over a mathematical symbol and see a popup hint (customizable if this happens and how) explaining it, or ctrl click it or some other combo to see its definition or where else it is used

if we could also actually program in this system, it would be a sort of total unification of note taking, IDE, and documentation/specification/standard/formal paper writing
(although we know by unification our other concepts dictate that it must be a framework where these pieces are modules of some framework)

throw git somewhere into the mix as well, so we can interop with repos (and so we can have some repo which also has code and documentation with any sort of rendering, "rich repo")