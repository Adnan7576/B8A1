# Assignment: Problem Solving with TypeScript & OOP

This repository contains solutions for the **B8A1: Problem Solving with TypeScript & OOP** assignment covering core TypeScript concepts, including basic types, optional and default parameters, readonly tuples, generic functions, interfaces, type narrowing, asynchronous Promises, and Object-Oriented Programming (OOP).

---

## File Structure

```text
├── solutions.ts
├── type-vs-interface.md
├── type-narrowing.md
└── README.md
```

---

## Overview of Solutions (`solutions.ts`)

All TypeScript solutions are implemented in `solutions.ts` with explicit parameter and return types, zero use of `any`, and strict type compliance:

1. **`multiplyValue`**: Handles multiplying a number by an optional multiplier. Properly falls back to multiplying by 2 when omitted (`undefined`) while safely handling `0`.
2. **`processInput`**: Uses `typeof` type narrowing across a union type (`string | number | boolean`) to format strings, multiply numbers by 10, or convert booleans to `"Active"` / `"Inactive"`.
3. **`formatCoordinate`**: Accepts a `readonly [number, number, string]` tuple and returns a formatted coordinate string without mutating the input.
4. **`concatenateArrays`**: A generic function using rest parameters (`...arrays: T[][]`) that combines multiple arrays into a single array preserving element order.
5. **`Course` & `getPopularCourses`**: Defines a `Course` interface and filters published courses meeting or exceeding a minimum student threshold without mutating the original array.
6. **`pluckValues`**: Generic function utilizing key constraints (`<T, K extends keyof T>`) to extract values of a specified property from an array of objects.
7. **`Employee` & `Manager`**: Demonstrates OOP inheritance and access modifiers (`protected`, `private`, `super`) with specialized formatted output methods.
8. **`validateAgeAsync`**: An asynchronous function returning `Promise<string>` that resolves after 1 second if age is 18 or older, or immediately rejects with an `Error` otherwise.

---

## Technical Blog Posts

The repository includes two technical blog posts analyzing core TypeScript paradigms:

1. [Differences Between Type Aliases and Interfaces in TypeScript](type-vs-interface.md)  
   Explores declaration merging, inheritance performance, union flexibility, and practical decision-making when designing type systems.

2. [Type Narrowing in TypeScript: A Practical Guide](type-narrowing.md)  
   Examines control-flow analysis and demonstrates type guards using `typeof`, `instanceof`, and the `in` operator.
