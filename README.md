# Async Flow Exercises

## Overview
This lab focuses on understanding how JavaScript handles asynchronous code execution.
Learners will explore concepts such as synchronous vs asynchronous behavior,
the Event Loop, Promises, async/await, and task queues.

---

# Learning Objectives

- Understand synchronous execution
- Identify asynchronous operations
- Predict output of async code
- Explain Event Loop behavior
- Differentiate between Microtask and Macrotask
- Debug async execution flow

---

# Step 1: Understanding Synchronous Execution

## Subtask 1.1: Write Basic Sync Code

### Example
```javascript
console.log("A");
console.log("B");
console.log("C");
```

### Expected Output
A
B
C

### Explanation
JavaScript executes synchronous code line by line in order.

---

# Step 2: Introduction to setTimeout (Macrotask)

## Subtask 2.1: Basic setTimeout Example

### Example
```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```

### Expected Output
Start
End
Timeout

### Explanation
setTimeout is placed into the Macrotask Queue and executes after synchronous code finishes.

---

# Step 3: Introduction to Promises (Microtask)

## Subtask 3.1: Basic Promise Example

### Example
```javascript
console.log("Start");

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

### Expected Output
Start
End
Promise

### Explanation
Promise callbacks go into the Microtask Queue, which executes before Macrotasks.

---

# Step 4: Microtask vs Macrotask Comparison

## Subtask 4.1: Combine Promise & setTimeout

### Example
```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

### Expected Output
Start
End
Promise
Timeout

### Explanation
Microtasks (Promises) execute before Macrotasks (setTimeout).

---

# Step 5: Async/Await Flow

## Subtask 5.1: Create Async Function

### Example
```javascript
async function test() {
  console.log("1");

  await Promise.resolve();

  console.log("2");
}

console.log("3");

test();

console.log("4");
```

### Expected Output
3
1
4
2

### Explanation
await pauses execution inside the async function and schedules the remaining code as a Microtask.

---

# Step 6: Advanced Flow Challenge

## Subtask 6.1: Predict the Output

### Example
```javascript
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

Promise.resolve().then(() => {
  console.log("C");
});

console.log("D");
```

### Expected Output
A
D
C
B

### Explanation
1. Synchronous code executes first (A and D).
2. Promise callback goes into Microtask Queue (C).
3. setTimeout callback goes into Macrotask Queue (B).
4. Microtasks execute before Macrotasks.

---

# Event Loop Summary

## Execution Order
1. Call Stack
2. Microtask Queue
3. Macrotask Queue

---

# Submission Guidelines

1. Create a GitHub repository
2. Upload all exercise files
3. Commit and push changes
4. Submit the GitHub repository link

---

# Conclusion

This lab strengthens understanding of JavaScript asynchronous behavior,
the Event Loop, Promises, async/await, and task scheduling.
