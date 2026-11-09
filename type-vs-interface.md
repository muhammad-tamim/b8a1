- [What are the core differences between type aliases and interface in TypeScript? When should you choose one over the other?](#what-are-the-core-differences-between-type-aliases-and-interface-in-typescript-when-should-you-choose-one-over-the-other)
  - [Introduction:](#introduction)
  - [Explanation:](#explanation)
  - [Conclusion:](#conclusion)

# What are the core differences between type aliases and interface in TypeScript? When should you choose one over the other?

## Introduction:
Ts provides us two ways to define custom types: `type` aliases and `interface`. They Both help us to describe the structure of data and make our code more error free. Although they look similar and can often be used for the same purpose but they have some important differences.

## Explanation:
- Type Alias: Allows us to define a custom type that can be reused throughout our code. We need to use type keyword to create an type alias.

```ts
// Without type alias
const user1: {
    id: number;
    name: string;
    isAdmin?: boolean; 
} = {
    id: 1,
    name: "Tamim",
    isAdmin: true
}

// with type alias
type User = {
    id: number;
    name: string;
    isAdmin?: boolean; 
};

const user2: User = {
    id: 2,
    name: "Nasrin"
};

const user3: User = {
    id: 3,
    name: "Kuddus"
};
```
- Interface: Defines the shape of an object:
  
```ts
// without interface
const user1: {
    name: string;
    age: number;
    isAdmin?: boolean
} = {
    name: "nasrin",
    age: 11,
    isAdmin: false
}

// with interface
interface User {
    name: string;
    age: number;
    isAdmin?: boolean; 
}
const user2: User = {
    name: "tamim",
    age: 20
}
```

## Conclusion:
- Use interface = for object structure and class only
- Use type alias = for everything else or developer often used type alias also objects