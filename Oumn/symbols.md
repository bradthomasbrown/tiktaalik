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
	2. TypeScript definition:
```ts
['… → …']: <const A extends unknown[]>(...a: A) => A
```
