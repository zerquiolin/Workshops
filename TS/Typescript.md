# Typescript

## Table of Contents

- [Typescript](#typescript)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Setting Up Ts](#setting-up-ts)
  - [Basyc Syntax](#basyc-syntax)
  - [Type Inference](#type-inference)
  - [Interfaces and Type Aliases](#interfaces-and-type-aliases)
  - [Type assersions](#type-assersions)
  - [Conditional Types](#conditional-types)
  - [Mapped Types](#mapped-types)
  - [Template Literal Types](#template-literal-types)
  - [Functions](#functions)
  - [Classes and Inheritance](#classes-and-inheritance)
  - [Modules](#modules)
  - [Generics](#generics)
  - [Decorators](#decorators)
  - [Js to Ts](#js-to-ts)
  - [Webpack](#webpack)

## Introduction

TypeScript serves as a powerful enhancement to JavaScript by introducing static typing, allowing developers to catch potential errors during development. As a superset of JavaScript, TypeScript provides features like interfaces, type aliases, and decorators to facilitate cleaner and more maintainable code. It compiles down to JavaScript, making it compatible with any JavaScript environment, and its adoption has grown significantly due to its ability to enhance code quality and developer productivity.

## Setting Up Ts

Setting up TypeScript involves installing it globally using npm and configuring a tsconfig.json file to customize the compilation process. The configuration file allows you to specify compilation options such as the target ECMAScript version, module system, and strict mode settings. This setup provides a foundation for leveraging TypeScript features in your project.

```bash
> npm install -g typescript
> tsc --init
> npm init -y
```

## Basyc Syntax

The basic syntax of TypeScript closely resembles JavaScript, with the addition of type annotations. Variables can be explicitly typed, functions can have parameter and return type annotations, and conditional statements can benefit from static typing. This section introduces the fundamental syntax elements that developers need to understand when working with TypeScript.

```typescript
// Variable declaration
let message: string = "Hello, TypeScript!";

// Function declaration
function greet(name: string): string {
  return `Hello, ${name}!`;
}

// Conditional statement
let isTypeScriptAwesome: boolean = true;
if (isTypeScriptAwesome) {
  console.log("Yes, it is!");
}
```

In the basic syntax example, we cover the fundamental elements of TypeScript. We declare a variable (message) with an explicit type annotation, create a function (greet) with a parameter and a return type, and use a conditional statement with a boolean variable (isTypeScriptAwesome). This illustrates the core building blocks of TypeScript's syntax.

## Type Inference

TypeScript offers type inference, allowing developers to omit explicit type annotations in many cases. The compiler analyzes the code and automatically deduces the variable types. This feature reduces verbosity while maintaining the benefits of static typing, promoting a balance between clarity and conciseness in code.

```typescript
let x = 10; // TypeScript infers x as number
let y = "Hello"; // TypeScript infers y as string
```

TypeScript's type inference allows variables to be declared without explicit type annotations while still benefiting from static typing. In this example, TypeScript infers the types of variables x and y based on their assigned values.

## Interfaces and Type Aliases

Interfaces and type aliases enable developers to define custom types in TypeScript. Interfaces describe the shape of objects, while type aliases provide a way to create reusable type definitions. This section explores how to use interfaces and type aliases to enhance code readability and maintainability.

```typescript
// Interface
interface Person {
  name: string;
  age: number;
}

// Type Alias
type Point = {
  x: number;
  y: number;
};
```

Here, we introduce interfaces and type aliases. Interfaces define a blueprint for objects, ensuring they have specific properties, while type aliases create custom type names for complex types. Person is an interface representing a person, and Point is a type alias for a 2D point.

## Type assersions

Type assertions in TypeScript provide a way to tell the compiler that a value should be treated as a specific type. This can be useful when working with variables of type 'any' or when dealing with complex data structures. Developers can employ type assertions to override the default type inference and work with the desired types.

```typescript
let value: any = "Hello, TypeScript!";
let length: number = (value as string).length;
```

Type assertions tell the TypeScript compiler that we are aware of the type of a particular variable. In this case, we assert that value is a string and then access its length property. Type assertions are helpful when working with variables of type any.

## Conditional Types

Conditional types in TypeScript allow for the creation of type transformations based on certain conditions. This section demonstrates how to use conditional types to create flexible and reusable type definitions that adapt to different scenarios within your code.

```typescript
type IsString<T> = T extends string ? true : false;

let isString: IsString<"Hello"> = true;
let isNotString: IsString<42> = false;
```

Conditional types create dynamic type checks. In this example, we define a conditional type IsString, which evaluates to true if T extends string, and false otherwise. We then demonstrate its usage with specific types.

## Mapped Types

Mapped types provide a concise way to create new types by transforming the properties of an existing type. This section delves into how mapped types can be utilized to generate modified versions of types, promoting code consistency and reducing redundancy.

```typescript
type OptionalProps<T> = { [K in keyof T]?: T[K] };

interface Car {
  make: string;
  model: string;
}

type OptionalCar = OptionalProps<Car>;
```

Mapped types transform the properties of an existing type. The OptionalProps type creates a new type with all properties of T optional. Here, it's applied to the Car interface to create OptionalCar.

## Template Literal Types

Template literal types introduce string interpolation capabilities to TypeScript's type system. This section illustrates how template literal types enable the creation of dynamic and precise type definitions, particularly useful in scenarios where the shape of a type depends on literal string values.

```typescript
type Greeting<T> = `Hello, ${T}!`;

let message: Greeting<"TypeScript"> = "Hello, TypeScript!";
```

Template literal types allow the creation of precise string literal types. In this example, the Greeting type is a template literal that forms a greeting message. We then use it to define a variable message with the specific type for "TypeScript".

## Functions

Functions in TypeScript can be enriched with explicit parameter and return type annotations. This section covers the basics of function declarations, optional and default parameters, as well as the importance of type annotations in function signatures to enhance code clarity and maintainability.

```typescript
// Function with explicit return type
function add(a: number, b: number): number {
  return a + b;
}

// Optional and default parameters
function greet(name: string, greeting: string = "Hello"): string {
  return `${greeting}, ${name}!`;
}
```

The functions example covers the basics of function declarations in TypeScript. It includes a function add with explicit parameter types and a return type, as well as a function greet with optional and default parameters.

## Classes and Inheritance

TypeScript supports classical object-oriented programming features, including classes and inheritance. This section explores how to define classes, constructors, and methods, emphasizing the extension of classes through inheritance. Understanding these concepts is crucial for building robust and scalable TypeScript applications.

```typescript
class Animal {
  constructor(public name: string) {}

  makeSound() {
    console.log("Some generic sound");
  }
}

class Dog extends Animal {
  makeSound() {
    console.log("Bark, bark!");
  }
}
```

This example introduces classes and inheritance. The Animal class has a constructor and a method makeSound, and the Dog class extends Animal with its own implementation of makeSound. It demonstrates the basic principles of object-oriented programming in TypeScript.

## Modules

Modules in TypeScript provide a way to organize code into separate files and promote code reusability. This section demonstrates how to create modules, export and import functionalities across files, facilitating the development of modular and maintainable TypeScript applications.

```typescript
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

// main.ts
import { add } from "./math";
let result = add(3, 4);
```

Modules help organize code into separate files. In this example, we create a module math exporting a function add, and then import and use it in another file main.ts. This showcases how to structure code across multiple files in a TypeScript project.

## Generics

Generics in TypeScript provide a powerful way to create reusable and flexible components by allowing types to be parameterized. This enables writing functions and classes that work with a variety of data types, providing type safety while maintaining code flexibility. With generics, you can write functions or classes that operate on a range of data types without sacrificing type information at compile-time. Here's a basic example of a generic function:

```typescript
// Generic function that echoes the input value
function echo<T>(value: T): T {
  return value;
}

let result: string = echo("Hello, Generics!");
let numberResult: number = echo(42);
```

In this example, the echo function uses a generic type T to represent the type of the input value. This allows the function to be invoked with different types while preserving the type information in the returned value. Generics are not limited to functions; they can also be applied to classes and interfaces, making them a versatile tool for building flexible and type-safe code.

## Decorators

Decorators are a powerful feature in TypeScript, allowing developers to annotate and modify classes and class members at design time. This section explains how to use decorators to add metadata, log information, and alter the behavior of classes and methods, contributing to a more modular and expressive codebase.

```typescript
function log(target: any, key: string) {
  console.log(`${key} was called`);
}

class Example {
  @log
  greet() {
    console.log("Hello!");
  }
}
```

Decorators allow modifying and adding metadata to classes and their members. In this example, the log decorator logs information when a method is called. We then apply this decorator to the greet method of the Example class.

Renaming a .js file to .ts initiates the migration from JavaScript to TypeScript. Developers can gradually add type annotations to existing code, leveraging TypeScript features incrementally while maintaining compatibility with existing JavaScript.

## Js to Ts

Transitioning from JavaScript to TypeScript can be a gradual process. Renaming a JavaScript file to a TypeScript file initiates the migration, and developers can then incrementally add type annotations to existing code. This section provides guidance on the steps to convert a JavaScript project to TypeScript and leverage the benefits of static typing.

## Webpack

Integrating TypeScript with Webpack enhances the development workflow by allowing the use of TypeScript features alongside powerful bundling capabilities. This section guides developers on setting up Webpack with TypeScript using the ts-loader to transpile TypeScript code into JavaScript, facilitating the creation of efficient and well-organized applications.
