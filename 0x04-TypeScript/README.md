# TypeScript

A typed superset of JavaScript that compiles to plain JavaScript.

## Overview

TypeScript is a strongly typed programming language that builds on JavaScript, giving you better tooling at any scale. It adds optional static typing to the language, allowing developers to describe the shape of objects, providing better documentation, and allowing TypeScript to validate that your code is working correctly.

## Key Features

- **Static Type-Checking**: Identify errors before runtime
- **Type Inference**: Automatic type detection when types aren't explicitly provided
- **IDE Integration**: Rich editor support with intelligent code completion
- **ECMAScript Compatibility**: Support for modern JavaScript features
- **Interfaces & Type Definitions**: Define complex object types
- **Generics**: Create reusable components with multiple types
- **Interoperability**: Works with existing JavaScript code
- **Compiler Options**: Configurable to suit your project's needs

## Installation

```bash
npm install -g typescript
```

## Quick Start

1. **Create a TypeScript file** (e.g., `hello.ts`):

```typescript
function greet(name: string): string {
  return `Hello, ${name}!`;
}

console.log(greet("TypeScript"));
```

2. **Compile it to JavaScript**:

```bash
tsc hello.ts
```

3. **Run the generated JavaScript**:

```bash
node hello.js
```

## TypeScript Configuration

Create a `tsconfig.json` file in your project root:

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "outDir": "./dist"
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

## Basic Types

```typescript
// Basic types
let isDone: boolean = false;
let decimal: number = 6;
let color: string = "blue";
let list: number[] = [1, 2, 3];
let x: [string, number] = ["hello", 10]; // Tuple

// Interfaces
interface Person {
  firstName: string;
  lastName: string;
  age?: number; // Optional property
}

// Functions with types
function add(x: number, y: number): number {
  return x + y;
}

// Generics
function identity<T>(arg: T): T {
  return arg;
}
```

## Advanced Features

### Type Assertions

```typescript
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```

### Union Types

```typescript
function formatCommandline(command: string | string[]): string {
  if (typeof command === "string") {
    return command.trim();
  } else {
    return command.join(" ");
  }
}
```

### Intersection Types

```typescript
interface Loggable {
  log(): void;
}

interface Identifiable {
  id: string;
}

type LoggableIdentifiable = Loggable & Identifiable;
```

### Utility Types

```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

// Partial makes all properties optional
type PartialTodo = Partial<Todo>;

// Pick selects specific properties
type TodoPreview = Pick<Todo, "title" | "completed">;

// Omit excludes specific properties
type TodoSummary = Omit<Todo, "description">;
```

## Integration with Frameworks

TypeScript works seamlessly with popular frameworks and libraries:

- **React**: Use with JSX via TSX files
- **Angular**: Built with TypeScript by default
- **Node.js**: Available via `@types` definitions
- **Vue.js**: Officially supported with class-based components
- **Express**: Type definitions available via DefinitelyTyped

## Community and Resources

- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [TypeScript GitHub Repository](https://github.com/microsoft/TypeScript)
- [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) - Type definitions for JavaScript libraries
- [TypeScript Playground](https://www.typescriptlang.org/play) - Try TypeScript in your browser

