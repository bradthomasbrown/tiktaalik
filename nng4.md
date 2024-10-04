https://adam.math.hhu.de/#/g/leanprover-community/nng4


https://ncatlab.org/nlab/show/equality
rfl - "reflexivity of equality"
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=30

>A last difference between type theory and set theory is the treatment of equality. The familiar notion of equality in mathematics is a proposition: e.g. we can disprove an equality or assume an equality as a hypothesis. Since in type theory, propositions are types, this means that equality is a type: for elements a, b : A (that is, both a : A and b : A) we have a type “a =A b”. (In homotopy type theory, of course, this equality proposition can behave in unfamiliar ways: see §1.12 and Chapter 2, and the rest of the book). When a =A b is inhabited, we say that a and b are (propositionally) equal.

### YRZUC (we do not fully understand)

we believe we understand the notion that an equality can be disproved or assumed as a hypothethesis. we can say "1 = 2" and that can be disproved or assumed as a hypothesis (which we then may try to prove or disprove). 

"propositions are types". what are types? set theory has sets and propositions, type theory has types. propositions are identified with particular types. So a type is a fundamental object of type theory, something we must accept is a "thing" at face value.

>Thus, the mathematical activity of proving a theorem is identified with a special case of the mathematical activity of constructing an object—in this case, an inhabitant of a type that represents a proposition.

Types can be "inhabited". so types can "be inhabited" and presumably `?` "can inhabit a type". since type theory has types as the "one basic notion", we presume that `?` is also a type. types can inhabit other types. "constructing an object" seems to be referring to the creation of a type.

>Informally, a deductive system is a collection of rules for deriving things called judgments. If we think of a deductive system as a formal game, then the judgments are the “positions” in the game which we reach by following the game rules.

