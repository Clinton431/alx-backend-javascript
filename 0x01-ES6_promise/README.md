# ES6 Promises in JavaScript

## Overview

Promises are a core feature in modern JavaScript, introduced in ES6 (ECMAScript 2015) to handle asynchronous operations more elegantly. They represent a value that may not be available yet but will be resolved at some point in the future, allowing for cleaner and more maintainable asynchronous code compared to callbacks.

## Contents

- [Basic Concepts](#basic-concepts)
- [Creating Promises](#creating-promises)
- [Using Promises](#using-promises)
- [Chaining Promises](#chaining-promises)
- [Error Handling](#error-handling)
- [Promise Methods](#promise-methods)
- [Async/Await](#asyncawait)
- [Best Practices](#best-practices)
- [Examples](#examples)

## Basic Concepts

A Promise is an object representing the eventual completion or failure of an asynchronous operation. A Promise exists in one of three states:
- **Pending**: Initial state, neither fulfilled nor rejected
- **Fulfilled**: Operation completed successfully
- **Rejected**: Operation failed

## Creating Promises

```javascript
const myPromise = new Promise((resolve, reject) => {
  // Asynchronous operation
  if (/* operation successful */) {
    resolve(value); // Promise is fulfilled with value
  } else {
    reject(error); // Promise is rejected with error
  }
});
```

## Using Promises

```javascript
myPromise
  .then(result => {
    // Handle successful result
  })
  .catch(error => {
    // Handle error
  })
  .finally(() => {
    // Executes regardless of success or failure
  });
```

## Chaining Promises

Promises can be chained to handle sequences of asynchronous operations:

```javascript
fetchData()
  .then(data => processData(data))
  .then(processedData => displayData(processedData))
  .catch(error => handleError(error));
```

## Error Handling

Errors in Promises can be handled using `.catch()` or as a second argument to `.then()`:

```javascript
myPromise
  .then(
    result => handleSuccess(result),
    error => handleError(error)
  );
```

## Promise Methods

- **Promise.resolve(value)**: Returns a resolved Promise with the given value
- **Promise.reject(reason)**: Returns a rejected Promise with the given reason
- **Promise.all(iterable)**: Returns a Promise that resolves when all Promises in the iterable have resolved
- **Promise.race(iterable)**: Returns a Promise that resolves or rejects as soon as one of the Promises in the iterable resolves or rejects
- **Promise.allSettled(iterable)**: Returns a Promise that resolves when all Promises in the iterable have settled
- **Promise.any(iterable)**: Returns a Promise that resolves as soon as one of the Promises in the iterable fulfills

## Async/Await

ES2017 introduced async/await syntax for working with Promises:

```javascript
async function fetchAndProcessData() {
  try {
    const data = await fetchData();
    const processedData = await processData(data);
    return displayData(processedData);
  } catch (error) {
    handleError(error);
  }
}
```

## Best Practices

1. Always handle Promise rejections
2. Use `.catch()` at the end of Promise chains
3. Avoid nesting Promises; use chaining instead
4. Return Promises from functions for better composability
5. Use `async/await` for cleaner asynchronous code
6. Remember that `.then()` and `.catch()` always return new Promises

## Examples

### Basic Promise Example

```javascript
function fetchUserData(userId) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (userId > 0) {
        const userData = {
          id: userId,
          name: 'User ' + userId,
          email: `user${userId}@example.com`
        };
        resolve(userData);
      } else {
        reject(new Error('Invalid user ID'));
      }
    }, 1000);
  });
}

fetchUserData(123)
  .then(user => console.log('User data:', user))
  .catch(error => console.error('Error:', error.message));
```

### Promise Chaining Example

```javascript
function getUser(userId) {
  return fetch(`https://api.example.com/users/${userId}`)
    .then(response => {
      if (!response.ok) throw new Error('User not found');
      return response.json();
    });
}

function getUserPosts(user) {
  return fetch(`https://api.example.com/users/${user.id}/posts`)
    .then(response => response.json());
}

getUser(1)
  .then(user => getUserPosts(user))
  .then(posts => console.log('User posts:', posts))
  .catch(error => console.error('Error:', error.message));
```

### Async/Await Example

```javascript
async function getUserWithPosts(userId) {
  try {
    const user = await getUser(userId);
    const posts = await getUserPosts(user);
    return { user, posts };
  } catch (error) {
    console.error('Error fetching user data:', error.message);
    throw error;
  }
}

getUserWithPosts(1)
  .then(data => console.log('User with posts:', data))
  .catch(error => console.error('Error:', error.message));
```

## License

MIT
