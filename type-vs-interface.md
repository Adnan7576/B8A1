# Differences Between Type Aliases and Interfaces in TypeScript

TypeScript offers two primary mechanisms to define custom data structures: type aliases (`type`) and interfaces (`interface`). While they often seem interchangeable when defining object shapes, they possess distinct architectural capabilities and compiler behaviors. Understanding these differences allows developers to make deliberate architectural decisions in their codebases.

The most notable difference is declaration merging. Multiple interface declarations with the same identifier in the same scope merge automatically into a single definition. This makes interfaces ideal for augmenting external library types or global environments. In contrast, a type alias cannot be reopened or declared more than once. Attempting to redeclare a type alias will immediately trigger a duplicate identifier compiler error. Furthermore, interfaces support structural inheritance via the `extends` keyword. The TypeScript compiler heavily optimizes interface inheritance chains through internal type caching.

```ts
interface User {
  id: string;
}
interface User {
  name: string;
} // Merged into { id: string; name: string; }
```

On the other hand, type aliases provide unmatched flexibility with complex type expressions. A type alias can directly represent primitive aliases, union types, intersection types, and tuples. In addition, mapped types and conditional types can only be declared using type aliases. Interfaces cannot model standalone union types or primitive values directly.

```ts
type Status = "pending" | "resolved" | "rejected";
type Coordinate = readonly [number, number];
```

When choosing between them, prefer `interface` for object-oriented designs, public library APIs, and extensible contracts that classes implement. Use `type` when you need union types, computed types, tuples, or specialized functional transformations.

In conclusion, interfaces excel at defining expandable object contracts across large systems. Conversely, type aliases provide the expressiveness required for compositional and functional type systems.
