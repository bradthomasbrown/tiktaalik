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

