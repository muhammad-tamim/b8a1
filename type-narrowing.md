- [What is Type Narrowing in TypeScript? Provide practical examples using typeof, instanceof, and the in operator.](#what-is-type-narrowing-in-typescript-provide-practical-examples-using-typeof-instanceof-and-the-in-operator)
  - [Introduction:](#introduction)
  - [Explanation:](#explanation)
  - [Conclusion:](#conclusion)


# What is Type Narrowing in TypeScript? Provide practical examples using typeof, instanceof, and the in operator.

## Introduction:

When a variable can have multiple possible types (union type), TypeScript needs extra information to know what operations are safe. So that time we use type Narrowing to narrow the type of the variable at runtime so TypeScript can safely understand what the variable actually is. 

```ts
function print(value: string | number) {
    console.log(value.length);
    console.log(value.toFixed(2))
}

// errors
/*
Property 'length' does not exist on type 'string | number'.
  Property 'length' does not exist on type 'number'.

Property 'toFixed' does not exist on type 'string | number'.
  Property 'toFixed' does not exist on type 'string'.
*/
```

here, TypeScript shows errors while using .length or .toFixed because it cannot determine whether value is a string or a number. because .length is only valid for string and .toFixed is only valid for number. We can fix this by using type narrowing. 

## Explanation:
Type Narrowing can be done in many ways in ts, below are some of the most common ways to narrow the type of a variable:

- Typeof: Checks the type of a value at runtime.

```ts
function print(value: string | number) {
    if (typeof value === "string") {
        console.log(value.length);
    }
    else if (typeof value === "number") {
        console.log(value.toFixed(2));
    }
}

print("Hello") // 5
print(3.14159) // 3.14
print(true) // Argument of type 'boolean' is not assignable to parameter of type 'string | number'.
```

- in Operator: Checks if a property exists in the object:

```ts
type Admin = {
    username: string;
    isAdmin: true
};
type User = {
    username: string
};

function checkRole(person: Admin | User) {
    if ("isAdmin" in person) {
        console.log("Admin user");
    } else {
        console.log("Normal user");
    }
}

checkRole({ username: "Tamim", isAdmin: true }) // Admin user
checkRole({ username: "Tamim" }) // Normal user
```

- Instanceof: The instanceof operator is used to check whether an object is an instance of a specific class or not.

```ts
class Dog {
    bark() {
        console.log("Woof!");
    }
}

class Cat {
    meow() {
        console.log("Meow!");
    }
}

function speak(animal: Dog | Cat) {
    if (animal instanceof Dog) {
        animal.bark();
    } else {
        animal.meow();
    }
}

speak(new Dog()); // Woof!
speak(new Cat()); // Meow!
```

## Conclusion:
Type Narrow is a technique and we used lots of operators to for that and they called type guards. So above examples we used typeof, instanceof, and in operator. They all are type guards and we used type guards for type narrowing.