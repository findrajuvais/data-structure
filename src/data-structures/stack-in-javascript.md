# Stacks

A stack is a data structure that follows the Last In, First Out (LIFO) principle. This means that the last element added to the stack is the first one to be removed.

#### Basic Operations:

1. Push: Add an element to the top of the stack.
2. Pop: Remove the element from the top of the stack.
3. Peek: View the element at the top of the stack without removing it.
4. isEmpty: Check if the stack is empty.
5. Size: Get the number of elements in the stack.

#### Basic Implementations:

##### Array to hold stack elements:

```javascript
let items = [];
```

##### Add an element to the stack:

```javascript
function push(item) {
  items.push(item);
}
```

##### Remove the top element from the stack:

```javascript
function pop() {
  if (isEmpty()) {
    return "Stack is empty";
  }
  return items.pop();
}
```

##### View the top element without removing it:

```javascript
function peek() {
  if (isEmpty()) {
    return "Stack is empty";
  }
  return items[items.length - 1];
}
```

##### Check if the stack is empty:

```javascript
function isEmpty() {
  return items.length === 0;
}
```

##### Get the number of elements in the stack:

```javascript
function size() {
  return items.length;
}
```

##### Clear the stack:

```javascript
function clear() {
  items = [];
}
```

##### Print the stack:

```javascript
function display() {
  console.log(items.toString());
}
```

##### Tests:
```javascript
push(10);
push(20);
push(30);

console.log(peek());  // Output: 30 (top element)
console.log(size());  // Output: 3

pop();  // Removes 30
console.log(peek());  // Output: 20 (now the top element)

print();  // Output: 10,20
console.log(isEmpty());  // Output: false

clear();
console.log(isEmpty());  // Output: true
```

#### Applications of Stacks:
1. Undo/Redo functionality in text editors.
2. Expression evaluation (e.g., converting infix to postfix).
3. Recursive function calls (the function call stack).
4. Backtracking algorithms (e.g., depth-first search in graphs).
