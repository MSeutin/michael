---
title: "Short Circuiting Part1"
date: 2023-07-30T00:29:37-07:00
draft: false
featuredImage: /images/short.jpeg
featuredImagePreview: /images/short.jpeg
description: "JS Short Circuiting Concepts, Or Operator"
keywords: ["Web Development", "Short Circuiting", "JavaScript", "Or Operator"]
tags:
  - js
categories:
  - mindset
comment:
seo:
menu:
repost:
---

# JS Short Circuiting to Shorten your Code - Part 1 (Logical OR)
In JavaScript, we can utilize short-circuiting using `||` (logical OR) or the `&&` (logical AND) operators. 
This article focuses on the logical OR (`||`) operator and provides an example of how to use it to simplify code.

## Logical OR `||`

### Examples
Try to guess and test them yourself
```js
true || false    // OUTPUT: true (1st value evaluated)
false || true    // OUTPUT: true (2nd value evaluated)
false || false   // OUTPUT: false (2nd value evaluated)

// other variants of the above
3.14 || 0        // OUTPUT: 3.14 (1st value evaluated)
0 || 3.14        // OUTPUT: 3.14 (2nd value evaluated)
0 || 0           // OUTPUT: 0 (2nd value evaluated)

// more variants
"zero" || 0         // OUTPUT: "zero" (1st value (it's truthy))
"" || 0.5           // OUTPUT: 0.5 (2nd value)
NaN || undefined    // OUTPUT: undefined (2nd value)

// one more
3 > 1 || "hello"    // OUTPUT: true (1st value evaluates to true)
```

### Logic
The boolean OR `||` returns true or false when included in a boolean expression. The evaluation proceeds from left to right, and as soon as a definitive answer is obtained, the result is returned. The boolean OR is true if either the left operand or the right operand is true, or both are true. It will only return false when both operands are false. When the left operand evaluates to true, there is no need to continue the evaluation as the operation is short-circuited, and the return value will be true. Conversely, if the left operand is false, the right operand must be evaluated to determine the final result (true or false).

Importantly, short-circuiting not only returns the boolean value but also the value of the evaluated operand. For example, when using `||`, if the left operand is a truthy value, the result will be the value of the left operand; otherwise, the result will be the value of the right operand. Understanding this behavior can be helpful in designing concise and efficient code.

### Falsy values
```js
false
0
null
NaN
undefined
"" // empty string without space
```
Everything that is not `falsy` is `truthy`, for example:
```js
// truthy 
" " 
[]
{}
3.14
"hello"
true

// using !! we can check their boolean value
console.log(!!" ")      // true
console.log(!![])       // true
console.log(!!{})       // true
console.log(!!3.14)     // true
console.log(!!"hello")  // true
console.log(!!true)     // true
```

### Example with objects
Let's consider two objects, `person1` and `person2`:
```js
// person1 has an age property
let person1 = {
  name: 'Michael',
  lastName: 'Smith',
  age: 30
}

// person2 does not have an age property
let person2 = {
  name: 'Bob',
  lastName: 'Wilson'
}
```
### Use Case:
We might receive either `person1` or `person2` as arguments to a function and not know if the `age` property is defined for each object.
If we need to perform calculations or operations involving `age`, we require a valid number.  However, `person2.age` would return `undefined` in this case, so we need a way to assign a default value to any object that lacks the `age` property:
```js
// short-circuiting with || to provide default values for age
let age1 = person1.age || 0
let age2 = person2.age || 0

console.log(`age1: ${age1}, age2: ${age2})
// OUTPUT: age1: 30, age2: 0

console.log(`person2.age is not defined: ${person2.age}`)
// OUTPUT: person2.age is not defined: undefined
```
### Explanation:
By using the logical OR (`||`) operator, we can effectively handle default values for the `age` property in each person object.
If `person1.age` is defined as truthy (not falsy), the variable `age1` will be assigned its value.
If `person1.age` is undefined or falsy (e.g., null, 0, an empty string), the `||` operator short-circuits and assigns the default value 0 to 'age1'.
Similarly, if `person2.age` is not defined (`undefined`) or falsy, the `||` operator short-circuits and assigns the default value 0 to `age2`.

### Alternatives:
Instead of using the logical OR (`||`) operator, you could achieve the same result using the ternary operator (conditional operator):
```js
// the ternary operator allows you to explicitly check if the `age` property is defined for each person object,
// and if it is, use its value; otherwise, use the default value 0.
let age1 = person1.age !== undefined ? person1.age : 0
let age2 = person2.age !== undefined ? person2.age : 0
```