We believe we understand this. From what I understand of basic school algebra, we can take `a + b = c + b` and subtract `b` from both sides, like `a + b - b = c + b - b`, then cancel out `b`, like `a = c`. We believe then that the two expressions following the first are "judgments" that we have derived from the "rules" we were taught in basic shool algebra (you can add the same thing to both sides of an equality and its' still equal, + x - x can be "cancelled out", etc.).

>In the deductive system of first-order logic (on which set theory is based), there is only one kind of judgment: that a given proposition has a proof.

What exactly is a proposition? `The familiar notion of equality in mathematics is a proposition: e.g. we can disprove an equality or assume an equality as a hypothesis.`
Basically, it seems that's the "previous definition (first-order-logic)" and that now we must assume it's a `type` with presumably some inhabitants.

>That is, each proposition A gives rise to a judgment “A has a proof”, and all judgments are of this form. A rule of first-order logic such as “from A and B infer A ∧ B” is actually a rule of “proof construction” which says that given the judgments “A has a proof” and “B has a proof”, we may deduce that “A ∧ B has a proof”. Note that the judgment “A has a proof” exists at a different level from the proposition A itself, which is an internal statement of the theory.

So in first-order-logic, propositions are `an internal statement of the theory`, perhaps a fundamental object taken to exist at face value. In first-order-logic, propositions are rules from which judgments are derived, these judgments are always of the form `A has a proof` where `A` is a proposition.
We wanted to verify that interpretation at https://en.wikipedia.org/wiki/First-order_logic, but found that first-order-logic is something distinguishable from `propositional logic`, which means we may be dealing with two different definitions of a `proposition`.
https://en.wikipedia.org/wiki/Propositional_calculus
`The propositional calculus`, `propositional logic`, `statement logic`, `sentential calculus`, `sentential logic`, `zeroth-order-logic` deals with `propositions` which can be true or false and relations between propositions including the construction of arguments based on them. Compound propositions are formed by connecting propositions by logical connectives (AND, equivalent, implies, NAND, etc.).
So, in zeroth-order-logic, a proposition seems to be a true or false declaration
In first-order-logic a proposition seems to be an expression from which one can derive judgments in the form of "has a proof". 
In type theory, `there is only one basic notion: *types*`, and so presumably a proposition is a type or is derived from types.
This presumption is confirmed by the earlier quote from the text: `in type theory, propositions are types`.
The basic judgment of type theory, or what we can derive `is written "a: A"`. The text gives an analogy, but we have a notion the analogy is harmful. If we want to fully understand, we must not use an analogy and use only the definition.

>In homotopy type theory, we regard the types as “spaces” (as studied in homotopy theory) or higher groupoids, and the logical constructions (such as the product A × B) as homotopy-invariant constructions on these spaces.

https://ncatlab.org/nlab/show/homotopy+theory
Homotopy theory is a study of mathematical contexts in which...
For now, we'll not go further but accept that a "space" is a mathematical context in homotopy theory, and thus, a type is a mathematical context. 

>In this way, we are able to manipulate spaces directly without first having to develop point-set topology (or any combinatorial replacement for it, such as the theory of simplicial sets). To briefly explain this perspective, consider first the basic concept of type theory, namely that the term a is of type A, which is written: a : A. This expression is traditionally thought of as akin to: “a is an element of the set A”. However, in homotopy type theory we think of it instead as: “a is a point of the space A”.

So perhaps we should use the term "space", the book seems to prefer it to "mathematical context". The judgment `a: A` in HoTT is thought as "a is a point of the space A", where "space A" is also "type A" or just "A". "a" is a term. `term a` is of `type A`. We presume then that terms are types, since `there is only one basic notion: *types*`. Since types can be inhabited, we presume we can say `a inhabits A` or `A is inhabited by a`.

>a, b : A (that is, both a : A and b : A)

Convenient notation.

>equality is a type: for elements a, b : A (that is, both a : A and b : A) we have a type “a = A b”.

In the text `we have a type “a = A b”.`, A appears to be a subscript suffix to `Equals Sign`.
### YRZUC (we copied from the text and the pasted result here is not the same. we lost some information)
### YRZUC (`Equals Sign` specifically refers to the unicode symbol with value U+3D, `=`. Specific references to symbols. We do not know the specifc reference to the symbol in the text. In https://symbl.cc/en/unicode/blocks/phonetic-extensions/#subblock-1D2C, there is Latin Letter Small Capital A, `ᴀ`, there is Latin superscript modifier letter Modifier Letter Capital A, but apparently no subscript captial A. What do we do about the text's subscript capital A? We could try to find a workaround like an extension for LaTeX (is LaTeX what would help?). We tried looking for a unicode symbol. We could find another software or try to make our own. We won't be able to express subscript capital A in most software or via hex numpad unicode. We wish they hadn't used that symbol. Do we make up our own notation to concisely describe LaTeX? symbols via unicode? We installed a LaTeX extension. We don't know how express the symbol still. Learn some LaTeX. LaTeX has software. Should we be using that? It's a language. It's a machine. From machine theory, we presume... Or do we make a proposition? A type? We're not sure if that makes sense. For now, we presume a familiar notion: we do not need all of LaTeX to express what we want, we just need *enough*. We presume a triviality: We map a single unicode point to LaTeX subscript capital A. Which is easier, faster, most intuitive? LaTeX or our mapping? Or perhaps we map a single unicode point to a subscript modifier. https://www.latex-project.org/help/documentation/. The word "subscript" does not appear in the documentation? Bizarre. Documentation may be for software. The extension we installed must map to something, in that area should be the possibilities, from that we could find the possibility matching our needs. Frustrating. We search `how do i subscript something in latex`. Brave's Leo AI amalgamates responses from non-official resources. Use an underscore. `$$A=_Ab$$` produces the accurate representation. Seems unpleasant that such a simple need was so complex.)
$$A=_Ab$$
### YRZUC (The idea of the mapping might be one wherein I have a system or software that allows me to use Unicode code points and perhaps it is written in Unicode code points and rendered "as if" LaTeX, but there would be an option to export as LaTeX. Although, I imagine that a single underscore cannot be made more concise. However, an underscore seems like a character that may appear otherwise, as it is a standard English keyboard character. Notion: Standard English keyboard characters might not be the best choice for language-specific syntax symbols, as they inherently make it so one using a standard English keyboard has a more restrictive "symbol-space" to work in. `A: A language wherein all immediate symbols on one's keyboard are unrestricted or unreserved is such that one may type anything possible and not encounter errors`. How freeing that may be. Perhaps an exercise would be to iteratively build such a programming language and see how it feels to use. Is `A` a novel concept? If one can make software that can alter any keyboard behavior, one could use software to completely redesign what the keyboard does. A fleeting notion of east Asian calligraphic orthography, or at least my minimal understanding: Symbols consist of parts, strokes, etc. Keys could be mapped to strokes, and symbols could be composed via many strokes. Extension of the notion is complete abstraction away from existing symbols such that new symbols could be defined as arbitrarily anything and remapped keyboard input could build those "things".)


> equality is a type: for elements $a, b : A$ (that is, both $a : A$ and $b : A$) we have a type $a=_Ab$

Ah, just single dollar signs can be used to inline. That is much nicer.

>When $a =_A b$ is inhabited, we say that $a$ and $b$ are **(propositionally) equal**.

>However, in type theory there is also a need for an equality *judgment*, existing at the same level as the judgment "$x : A$". This is called **judgmental equality** or **definitional equality**, and we write it as $a \equiv b : A$ or simply $a \equiv b$. It is helpful to think of this as meaning "equal by definition". For instance, if we define a function $f : \mathbb{N} \to \mathbb{N}$ by the equation $f(x) = x^2$, then the expression $f(3)$ is equal to $3^2$ *by definition*. Inside the theory, it does not make sense to negate or assume an equality-by-definition; we cannot say "if $x$ is equal to $y$ by definition, then $z$ is not equal to $w$ by definition". Whether or not two expressions are equal by definition is just a matter of expanding out the definitions; in particular, it is algorithmically decidable (though the algorithm is necessarily meta-theoretic, not interal to the theory).

>Alternatively, if we regard a deductive system as an algebraic theory, then judgmental equality is simply the equality in that theory, analogous to the equality between elements of a group $-$ the only potential for confusion is that there is *also* an object *inside* the deductive system of type theory (namely the type "$a = b$") which behaves internally as a notion of "equality".

### YRZUC (https://detexify.kirelabs.org/classify.html lets you search LaTeX symbols by drawing them. Very neat. https://github.com/artisticat1/obsidian-latex-suite/blob/main/src/default_snippets.js is the mapping we presumed exists for the plugin. We can see that `===` should map to the three vertical line equals, or LaTeX `\equiv`, $\equiv$. It didn't map. Odd, perhaps we need some setting.)

>The reason we *want* a judgmental notion of equality is so that it can control the other form of the judgment, "$a : A$". For instance, suppose we have given a proof that $3^2 = 9$, i.e. we have derived the judgment $p : (3^2 = 9)$ for some $p$. Then the same witness $p$ ought to count as a proof that $f(3) = 9$, since $f(3)$ is $3^2$ *by definition*. The best way to represent this is with a rule saying that given the judgments $a : A$ and $A \equiv B$, we may derive the judgment $a : B$.

### YRZUC (we are unsure of the meaning of "proof", what $p$ is, and the meaning of "witness")

Notion: In first-order-logic, propositions are made and judgements are derived in the form "P has a proof". Was not the HoTT concept for that $a : A$?

> The basic judgment of type theory, analogous to “$A$ has a proof”, is written “$a : A$”

It is, we had just omitted the analogy earlier. We presume then that $p$ is a term. $p : (3^2 = 9)$ is then interesting: $3^2 = 9$ is a type. We presume $p : (3^2 = 9)$ is equivalent to $p$ is point in the space $3^2 = 9$, in accordance to:

> To briefly explain this perspective, consider first the basic concept of type theory, namely that the term $a$ is of type $A$, which is written: $a : A$. This expression is traditionally thought of as akin to: “$a$ is an element of the set $A$”. However, in homotopy type theory we think of it instead as: “$a$ is a point of the space $A$”.

The use of the term `witness` is interesting. Contextually, we presume the following are equivalent:
- $p$ is a witness of $3^2 = 9$
- $p$ is a point in the space of $3^2 = 9$
- $p$ inhabits $3^2 = 9$
- $3^2=9$ is inhabited by $p$
- $3^2 = 9$ has witness $p$
- $3^2 = 9$ is a space containing point $p$

Summary:

1. $Type$
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=29
>Instead of the two basic notions of set theory, sets, and propositions, type theory has one basic notion: *types*.
2. $Space$
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=15
>Homotopy type theory (HoTT) interprets type theory from a homotopical perspective. In homotopy type theory, we regard the types as "spaces" (as studied in homotopy theory) or higher groupoids, and the logical constructions (such as the product $A \times B$) as homotopy-invariant constructions on these spaces.
3. $Term$, $Point$
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=15
>To briefly explain this perspective, consider first the basic concept of type theory, namely that the *term* $a$ is of *type* $A$, which is written $a : A$... in homotopy type theory we think of it ... as "$a$ is a point of the space $A$".
4. $Universe$
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=16
>In type theory, one can have a type whose elements are themselves types; such a type is called a *universe* and is usually denoted by $\mathcal{U}$. Those types that are terms of $\mathcal{U}$ are commonly called *small* types.
5. $Proposition$
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=20
>In type theory, we represent mathematical statements by types, which can be regarded simultaneously as both mathematical constructions and mathematical assertsion, a conception also known as *propositions as types*. Accordingly, we can regard a term $a : A$ as both an element of the type $A$ (or in homotopy type theory, a point in the space $A$), and at the same time, a proof of the proposition $A$.
6. $Rules$, $Judgments$
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=29
>Informally, a deductive system is a collection of **rules** for deriving things called **judgments**. If we think of a deductive system as a formal game, then the judgments are the "positions" in the game which we reach by following the game rules... The basic judgment of type theory, analogous to "$A$ has a proof", is written "$a : A$" and prounounced as "the term $a$ has type $A$", or more loosely "$a$ is an element of $A$" (or, in homotopy type theory, "$a$ is a point of $A$"). 
7. $Witness$, $Evidence$
https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=29
> When $A$ is a type representing a proposition, then $a$ may be called a *witness* to the provability of $A$, or *evidence* of the truth of $A$ (or even a *proof* of $A$, but we will try to avoid this confusing terminology).

### YRZUC (this is confusing. `one can have a type whose elements are themselves types`. `type theory has one basic notion:  *types*`. would it not then be nonsensical to "have a type whose elements are *not* types"? if so, then the first statement is redundant. otherwise, the second statement is false.)

>Since in type theory, propositions are types, this means that equality is a type: for elements $a,b : A$ (that is, both $a : A$ and $b: A$) we have a type "$a =_A b$". (In *homotopy* type theory, of course, this equality proposition can behave in unfamiliar ways...). When $a =_A b$ is inhabited, we say that $a$ and $b$ are **(propositionally) equal**

This makes more sense now. $a =_A b$ is a type variant representing a proposition, if it is inhabited or contains points, those points are "witnesses" or "evidence" of the proposition. With "evidence", it's propositionally true. In this case, since it's roughly about equality, $a$ and $b$ are propositionally equal.

>However, in type theory there is also a need for an equality *judgment*, existing at the same level as the judgment "$x : A$". This is called **judgmental equality** or **definitional equality**, and we write it as $a \equiv b : A$ or simply $a \equiv b$. It is helpful to think of this as meaning "equal by definition". For instance, if we define a function $f : \mathbb{N} \to \mathbb{N}$ by the equation $f(x) = x^2$, then the expression $f(3)$ is equal to $3^2$ *by definition*.

>The reason we *want* a judgmental notion of equality is so that it can control the other form of judgment, "$a : A$". For instance, suppose we have given a proof that $3^2 = 9$, i.e. we have derived the judgment $p : (3^2 = 9)$ for some $p$. Then the same witness $p$ ought to count as a proof that $f(3) = 9$, since $f(3)$ is $3^2$ *by definition*. The best way to represent this is with a rule saying that given the judgments $a : A$ and $A \equiv B$, we may derive the judgment $a : B$.

$x : A$
$a \equiv b : A$ or $a \equiv b$ (`we write definitional equality as`)
$f : \mathbb{N} \to \mathbb{N}$ defined as $f(x) = x^2$

>$f(3)$ is equal to $3^2$ *by definition*

substituting examples for definitions, we get:

$a$ is $f(3)$
$b$ is $3^2$
$f(3)$ is equal to $3^2$ *by definition*, and we write it as $a \equiv b : A$
$f(3) \equiv 3^2 : A$

what is $A$?
If $f(x) = x^2$ is a proposition, then from

>When $A$ is a type representing a proposition, then $a$ may be called a *witness* to the provability of $A$.

we presume

$f(3) \equiv 3^2 : f(x) = x^2$

but $f$ is defined, and if it's defined we presume it's not a proposition, therefore $A$ is not $f(x) = x^2$
what is $A$?

questions

if $a$ is $f(3)$ then $a :\ ?$
if $a$ is $f(3)$ then $f(3) :\ ?$
if $b$ is $3^2$ then $b:\ ?$
if $b$ is $3^2$ then $3^2:\ ?$

when writing $a \equiv b : A$, is that syntax specifically and only `definitional equality` or is that also a point in space, where $a \equiv b$ is a point in $A$?

### YRZUC if $A$ is a proposition where $a \equiv b$ is a witness or evidence, what would $a \equiv b$ be a witness or evidence of?

We presume a type "$a \equiv_A b$".
Analogous to `equality is a type`, this presumed type is `definitional equality`.

>When $a =_A b$ is inhabited, we say that $a$ and $b$ are **(propositionally) equal**.

Therefore, we presume that the above statement is equivalent to "when $a$ and $b$ are **(propositionally) equal**, we say $a =_A b$ is inhabited".

Therefore, we presume that when $f(3)$ and $3^2$ are **(definitionally) equal**, we say $f(3) \equiv_A 3^2$ is inhabited.

### YRZUC we must find the definition of "inhabits"

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=29
>Thus, the mathematical activity of *proving a theorem* is identified with a special case of the mathematical activity of *constructing an object*—in this case, an inhabitant of a type that represents a proposition.

$f(3) \equiv_A 3^2$ is inhabited. If $f(3) \equiv_A 3^2$ were a proposition or theorem, it would be proved by constructing an object, which would be its inhabitant.

$? : f(3) \equiv_A 3^2$

Or, more generally,

$? : f(x) \equiv_A x^2$

Let's call $?$ $foo$.

$foo : f(x) \equiv_A x^2$

Now, it is inhabited, and is therefore "proved", with $foo$ as a witness.

We still wonder,
what is $A$?
We also now wonder,
what is $3$?

$f : \mathbb{N} \to \mathbb{N}$ defined as $f(x) = x^2$

We presume when we say "$a : A$ defined as $b$", we can write "$a \equiv_{A} b$".

Therefore,

$f \equiv_A f(x) = x^2 : A$
what is $A$?

Let's call $A$ $Bar$

Thus
$f \equiv_{Bar} f(x) = x^2 : Bar$,

Back to our presumed type,
$a \equiv_A b$

By the `OBN`, everything is a type.

>Since in type theory, propositions are types, this means that equality is a type: for elements $a,b : A$ (that is, both $a : A$ and $b : A$) we have a type "$a =_A b$".

YRZUC The text supposed that (propositional) equality is a proposition. We presume then that definitional equality is a proposition. Therefore, we can or perhaps should say that its inhabitants are witnesses. Prefer witness to evidence.

YRZUC Distinctualize. When we say propositional equality, we can write $=$. When we say definitional equality, we can write $\equiv$. In English, we can respectively write $peq$ and $deq$ or respectively $equal$ and $equivalent$.

Since type $a =_A b$ and $a : A$ and $b : A$ or $a,b : A$, and since `OBN`, we presume $A$ is a $Universe$.

We presume $\mathbb{N}$ is a type.
We presume $3$ is a type.
We presume $3 : \mathbb{N}$, which is a type.
We presume $3^2 : \mathbb{N}$ and $9 : \mathbb{N}$ as well.
We presume $3,3^2,9 : \mathbb{N}$, $\mathbb{N}$ is a $Universe$.

YRZUC Shorthand or notation for type / object construction.
YRZUC We should say type, not object, per the `OBN`.
YZRUC Shorthand or notation for presumptions. Presumptions are hypotheses. Presumptions are propositions. Is that correct? If so, that language can be subsumed by HoTT. Propositions are types.

If a universe is a type that contains types, perhaps we can "construct" $\mathbb{N}$ like $\mathbb{N} : \mathcal{U}$. ^c72545

>.    However, the main difference between the presentation of type theory in the book and in this appendix is that here judgments are explicitly formulated in an ambient **context**, or list of assumptions, of the form $$x_{1} : A_{1},x_{2}: A_{2},\dots,x_{n} : A_{n}.$$An element $x_i : A_i$ of the context expresses the assumption that the variable $x_i$ has type $A_i$. The variables $x_1,...x_n$ appearing in the context must be distinct. We abbreviate contexts with the letters $\Gamma$ and $\Delta$.
>.    The judgment $a: A$ in context $\Gamma$ is written $$\Gamma \vdash a : A$$and means that $a : A$ under the assumptions listed in $\Gamma$. When the list of assumptions is empty, we write simply $$\vdash a : A$$or $$\cdot \vdash a : A$$where $\cdot$ denotes the empty context. The same applies to the equality judgment $$\Gamma \vdash a \equiv b : A$$.    However, such judgments are sensible only for **well-formed** contexts, a notion captured by our third and final judgment$$(x_{1} : A_{1},x_{2} : A_{2},\dots,x_{n} : A_{n})\ \text{ctx}$$expressing that each $A_i$ is a type in the context $x_1 : A_1,x_2 : A_2,...,x_{i-1} : A_{i - 1}$. In particular, therefore, if $\Gamma \vdash a : A$ and $\Gamma\ \text{ctx}$, then we know that each $A_i$ contains only the variables $x_1,...x_{i-1}$, and that $a$ and $A$ contain only the variables $x_1,...x_n$.

### YRZUC $\Gamma$ (Gamma). $\Delta$ (Delta)

We just found way later in the text how the text constructs $\mathbb{N}$. Note, this is just the formation rule of the type itself, there are a lot of other rules near it. For instance $\mathbf{N}\text -\scriptsize INTRO_1$ and $\mathbf{N}\text -\scriptsize INTRO_2$ are the classic Peano rules defining zero and the successor function. There is also an elimiation rule and two computation rules.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=449
>$$\frac{\Gamma\ \text{ctx}}{\Gamma \vdash \mathbb{N} : \mathcal{U}_{i}}\mathbb{N}\text{-}\textbf{\scriptsize FORM}$$

YRZUC Appendix A of the HoTT text is the formal theory, and we have wound up there. It appears that **judgmentally equal** is used instead of "definitionally equal".

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=438
>In Chapter 1, we presented the two basic **judgments** of type theory. The first, $a : A$ asserts that a term $a$ has type $A$. The second, $a \equiv b : A$, states that the two terms $a$ and $b$ are **judgmentally equal** at type $A$.

YRZUC we find it interesting that the terminology here is `at type A`. We haven't seen that before (yet?)

>To construct an element $a$ of type $A$ is to derive $a : A$; in the book, we give informal arguments which describe the construction of $a$, but formally, one must specify a precise term $a$ and a full derivation that $a : A$.

YRZUC we find it some combination of fascinating, ironic, frustrating, and bizarre that we have found ourselves at the back end of the text in order to fully comprehend things, before we've moved past the very beginning of the text, much like the Ethereum Yellow Paper. why can't people just put information in a text in the order in which one learns? why must i jump around in order to understand?

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=440
> The equality judgment $t \equiv u : A$ is then derived by the following single rule:$$\text{if}\ t : A, u : A,\text{and}\ t \downarrow u, \text{then}\ t \equiv u : A$$

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=440
> **Convertibility** $t\downarrow t'$ between terms $t$ and $t'$ is the equivalence relation generated by the defining equations for constants, the computation rule$$(\lambda x.t)(u):\equiv t[u/x]$$and the rules which make it a *congruence* with respect to application and $\lambda$-abstraction:
> - if $t \downarrow t'$ and $s \downarrow s'$ then $t(s) \downarrow t'(s')$, and
> - if $t \downarrow t'$ then $(\lambda x.t)\downarrow(\lambda x.t')$.

