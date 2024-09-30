## …
- **Name** Horizontal Ellipsis
- **Unicode** U+2026
- **Description** Denotes unstructured inputs. Implicitly immediately converts unstructured inputs into a structured form. 
- **Implications**
	1. Immediately coerces into a structured form (array/tuple).
	2. Can only exist once, at the end of a function's parameters.
	3. Is an identifier.
	4. Can consist of heterogenous types.
- **Examples**
	1. JavaScript rest parameter.
```js
const f = (...rest) => rest
```
	1. TypeScript definition:
```ts
['… → …']: <const Rest extends unknown[]>(...rest: Rest) => Rest
```

## →
- **Name** Rightwards Arrow
- **Unicode** U+2192
- **Description** Represents function application or mapping in type expressions. Separates the input types from the output type in function signatures.
- **Examples**
	1. TypeScript identity function:
```ts
['a → a']: <const A>(a: A) => A
```

## Ѓ
- **Name** # Cyrillic Capital Letter Gje
- **Unicode** U+403
- **Description** Specific to TypeScript (for now), an interface that contains mappings of Oumn expressions to their TypeScript type expression equivalents.
- **Notes**
	1. We have a notion that interfaces are "high, surface, top-heavy" as opposed to implementations "low, plumbing, bottom-heavy", so the symbols used for those correlate with that notion somewhat. ^18479a
- **Examples**
	1.  TypeScript interface container
```ts
interface Ѓ {
  ['… → …']:
    <const Rest extends unknown[]>(...rest: Rest) => Rest

  ['a b c → d']:
    <const A, const B, const C, D>(a: A, b: B, c: C) => D
    
  ['a → a']:
    <const A extends number>(a: A) => A
}
```

## Ђ
- **Name** Cyrillic Capital Letter Dje
- **Unicode** U+402
- **Description** Specific to TypeScript (for now), an interface that contains mappings of Oumn expressions to their TypeScript type expression equivalents.
- **Notes**
	1. See [[symbols#^18479a]].
- **Examples**
	1.  TypeScript implementation container
```ts
class Ђ {
  static id:
    Ѓ['a → a'] =
      a => a
}
```

## ℝ
- **Name** Double-Struck Capital R
- **Unicode** U+211D
- **Description** The set of real numbers.
- **Notes**
	1.  Can be used as a modifier or another type for the ᐊ operator. ^8c8ff0
- **Examples**
	1. TypeScript's `number` type.
```ts
['ℝa → ℝ']:
  (a: number) => number
```

## ℤ
- **Name** Double-Struck Capital Z
- **Unicode** U+2124
- **Description** The set of integers.
- **Notes**
	1.  Can be used as a modifier or another type for the ᐊ operator.
- **Examples**
	- TypeScript's `bigint` type.
```ts
['ℤa → ℤ']:
  (a: bigint) => bigint
```

## ᐊ
- **Name** Canadian Syllabics A
- **Unicode** U+140A
- **Description** TypeScript `extends` operator, also known as [`assignable to`](specifications#^5fbff3)
- **Notes**
	1.  [Almost means subtype](https://javascript.xgqfrms.xyz/pdfs/TypeScript%20Language%20Specification.pdf#page=66), but not quite.
	2. See [[#^8c8ff0]].
- **Examples**
```ts
['ℝᐊa → a']:
  <const A extends number>(a: A) => A

['ℝa → a']:
  <const A extends number>(a: A) => A
```

## Ω
- **Name** Greek Capital Letter Omega
- **Unicode** U+3A9
- **Description** The universal set.
- **Examples**
	1.  TypeScript's `unknown` type.

## ⊏
- **Name** Square Image Of
- **Unicode** U+228F
- **Description** Array modifier

## □

`⊏□`