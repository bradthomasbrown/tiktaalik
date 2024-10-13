A class of machine or programming languages consisting entirely of symbols that require 3 or more keypresses from the perspective of some culture's standard keyboard.

For example, on a Razer BlackWidow V3, a [[#QWERTY]] keyboard, we have the following symbols and the amount of keypresses required to enter them:

<table>
  <tr>
    <th>
       symbol
    </th>
    <th>
       keypresses
    </th>
     <th>
       notes
     </th>
  </tr>
  <tr>
    <td>
      a
    </td>
    <td>
      1 | 2
    </td>
    <td>
      depends on capslock
    </td>
  </tr>
  <tr>
    <td>
      A
    </td>
    <td>
      1 | 2
    </td>
    <td>
      depends on capslock
    </td>
  </tr>
  <tr>
    <td>
      ☺
    </td>
    <td>
      2
    </td>
    <td>
      alt n1
    </td>
  </tr>
  <tr>
    <td>
	   Ђ
    </td>
    <td>
      5
    </td>
    <td>
      alt +,n4,n0,n2 with hex numpad enabled on windows
    </td>
  </tr>
</table>

So in our machine or programming language, the symbols `a`, `A`, and `☺` would be forbidden as language symbols, but `Ђ` would be permitted. The purpose is that writing a specification for or programming in the language with the targeted keyboard class would have the following tradeoffs:
- One can almost or certainly freely type anything they can, with ease, without running into a conflict with a language keyword.
- However, the keys required for any keyword are, in this case, possibly a minimum of 5 (since for any count of `nx` less than the pattern `alt +,nx,nx,nx` seems to produce a symbol that visually or explicitly conflicts with symbols requiring fewer than 3 keypresses we might say the practical minimum is 5).

There is an unnamed concept for a new language that allows "switching" between languages, as well as concepts to explore conceptually the idea of programming languages and how they relate.
For example, TypeScript is a superset of JavaScript, so every JavaScript program is a valid TypeScript program (simplifying). There is a clear "super/sub" relation here.
JSX is JavaScript but can also "switch" into HTML or CSS. There's some "switch" relation here.

Languages may also have "language servers" a concept that might specifically be for some IDEs but could be thought of or made more general.

Langauges may also be "extensible" or not, where most or all current languages appear to be not extensible at all (by "extensible" we mean that there is some straightforward-ish process to modifying or extending the language, or even removing parts of it, such that the language is very modular and flexible). We may take this concept to extremes by thinking of existing languages or new languages where we take out or add single parts. For instance, imagine JavaScript without the `for` keyword, so no `for` loops. `for` could then be thought of as a "piece" of a conceptually modular version of JavaScript, and perhaps with many "pieces" one can build JavaScript (or any language). Pieces are more digestible and could be shared, and perhaps anyone could take any arrangement of pieces and build a language more suited to their own tastes and needs.

Languages may also have "engines" and "runtimes" and IDEs (with language servers) may run programs constantly (as the user types) and provide visual feedback to users indicating any errors.

Languages may have "type systems" (which we conjecture are just "higher languages" and also "less computationally well-founded" languages) that can be "run" like a program and likewise an IDE (with a language server) may run it constantly (as the user types) and provide visual feedback to users indicating any errors. Currently, we are under the impression that all langauges only have one "higher language" (the "type system"), but we think there could be potentially many more than just one (where each higher language is more generalized and can express more in fewer symbols but is less computationally well-founded and thus cannot perfectly express the program). There may be different "classes" of type systems (dependent, etc.).

We like Deno, the ease of setup and ease of use, the language server it provides (where we use it with the VSCode IDE), and how the type system (via TypeScript) can capture meaning of parts of the program and catch some errors.

Languages usually have some distinct style (Imperative, Functional, Logic, Aspect, Object, etc.). Perhaps there is merit in which the style of a language can be switched or the language is flexible enough to support multiple/all styles (especially if it's extensible).

A new and ideal language should not assume it is "the superior language" and it should proactively work with other languages (sufficient extensibility may provide a framework where this is "built-in").

Machine code is conjectured to be the most computationally well-founded and thus perhaps most superior language (in the perspective of computationally well-founded languages).

Metrics for a language are important and underrated, or at least that is our impression. It should be straightforward to determine what metrics exist and how to measure them for any part of the language in a program. (how much CPU time is spent in this line of code? in this function? (for some program run or runs) how much did memory usage increase from this or that? how much did storage usage increase? decrease? "type instantiation count" and "type recursion depth" for TypeScript - with Deno it is not straightforward to determine this for any segments of code. (metrics from arbitrary line to arbitrary line, inclusive or exclusive))

For a language with a type system and a language server for some IDE, the displayed type might not be immediately obvious or might have been some "calculated type". It would be useful to have an option to where one can see how that type "came about". Since types could be thought of as a higher computational language, types could be "optimized" (and we might want to see what the optimization steps are, since that could allow us to write better/more optimized types).
### QWERTY
A keyboard layout for Latin-script alphabets.