YRZUC So far it seems that $:\equiv$ is a given operator, or rather a metatheoretic shorthand for simply saying "a is b" (a $:\equiv$ b), and as such, *shouldn't* (but maybe could be?) defined in HoTT. On the other hand, $\equiv$ seems to be something within HoTT. In the index of symbols $:\equiv$ is `definition` and $\equiv$ is `judgmental equality`. Since a judgment is more or less defined as "a position one may find themselves in while following the rules in type theory (optionally within a context)", it makes sense that judgmental equality is "equal, in theory" (and definitional equality is "equal, by definition").

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=440
>.   The second kind of defined constant is used to specify a (parameterized) mapping $f(x_1,...,x_n,x)$, where $x$ ranges over a type whose elements are generated by zero or more primitive constants. For each such primitive constant $c$ there is a defining equation of the form$$f(x_1,\dots,x_n,c(y_1,\dots,y_m)):\equiv t,$$where $f$ may occur in $t$, but only in such a way that it is clear that the equations determine a totally defined function.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=49
>.   As an example, we look at how to define a function on natural numbers which doubles its argument. In this case we have $C :\equiv \mathbb{N}$. We first need to supply the value of $\text{double}(0)$, which is easy: we put $c_0 :\equiv 0$. Next, to compute the value of $\text{double}(\text{succ}(n))$ for a natural number $n$, we first compute the value of $\text{double}(n)$ and then perform the successor operation twice. This is captured by the recurrence $c_s(n,y) :\equiv \text{succ}(\text{succ}(y))$. Note that the second argument $y$ of $c_s$ stands for the result of the *recursive call* $\text{double}(n)$.
>.   Defining $\text{double} : \mathbb{N} \to \mathbb{N}$ by primitive recursion in this way, therefore, we obtain the defining equations:$$\begin{align}
\text{double}(0) &:\equiv 0 \\
\text{double}(\text{succ}(n)) &:\equiv \text{succ}(\text{succ}(\text{double}(n))).
\end{align}$$This indeed has the correct computation behavior: for example, we have$$\begin{align}
\text{double}(2) &\equiv \text{double}(\text{succ}(\text{succ}(0))) \\
&\equiv c_{s}(\text{succ}(0),\text{double}(\text{succ}(0))) \\
&\equiv \text{succ}(\text{succ}(\text{double}(\text{succ}(0)))) \\
&\equiv \text{succ}(\text{succ}(c_{s}(0,\text{double}(0)))) \\
&\equiv \text{succ}(\text{succ}(\text{succ}\text{(succ}(\text{double(0}))))) \\
&\equiv \text{succ}(\text{succ}(\text{succ}(\text{succ}(c_{0})))) \\
&\equiv \text{succ}(\text{succ}(\text{succ}(\text{succ}(0)))) \\
&\equiv 4
\end{align}$$

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=35
>.   We have seen how to define functions in one variable. One way to define functions in several variables would be to use the cartesian product, which will be introduced later; a function with parameters $A$ and $B$ and results in $C$ would be given the type $f : A \times B \to C$. However, there is another choice that avoids using product types, which is called **currying**.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=49
>So far we have rules for constructing new types by abstract operations, but for doing concrete mathematics we also require some concrete types, such as types of numbers. The most basic such is the type $\mathbb{N} : \mathcal{U}$ of natural numbers; once we have this we can construct integers, rational numbers, real numbers, and so on.
>.   The elements of $\mathbb{N}$ are constructed using $0 : \mathbb{N}$ and the successor operation $\text{succ} : \mathbb{N} \to \mathbb{N}$. When denoting natural numbers, we adopt the usual decimal notation $1 :\equiv \text{succ}(0), 2 :\equiv \text{succ}(1), 3 :\equiv \text{succ}(2),....$

