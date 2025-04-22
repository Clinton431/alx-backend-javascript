# ES6 Data Manipulation

A modern guide to JavaScript data manipulation using ES6+ features.

## Overview

This library provides a comprehensive set of utilities for manipulating JavaScript data structures using ES6+ features. It leverages arrow functions, destructuring, spread operators, and other modern JavaScript features to make data transformation more concise and readable.

## Installation

```
npm install es6-data-manipulation
```

## Key Features

- **Array Operations**: Efficient methods for filtering, mapping, and reducing arrays
- **Object Manipulation**: Tools for merging, cloning, and transforming objects
- **Functional Programming**: Pure functions for predictable data transformations
- **Performance Optimized**: Designed for handling large datasets efficiently

## Usage Examples

### Array Operations

```javascript
// Filter array elements
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);

// Transform data with map
const doubled = numbers.map(num => num * 2);

// Combine operations with chaining
const sumOfDoubledEvenNumbers = numbers
  .filter(num => num % 2 === 0)
  .map(num => num * 2)
  .reduce((sum, num) => sum + num, 0);
```

### Object Operations

```javascript
// Merge objects with spread operator
const defaultOptions = { timeout: 1000, retry: true };
const userOptions = { timeout: 2000 };
const options = { ...defaultOptions, ...userOptions };

// Clone objects
const original = { name: 'Original', nested: { value: 42 } };
const clone = JSON.parse(JSON.stringify(original));

// Extract properties with destructuring
const { name, nested: { value } } = original;
```

## Advanced Examples

### Working with Collections

```javascript
const users = [
  { id: 1, name: 'Alice', role: 'admin' },
  { id: 2, name: 'Bob', role: 'user' },
  { id: 3, name: 'Charlie', role: 'user' }
];

// Find specific elements
const admin = users.find(user => user.role === 'admin');

// Group by property
const groupByRole = users.reduce((groups, user) => {
  groups[user.role] = groups[user.role] || [];
  groups[user.role].push(user);
  return groups;
}, {});

// Convert to Map for faster lookups
const userMap = new Map(users.map(user => [user.id, user]));
```

## Browser Support

- Chrome 51+
- Firefox 54+
- Safari 10+
- Edge 15+

## License

MIT
