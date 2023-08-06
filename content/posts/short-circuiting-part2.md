---
title: "Short Circuiting Part2"
date: 2023-07-30T00:33:11-07:00
draft: false
featuredImage: /images/and.jpeg
featuredImagePreview: /images/and.jpeg
description: "JS Short Circuiting Concepts, And Operator"
keywords: ["Web Development", "Short Circuiting", "JavaScript", "And Operator"]
tags:
  - js
categories:
  - "web dev" 
---

## Part 2 (logical AND)

In JavaScript, we can utilize short-circuiting using `||` (logical OR) or the `&&` (logical AND) operators. This article focuses on the logical AND (`&&`) operator and provides examples.

## Logical AND `&&`

### Examples

Try to guess and test them yourself

```javascript
true && false          // OUTPUT: false (2nd value eval)
false && true          // OUTPUT: false (1st value eval)
true && true           // OUTPUT: true (2nd value eval)

// other variants of the above
"" && "michael"        // OUTPUT: "" (1st value eval)
!!("" && "michael")    // OUTPUT: false (!! eval to bool)
0 && 3.141             // OUTPUT: 0 (1st value eval)
3 && null              // OUTPUT: null (2nd value eval)
```

### Logic

The boolean AND `&&` returns true or false when included in a boolean expression. The evaluation proceeds from left to right, and as soon as a definitive answer is obtained, the result is returned. The boolean AND is true only if both operands are true. When the left operand evaluates to false, there is no need to continue the evaluation as the operation is short-circuited, and the return value will be false. Conversely, if the left operand is true, the right operand must be evaluated to determine the final result (true or false).

Importantly, short-circuiting not only returns the boolean value but also the value of the evaluated operand. For example, when using `&&`, if the left operand is a falsy value, the result will be the value of the left operand; otherwise, the result will be the value of the right operand. Understanding this behavior can be helpful in designing concise and efficient code.

### Falsy Values

```javascript
false
0
null
NaN
undefined
"" // empty string without space
```

Everything that is not `falsy` is `truthy`, for example:

```javascript
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

### Use Cases for the `&&` Operator

Classic use is in React:

```javascript
function Show({condition}){
    return(<>
        <h1>Result</h1>
        {condition && <Success />}
    </>)
}
```

* If `condition` is falsy, `<Success />` won't be rendered
    
* if `condition` is truthy, `<Success />` will be rendered.
    

## Operator Precedence

Since we have learned both the `||` and the `&&` operators, it is important to know that the `&&` operator takes precedence over the `||` operator:

```javascript
true || false && false          // returns true
```