YRZUC hey, did we not use that exact notation? [[nng4#^c72545|We did.]] Nice.

YRZUC the way the text writes the doubling examples and non-dependent function $f : \mathbb{N} \to C$ out of the natural numbers by recursion is a bit jarring, but we think we see a pattern that isn't explicitly given.

Let's write down the non-dependent function by natural number recursion defining equations, then the $\text{double} : \mathbb{N} \to \mathbb{N}$ defining equations, then the recurrence that captures $\text{double}$.$$
\begin{align}
  f(0) &:\equiv c_{0}&a_0 \\
  f(\text{succ}(n)) &:\equiv c_{s}(n,f(n))&a_1 \\
  \\
  \text{double}(0) &:\equiv 0&b_0 \\
  \text{double}(\text{succ}(n)) &:\equiv \text{succ}(\text{succ}(\text{double}(n))) &b_1 \\
  \\
  c_{s}(n,y) &:\equiv \text{succ}(\text{succ}(y))&c_0
\end{align}
$$What did we see? RHS of $a1$ is just $c0[\ f(n)\ /\ y\ ]$. If we perform that substitution on $c0$, we can chain $a1$ with RHS $c0$. As well, $f(n)$ is $double(n)$.$$
\begin{align} \\
  f &:\equiv \text{double} && &&&d_{0} \\
  f(n) &:\equiv \text{double}(n) &&:\equiv y &&&d_1 \\
  f(\text{succ}(n)) &:\equiv c_{s}(n,f(n)) &&:\equiv \text{succ}(\text{succ}(f(n)))&&&d_2 \\
  \text{double}(\text{succ}(n)) &:\equiv c_{s}(n,\text{double}(n)) &&:\equiv \text{succ}(\text{succ}(\text{double}(n)))&&&d_3
\end{align}
$$$d_2$ is interestingly backwards-looking from the formal definition. We'll map it. $c_s$ is a parameterized mapping $f(\mathbb{N},x)$, where $x$ ranges over $C$, whose elements are generated by zero or more primitive constants (presumably $\mathbb{N}$). For each such primitive constant $c$, there is a defining equation (refer to $d_2$ or $d_3$). So our parameterized mapping $f$ is $c_s$ and "for each" primitive constant $c$ is referring to those constants generated by $f(n)$ applied to $\mathbb{N}$. Bit backwards looking, if we understand it correctly, since $f$ is $c$ and $c$ is $f(n)$.

$c_s$ is the "next step", and in this case, if we substitute $d2[0,\text{double}/n,f]$, our parameterized mapping is $c_s(0,\text{double}(0))$, and we can see by the equal definitions that it's $2$. So the "next step" from $0$ is $2$, and since $x$ or $f(n$) or $double(n)$ or $y$ (all are the same) ranges over $C$, whose elements are generated by... then that means that the elements of $C$ must be $0, 2, 4,...$ (although formally in $\text{succ}$ form, presumably).

YRZUC yrzuc has possibly become a sort of stand-in exclamation or acknowledgment sound, like midwesterners saying "ope" (instinctive reaction noise). In our case, it original referred to an event or input to the human machine, but now that we are declaring it as those inputs arise, it has become a sort of "instinctive reaction noise" (but textual).

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=39
>For example, we can form the function type $A \to B$ when $A$ is a type and when $B$ is a type. We can form the dependent function type $\prod_{(x:A)}B(x)$ when $A$ is a type and $B(x)$ is a type for $x:A$.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=40
>.   As an example, we can derive the **projection** functions$$
\begin{align}
  \text{pr}_{1}:A\times B \to A \\
  \text{pr}_{2}:A\times B \to B
\end{align}
$$with the defining equations$$
\begin{align}
  \text{pr}_{1}((a,b)) &:\equiv a \\
  \text{pr}_{2}((a,b)) &:\equiv b.
\end{align}
$$

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=41
>.   We leave it as a simple exercise to show that the recursor can be derived from the projections and vice versa.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=37
>In type theory we often use a more general version of function types, called a $\prod$**-type** or **dependent function type**. The elements of a $\prod$-type are functions whose codomain type can vary depending on the element of the domain to which the function is applied, called **dependent functions**. The name "$\prod$-type" is used because this type can also be regarded as the cartesian product over a given type.
>.   Given a type $A : \mathcal{U}$ and a family $B : A \to \mathcal{U}$, we may construct the type of dependent functions $\prod_{(x:A)}B(x):\mathcal{U}$. There are many alternative notations for this type, such as$$
\begin{array}
  \textstyle\prod_{(x:A)}B(x)
  & \displaystyle\prod_{(x:A)}B(x)
  & \prod(x:A),\ B(x).
\end{array}
$$If $B$ is a constant family, then the dependent product type is the ordinary function type:$$
\textstyle\prod_{(x:A)}B \equiv (A \to B).
$$

https://hott.github.io/book/hott-online-15-ge428abf.pdf
>.   To model a collection of types varying over a given type $A$, we use functions $B : A \to \mathcal{U}$ whose codomain is a universe. These functions are called **families of types** (or sometimes *dependent types*); they correspond to families of sets as used in set theory.
>.   An example of a type family is the family of finite sets $\text{Fin} : \mathbb{N} \to \mathcal{U}$, where $\text{Fin}(n)$ is a type with exactly $n$ elements. (We cannot *define* the family $\text{Fin}$ yet $-$ indeed, we have not even introduced its domain $\mathbb{N}$ yet $-$ but we will be able to soon.) We may denote the elements of $\text{Fin}(n)$ by $0_n,1_n,...,(n-1)_n$, with subscripts to emphasize that the elements of $\text{Fin}(n)$ are different from those of $\text{Fin}(m)$ if $n$ is different from $m$, and all are different from the ordinary natural numbers.
>.   A more trivial (but very important) example of a type family is the **constant** type family at a type $B:\mathcal{U}$, which is of course the constant function $(\lambda(x:A).B):A\to \mathcal{U}$.

We think that "the recursor" is another way of saying "the second kind of defined constant", so some function like $f(x_1,...,x_n,c(y_1,...,y_m)) :\equiv t$, where $c$ ranges over a type whose elements are generated by zero or more primitive constants.$$
\begin{align}
  \text{pr}_{1}:\ &A\times B \to A \\
  \text{pr}_{2}:\ &A\times B \to B \\
  \textstyle\prod_{(x:A\times B)}C(x)\equiv\ (&A\times B\to C) \\
  \textstyle\prod_{((x,y):(A, B))}C(x, y)\equiv\ (&A\to B\to C) \\
  \textstyle\prod_{((x:A,y:B))}C(x, y)\equiv\ (&A\to B\to C) \\
  \textstyle\prod_{(x:A,y:B)}C(x, y)\equiv\ (&A\to B\to C) \\
\end{align}
$$The idea here is that we take the forming rules for a dependent function type and the projection functions, then we form a dependent function that generalizes. We think that the dependent function type is "the recursor" and thus is also "the second kind of defined constant". Specifically, perhaps the dependent function type is an example of "the second kind of defined constant".

Since the projection functions give us a a type $A\times B : \mathcal{U}$, we can use that as the first part of the forming of the dependent function. However, we then need a family $?:A\times B\to\mathcal{U}$, in order to be allowed to construct a type of dependent functions.
What if $?$ was $A$ such that we have a dependent function $\prod_{(x:A\times B)}A(x)$? The only way this could represent our projection functions is if $B$ was in $A$ and $A$ was also in $A$, which respectively we shouldn't assume and doesn't make sense (we think). For the same reason, $?$ shouldn't be $B$.
So we pick the next letter, $?$ is $C$. $C$ is fresh and new, and if we think about how we can use it to represent our projection functions, then $C$ just needs to contain at least $A$ and $B$, then it should be able to do that.
So $C(x)$ is a type for $x:A\times B$.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=38
>.   Another important class of dependent function types, which we can define now, are functions which are **polymorphic** over a given universe. A polymorphic function is one which takes a type as one if its arguments, and the acts on elements of that type (or of other types constructed from it). An example is the polymorphic identity function $\text{id}:\prod_{(A:\mathcal{U})}A\to A$, which we define by $\text{id}:\equiv\lambda(A:\mathcal{U}).\lambda(x:A).x$.
>.   We sometimes write some arguments of a dependent function as subscripts. For instance, we might equivalently define the polymorphic identity function by $\text{id}_A(x):\equiv x$. Moreover, if an argument can be inferred from context, we may omit it altogether. For instance, if $a:A$, then writing $\text{id}(a)$ is unambiguous, since $\text{id}$ must mean $\text{id}_A$ in order for it to be applicable to $a$.
>.   Another, less trivial, example of a polymorphic function is the "swap" operation that switches the order of the arguments of a (curried) two-argument function:$$
\text{swap}\prod_{(A:\mathcal{U})}\prod_{(B:\mathcal{U})}\prod_{(C:\mathcal{U})}(A\to B \to C)\to(B\to A\to C).
$$We can define this by$$
\text{swap}(A,B,C,g):\equiv\lambda b.\lambda a.g(a)(b).
$$.   Note that as we did for ordinary functions, we use currying to define dependent functions with several arguments (such as $\text{swap}$). However, in the dependent case the second domain may depend on the first one, and the codomain may depend on both. That is, given $A:\mathcal{U}$ and type families $B:A\to\mathcal{U}$ and $C:\prod_{(x:A)}B(x)\to\mathcal{U}$, we may construct the type $\prod_{(x:A)}\prod_{(y:B(x))}C(x,y)$ of functions with two arguments. In the case when $B$ is a constant and equal to $A$, we may condense the notation and write $\prod_(x,y:A)$; for instance, the type of swap could also be written as$$
\text{swap}:\prod_{(A,B,C:\mathcal{U})}(A\to B\to C)\to(B\to A\to C)
$$Finally, given $f:\prod_{(x:A)}\prod_{(y:B(x))}C(x,y)$ and arguments $a:A$ and $b:B(a)$, we have $f(a)(b):C(a,b)$, which, as before, we write as $f(a,b):C(a,b)$.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=33
>Given types $A$ and $B$, we can construct the type $A\to B$ of **functions** with domain $A$ and codomain $B$. We also sometimes refer to functions as **maps**.
>.   Given a function $f:A\to B$ and an element of the domain $a:A$, we can **apply** the function to obtain an element of the codomain $B$, denoted $f(a)$ and called the **value** of $f$ at $a$. It is common in type theory to omit the parentheses and denote $f(a)$ simply by $f a$, and we will sometimes do this as well.
>.   But how can we construct elements of $A\to B$? There are two equivalent ways: either by direct definition or by using $\lambda$-abstraction. Introducing a function by definition means that we introduce a function by givint it a name $-$ let's say, $f$ $-$ and saying we define $f:A\to B$ by giving an equation$$
f(x):\equiv\Phi\tag{1.2.1}
$$where $x$ is a variable and $\Phi$ is an expression which may use $x$. In order for this to be valid, we have to check that $\Phi:B$ assuming $x:A$.
>.   Now we can compute $f(a)$ by replacing the variable $x$ in $\Phi$ with $a$. As an example, consider the function $f:\mathbb{N}\to\mathbb{N}$ which is defined by $f(x):\equiv x+x$. Then $f(2)$ is judgmentally equal to $2+2$.
>.   If we don't want to introduce a n ame for the function, we can use $\lambda$-**abstraction**. Given an expression $\Phi$ of type $B$ which may use $x: A$, as above, we write $\lambda(x:A).\Phi$ to indicate the same function defined by $(1.2.1)$. Thus, we have$$
(\lambda(x:A).\Phi):A\to B.
$$For the example in the previous paragraph, we have the typing judgment$$
(\lambda(x:\mathbb{N}).x+x):\mathbb{N}\to\mathbb{N}.
$$As another example, for any types $A$ and $B$ and any element $y:B$, we have a **constant function** $(\lambda(x:A).y):A\to B$.
>.   We generally omit the type of the variable $x$ in a $\lambda$-abstraction and write $\lambda x.\Phi$, since the typing $x: A$ is inferable from the judgment that the function $\lambda x.\Phi$ has type $A\to B$. By convention, the "scope" of the variable binding "$\lambda x.$" is the entire rest of the expression, unless delimited with parentheses. Thus, for instance, $\lambda x.x+x$ should be parsed as $\lambda x.(x+x)$, not as $(\lambda x.x)$+x.
>.   Now a $\lambda$-abstraction is a function, so we can apply it to an argument $a:A$. We then have the following **computation rule** (often referred to as $\beta$**-conversion** or $\beta$**-reduction**), which is a definitional equality:$$
(\lambda x.\Phi)(a)\equiv\Phi'
$$where $\Phi'$ is the expression $\Phi$ in which all occurrences of $x$ have been replaced by $a$. Continuing the above example, we have$$
(\lambda x.x+x)(2)\equiv2+2.
$$Note that from any function $f:A\to B$, we can construct a lambda abstraction function $\lambda x.f(x)$. Since this is by definition "the function that applies $f$ to its arugment" we consider it to be definitionally equal to $f$:$$
f\equiv(\lambda x.f(x)).
$$This equality is the **uniqueness prinicple for function types**, because it shows that $f$ is uniquely determined by its values.
>.   The introduction of functions by definitions with explicit parameters can be reduced to simple definitions by using $\lambda$-abstraction: i.e., we can read a definition of $f:A\to B$ by$$
f(x):\equiv\Phi
$$as$$
f:\equiv\lambda x.\Phi.
$$

YRZUC-notion a family and a universe may be the same thing, perhaps some redundancy, or that there's something we must understand more.

>To model a collection of types varying over a given type $A$, we use functions $B : A \to \mathcal{U}$ whose codomain is a universe. These functions are called **families of types** (or sometimes *dependent types*);

Why not write that as $\prod_{(x:A)}\mathcal{U}(x)$? That would imply that we have a family $\mathcal{U}:A\to\mathcal{U}$. Something about that seems a bit "forbidden". What if we made that in the polymorphic style? $\prod_{(A:\mathcal{U})}A\to\mathcal{U}$. We could define this as $\text{foo}:\equiv\lambda(A:\mathcal{U}).\lambda(x:A).\Phi$.
This seems to be subtly different from $\prod_{(x:A)}B(x)$, since there we're implying that $A,B:\mathcal{U}$, but in what we're writing, we're implying $A:\mathcal{U_i}$, then $A,\mathcal{U}_i:\mathcal{U}_{i+1}$, *we think*.
The major difference seems to be that with $A$ and $B$, the implication is that $A$ and $B$ are separate, and if they are universes, neither contains the other. But, that's not possible, is it? According to the formal specification, we have a notion that creation of types just adds to a context, where perhaps each addition is a new universe.
We have a notion that the very concept of two completely unrelated types is possibly not reasonable, unless we make a specific type former that can do that.

We're going to refer to the formal presentation. We immediately found ourselves looking at the dependent function types, noticing that they express the $\prod$-notation as just shorthand for "the second kind of defined constant", but they also introduce it as a primitive constant.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=441
>We introduce a primitive constant $c_\prod$, but write $c_\prod(A,\lambda x.B)$ as $\prod_{(x:A)}B$.

That is the "second kind of defined constant" format, where $c_\prod$ is $f$, $A$ is $x_1$, and $\lambda x.B$ is $x$ or $c(y_1,...,y_m)$, which ranges over a type whose elements are generated by zero or more primitive constants. In this case, we'd be ranging over $B$, and our primitive constants are perhaps points $x_n$ in $A$, *generated* by applying $\lambda x.B$ at $x$.

Just under the above quote:

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=441
>Judgments concerning such expression and expression of the form $\lambda x.b$ are introduced by the following rules:
>- if $\Gamma\vdash A:\mathcal{U}_n$ and $\Gamma,x:A\vdash B:\mathcal{U}_n$, then $\Gamma\vdash\prod_{(x:A)}B:\mathcal{U_n}$
>- if $\Gamma,x:A\vdash b:B$ then $\Gamma\vdash(\lambda x.b):(\prod_{(x:A)}B)$
>- if $\Gamma\vdash g:\prod_{(x:A)}B$ and $\Gamma\vdash t:A$ then $\Gamma\vdash g(t):B[t/x]$

That first rule basically says "if $A$ is in some universe assuming some context, and $B$ is in the same universe assuming some context necessarily including $x$ as a point in $A$, then we can make a dependent function type in that universe whose elements consist of the value of $B$ at $x$."

YRZUC, the presentation immediately introduces things that don't appear to be types. Contexts are a list of assumptions in the form of pairs of elements and types. The variables must be distinct (note, it does not say the types must be distinct).

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=439
>The objects and types of our type theory may be written as terms using the following syntax, which is an extension of $\lambda$-calculus with *variables* $x$, $x'$, ..., *primitive constants* $c$, $c'$, ..., *defined constants* $f$, $f'$, ..., and term forming operations

"objects and types".
Not really "one basic notion: types" then is it? Or is that starting to blend theory and metatheory?

YRZUC if one misspells "metatheory", they may get "meatheory" or "metathoery", or even "meathoery". Meat hoe. I'm sorry, I just found that amusing.

It also seems confusing, the identifiers *primitive constants* versus *defined constants*. We tend to think of a constant as a constant, like $3$, $2 + 2$, "$foo$", $\text{\{ foo: "bar" \}}$, $\text{true}$, $[0, 1, 2]$, etc. To the book, it appears that a primitive constant is a single unchanging value, but a defined constant is a variable value. Both examples given for defined constants are functions. Oh, perhaps that makes sense. A primitive constant isn't defined, it just *is*. Like $0$. We don't need to define $0$, it just is $0$. But $f(x)$ or $\lambda x.\Phi$ isn't particularly useful without being defined. Actually, perhaps $\lambda x.\Phi$ is a primitive constant, since it isn't defined and the function implementation is obscured or abstracted. $f(x) :\equiv x$ is defined, and it's roughly an identity. $f(x) :\equiv x^2$ is defined, and it squares a value.

YRZUC despite having "objects and types" as well as "constants and variables", one of the first structural rules given has this snippet: $\vdash A_n:\mathcal{U}_i$, where $A_n$ is in the position of a "variable" but is clearly a type in universe $\mathcal{U_i}$.

Assuming nothing, we can conclude $\cdot\ \text{ctx}$. This is the $\text{ctx-}\scriptsize\text{EMP}$ rule of inference for a context.
We find the next rule of inference interesting, because it assumes that a type is in a universe. However, a this point, a hierarchy of universes is *postulated* in presentation 1. In the second presentation, after the context inference rules, there's type universe inference rules. The $\mathcal{U}\text{-}\scriptsize\textbf{INTRO}$ rule allows introduction of a universe, although in a bit of an odd way since it necessarily implies the conclusion of up to two universes from nothing. An English interpretation:
"Given a well-formed context (which can be empty), we can derive that a universe is a point in the next universe", which is expressed with $\Gamma\vdash\mathcal{U}_{i}:\mathcal{U}_{i+1}$.

Is $\vdash$ context concatenation?

We interpret $\text{ctx-}\scriptsize\textbf{EXT}$ to mean that if $\Gamma\vdash A:B$, then we can conclude or derive new variables in $A$ as long as they are distinct from any variables in $\Gamma$, and the result is a well formed context which appears to be $(\Gamma,x:A)\ \text{ctx}$. 
It seems that $A$, $B$, and $\mathcal{U}$ can all be used interchangeably. The context extension rule seems to also imply that variables are added one at a time.
So we could say $\mathcal{U}_i:\mathcal{U}_{i+1}$, or we could also just say $A:B$. The text also states that we can say $\mathcal{U}:\mathcal{U}$ and it's *implied* that the latter is a "higher" or "later" universe containing the former.

In fact, we wonder if we can write rules that more intuitively and accurately express that all things are types, starting with some "consolidation" of the syntax such that it doesn't appear that there are "universes with indicies" and also "types", but that there are just types, since that is what the text seems to want us to understand.

One thing we seem to be focusing on is that there don't seem to be any explicit rules for the creation of a type in the form $A$.
- The context rules allow us to create empty contexts out of nothing and add distinct variables to an existing type.
- The first structural rule allows us to derive assumptions from well-formed contexts. If a context is a structure holding assumptions like a stack, then that rule allows us to produce a typing judgment out of any of the assumptions in the stack, almost like allowing us to "peer into" the context or "extract from" the context.
- Every other structural rule has hypotheses that require the existence of a type. Note then, that is seems all structural rules can only be applied with a non-empty context.
- The first type universe rule is written peculiarly. It appears to state that given any well formed context (could be empty), that we can create two universes, with one inhabiting the other. This is peculiar since one universe is taking on the role of a what appears to be a variable and the other universe is taking on the role of what appears to be a type, such that $\mathcal{U}_i:\mathcal{U}_{i+1}$ and $a:A$ should mean the same thing. There is a note that says $a: A$ implies $A : \mathcal{U}_i$ for some $i$, which is even more peculiar, as it seems to indicate that we can't have a "variable" without there being three objects: the variable, the type of the variable, and the universe inhabited by the type. We find it interesting and peculiar that there seems to be no way to define a variable, type, universe, or any other name of an object where we define it by itself. It seems everything must be inhabited by something. That sort of makes sense, as being inhabited is like saying "it is proved", and without being inhabited, we "don't have proof" which isn't useful.
- Dependent function type rules all require an existing type.
- Dependent pair type rules all require an existing type.
- Coproduct types all require an existing type.
- The empty type rule does allow us to create a type from nothing, but only the $\textbf0$ type and the universe we have it inhabit.
- The same applies for the unit type $\textbf{1}$, except we can create a universe, type, and variable with the first two rules (although like the type, the variable must be $\textbf{*}$).
- The natural number rules allow us to create the natural numbers.
- Identity types all require a type.

So it seems we can only create universes and some explicitly defined and unique types, like the natural numbers, the unit type, and the empty type.
It would seem then that the concept of $A$ is strange. How do we get to $A$? The only way is if we consider $A$ to be shorthand for some universe.

It would seem then, that every time $A$, $B$, $C$, etc. is referenced in the HoTT book, I don't understand what those are (unless they are shorthand for universes, which the book seems to want to be some distinct notion, which also contrasts with the premise that `there is one basic notion: types`).

If I wanted then to "properly" do some exercise involving a derivation involving some type $A$, wouldn't I then necessarily have to either omit information (therefore the derivation isn't "proper") or create rules that allow the introduction of $A$?

Your context extension rule use is how I imagine I should approach it, but that has the odd effect of the "type" $A$ as variable being added to the "universe" U_i as a type.

It makes me wonder why they distinctualize variable and universe as things at all, especially in the formal presentation, when it seems it could be much more intuitive, simple, and concise to describe contexts as * being pairs of types, where the left of a pair inhabits the right of a pair * all lefts of pairs in a context must be distinct and instead of "universe introduction and accumulation rules" we just have "type introduction and accumulation rules".

Then, there's only types, which is in line with `there is one basic notion: types`, and it's now simple and intuitive to answer the question "where does $A$ come from?" as we can now use our "type introduction" rules.

An odd consequence of viewing things this way is that although we can answer "where does $A$ come from?", since all types must be inhabited (which as the notes say make sense, inhabitation is proof and without proof a type is meaningless), then $A$ doesn't really exist on its own, $A$:$B$ is the first "thing" we can produce, necessarily meaning we either have 0 types, 2 types, or more than 2 types. I find that interesting.

I don't think there'd be any new, removed, or modified implications, the above is just a result of taking every instance of U, U_i, and U_{(i+1)} in the formal presentation and changing it to A, A, and B respectively.

Likewise, take every instance of "variable" and "universe" and change it to "type" and "type" respectively. I think that shouldn't change anything, as long as we specify in the situations where there's now an ambiguity what rules need to be followed in order for things to remain the same.

For example, "variables in a context must be distinct" would become "types in a context must be distinct", but since a context was made of pairs of variables and types, it seems the meaning now changed. It's very similar to the notions of "variable capture" mentioned in the text. In order for us to then retain the original meaning, we can add or modify to specify "left types of a context must be distinct" in order to make those distinct from "right types", or we could say "inhabitants must be distinct" or something to that effect.

I wonder why the book doesn't seem to indicate that sort of understanding. Perhaps it does and I missed it. Do you know if this is a point of view that has been taken up before? I'd be surprised if it was novel.

What I imagine would make the most sense is if at the beginning of the book or the formal presentations there was some big, unavoidable disclaimer to the effect of "we're going to say variables and universes but we really mean types, just keep that in mind", but I haven't seen anything to that effect, which makes me wonder if there's some possibly more substantial difference between what the book puts forth compared to how we want to understand it.

I'm going to try and use my understanding as I read the book. I do wonder about the whole "there are 0, 2, or more than 2 types" thing. It makes me think about imaginary numbers. Perhaps there is some use, hidden, in there being an uninhabited type and allowing the existence of 1 type.

"Something that when squared equals -1" was always considered to be meaningless until suddenly it wasn't and became at least a large part of electrical engineering and mathematics.

Do you know if anyone has considered this for type theory or HoTT specifically?

Imaginary Type. $:A$.

Anyways, back to trying to derive the recursor from the projection functions.
So we assume we have:
- $A:C$
- $B:C$
- $A\times B:C$
- $\text{pr}_{1}:A\times B \to A$
- $\text{pr}_{2}:A\times B \to B$
- $\text{pr}_{1}((a,b)) :\equiv a$
- $\text{pr}_{2}((a,b)):\equiv b$
- $a:A$
- $b:B$
- $x:A\times B$
- $(a,b):A\times B$
- $x \equiv (a,b)$
and we want to derive a function, called the recursor, which should probably be like the "second kind of defined constant".
It'd be trivial to create, we think, but to derive is a different beast.
We thought for a moment that we wanted the dependent function introduction rules, but we recall that the dependent function symbol is syntactic sugar for a certain $\lambda$-abstraction. We want the introduction rules without the sugar.
We also think that the derivation tree notation they use is horrible on the eyes, so we'll probably just use the *if-then* style. We'll also omit the full context forms.
- If $a:A,b:B$ then $\lambda(a:A).b:\prod_{(a:A)}B$ ($\scriptsize\prod\text{-}\textbf{INTRO}$)
With that rule, we now have
- $\lambda(x:A\times B).\Phi:\prod_{(x:A\times B)}C$, which we can simplify to $\lambda x.\Phi:\prod_{A\times B}C$ and use the $\scriptsize\prod\text{-}\textbf{UNIQ}$ rule to derive then that $\Phi\equiv\lambda x.\Phi:\prod_{A\times B}C$
Interestingly, the dependent function rules don't include the notation of a type family or specifically something like $C(x)$, they only describe what we had written and that the computation involves replacing of variables. However, the book would have had us believe that what we wrote is a "constant function". It seems that in the formal presentation, the notion of "constant function" is generalized away completely.
If we desugar the syntax we get
- $\Phi\equiv\lambda x.\Phi:c_\prod(A\times B,\lambda x.C)$
We seem a bit stuck here, since we don't seem to be able to derive exactly what $\Phi$ is, rather we know its type only.
Oh that's odd, the product type isn't real. It's just a special case of dependent pair types where $B$ doesn't contain free occurrences of $a$ where $a:A$. So technically, we have
- $A\times B:\equiv\sum_AB$
We think then that we can derive the hypotheses for the $\scriptsize\sum\text{-}\text{ELIM}$ rule.
Do we have $z:\sum_AB$ and some $C$?
- $A\times B:\equiv\sum_AB$, so we can look for $z:A\times B$ and some C
- $(a,b):A\times B$, so $z\equiv(a,b)$
- we have a $C$ (specifically it does also "come after" or is inhabited by the previous things)
Do we have $x:A,y:B$ and some $g:C[(x,y)/z]$?
- $a:A$ (we'll refer to the x in the rule as just $a$ to not confuse it with the product from earlier
- $b:B$ (we'll do the same but for y just as consistency)
- we can get a $g$ if we apply $\scriptsize\prod\text{-}\text{ELIM}$
	- $f:\prod_{(x:A)}B$ and $a:A$
	- $\Phi:\prod_{A\times B}C$ and $x:(A\times B)$ gives us
	- $\Phi\equiv f$ and likewise we'll keep track of our terms to avoid capturing
	- applying now with the hypotheses we derived we get $\Phi(x):C[x/c]$, which is also $\Phi((a,b)):C[(a,b)/c]$, which satisfies the above like
- $g\equiv\Phi((a,b))$ or $g\equiv\Phi(x)$
Do we have $p:\sum_{(x:A)}B$?
- We can rewrite what we have so that's $p:A\times B$, which we have as
- $x:A\times B$ or $(a,b):A\times B$
So we can now apply $\scriptsize\sum\text{-}\text{ELIM}$ now that we have derived the correct hypotheses, giving us$$
\text{ind}_{\sum_AB}({c.}C,{a.}{b.}\Phi,x):C[x/c]
$$And since our dependent pair is assumed to be the special variant (since it was defined as a cartesian product) we'll change that back.$$
\text{ind}_{A\times B}({c.}C,{a.}{b.}\Phi,x):C[x/c]
$$We wonder if that's the recursor?
The answer was:$$
\begin{align}
  \text{rec}_{A\times B}:\prod_{C:\mathcal{U}}(A\to B\to C)\to A\times B\to C \\
  \text{rec}_{A\times B}(C,g,(a,b)):\equiv g(a)(b)
\end{align}
$$We'll cheat a bit on the deriving the projection functions from what we have, but first the text seems to implicitly rewrite those as $\lambda$-abstractions:
- $\text{pr}_1:\equiv\lambda a.\lambda b.a$
- $\text{pr}_2:\equiv\lambda a.\lambda b.b$
And then it appears they just used that as $g$ (or in our case $\Phi$):$$
\begin{align}
  \text{pr}_1&:\equiv\text{ind}_{\sum_AB}(c.C,{\lambda a.}{\lambda b.}a,(a,b)) \\
  \text{pr}_2&:\equiv\text{ind}_{\sum_AB}(c.C,{\lambda a.}{\lambda b.}b,(a,b))
\end{align}
$$We think our result is not onlly correct, but actually goes quite a bit further:
- Instead of a judgment of the name of the function belonging to a type, then a definition of the function, we ended up with a single judgment and no definition needed, since our 2nd argument for the induction function we produced defines itself by binding $a$ and $b$, which arose after applying $\scriptsize\sum\text{-}\text{ELIM}$, from which we derived the substitution hypothesis by applying $\scriptsize\prod\text{-}\text{ELIM}$, where we got the dependent function type hypothesis from applying $\scriptsize\prod\text{-}\textbf{INTRO}$.
- $c$ is something new that we bind in $C$ and we also explicitly state that the type of the inductor substitutes $x$ for $c$. If we look at the solution, we can see that $A\to B$ effectively gets replaced by $A\times B$, so we conjecture that $c$ is a sort of free variable (type?) inhabiting $C$ whose type is $A\to B$. Since our inductor substitutes $x$ for $c$ and $x$ is of type $A\times B$, then our conjecture that it substitutes some $A\to B$ would explain the behavior. However, the consequence of that seems to be that we have basically accidentally derived $c:C$ somewhere along the way, which, if correct and valid, is very neat. Looking back, we derived that $(a,b)$ was what ended up as $c$. We also see that $(a,b):\sum_{(x:A)}B$ is the conclusion of $\scriptsize\sum\text{-}\text{INTRO}$, where $b$ is of type $B[a/x]$ for some $x:A$. This seems to imply that $(a,b)$ is indeed something akin to a function $A\to B$, as we are substituting $a$ for some $x$ in $B$. But it's a bit more than that, since it's not a function, it's more simply "a type where we substitute free occurrences of an inhabitant", where take "free" to mean "not bound". Since we're assuming there are no free occurrences of $a$ in our $B$ (since we were given a cartesian product, a special case where there are no free occurences of $a$ in $B$), we can think of our $(a, b)$ AKA $c$ as a constant function $A\to B$, where the $A$ doesn't particularly matter (in our case). So our conjecture that $c$ is a function $A\to B$ appears to be consistent, specifically that it is a function $A\to B$ where the $A$ "doesn't matter" (since we were given a cartesian product, a case specifically with that property). There seems to be a sort of blending or blurring between function types, dependent function types, and dependent pair types here, we're curious to explore that more.
- We retain the dependent pair nature between A and B, which seems to be a generalization of the solution's $A\times B$. We take it then that our solution is more general and thus more useful, since we are not restricted to the special case of the relation between $A$ and $B$ where $B$ doesn't contain free occurences of some $x:A$. Likewise, the third argument of our inductor differs from the solution in that we don't specify $(a,b)$, but rather just $x$, which is something we will use to substitute $c$, where either we already derived or it can be derived (or easily inferred from the dependent pair type given) that $x$ and $c$ are of type $\sum_AB$.

https://hott.github.io/book/hott-online-15-ge428abf.pdf#page=40
>We leave it as a simple exercise to show that the recursor can be derived from the projections and vice versa.

Perhaps it was simple since it only took me, an uneducated, inexperienced person less than a day, but that definitely was not what I would call "simple".

Do we now understand enough to see if this can be implemented in TypeScript or, if not, why?
One recurring thought was that JavaScript functions are *not* mathematical functions and that's a bit unfortunate theory-wise (but great for a programmer). Well they are, but they're way more complicated. They're more like opcodes in a state machine.

https://stackoverflow.com/questions/78317301/typescript-noinfer-type-not-working-as-expected
https://github.com/microsoft/TypeScript/issues/47599

well, we know why now, and we have some minimal reproductions exemplifying. basically, typescript employs a convoluted and fragile context system, where anything besides immediately accessible context causes typescript to just break down and give up.

```ts
const f:
  <X extends string | number>(_x: X) => X =
    x => x

const g:
  (l: number) => string =
    l =>
    'A'.repeat(l)

const q:
  <X, R>(f: (x: X) => R) =>
  (x: X) =>
  R =
    f =>
    x =>
    f(x)

const h:
  <X, R>(f: (x: X) => R) =>
  <Y>(g: (y: Y) => X) =>
  (y: Y) =>
  R =
    f =>
    g =>
    y =>
    f(g(y))

const i:
  <X, R, Y>(f: (x: X) => R, g: (y: Y) => X) =>
  (y: Y) =>
  R =
    (f, g) =>
    y =>
    f(g(y))

const qf = q(f) // inference works. X is X and R is also X
const _qffoo = qf("foo") // const _qffoo: "foo"

const hf = h(f) // inference fails despite the initial signature being the exact same

const ifg = i(f, g) //  inference works
```