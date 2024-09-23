our implementation in typescript

differences compared to the Ethereum Yellow Paper
1. tuples
	1. `Tuples are typically denoted with an upper-case letter, e.g. T, is used to denote an Ethereum transaction. This symbol may, if accordingly defined, be subscripted to refer to an individual component, e.g. Tn, denotes the nonce of said transaction. The form of the subscript is used to denote its type; e.g. uppercase subscripts refer to tuples with subscriptable components.`
	2. we'll actually provide the full definition for tuples when we define a tuple, not partial definitions scattered throughout. the definition will be in Typescript, and should be intuitive.
2. gas estimation
	1. not mentioned explicitly at all, and gas calculations are scattered throughout
	2. we'll put this in more or less one place, near the beginning. it's required to interact with or create smart contracts, and that's what makes the EVM unique. it should be treated with more respect.
3. fluff
	1. "We use a number of typographical conventions for the formal notation, some of which are quite particular to the present work:"
	2. as we iteratively make whatever documentation final, let's not do that kind of shit. that sentence genuinely has no reason to exist. 3 + 1 should result in a "conventions" section not existing at all. "show, don't tell".
4. implementation identification
	1. not discussed. implementations are vaguely referred to as abstract, like "it is assumed that the implementation will do this", "implementations must be able to", "in most practical implementations", etc.
	2. 