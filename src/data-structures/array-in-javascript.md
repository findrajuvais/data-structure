# Array

- An array is a built-in data structure that allows you to store multiple values in a single variable. Arrays are flexible, dynamic, and provide several methods for accessing, modifying, and iterating over elements.
- Each element in an array is stored at a specific index, starting from 0.
- Arrays in JavaScript are dynamic, meaning they can grow or shrink in size automatically as elements are added or removed.
- JavaScript arrays can hold values of any type (numbers, strings, objects, etc.).


### Creating an Array:

```javascript
// Using array literal
let arr = [1, 2, 3, 4, 5];

// Using the Array constructor
let arr2 = new Array(10);  // Creates an array of length 10, with all elements being undefined
let arr3 = new Array(1, 2, 3);  // Creates an array [1, 2, 3]
```

### Accessing Elements:

```javascript
let arr = [10, 20, 30, 40];
console.log(arr[0]); // Output: 10
console.log(arr[2]); // Output: 30

#### array length:
console.log(arr.length); // Output: 4
```

### Adding and Removing Elements:

```javascript
// Adding elements to the end
arr.push(5);  // arr = [1, 2, 3, 4, 5]

// Removing the last element
arr.pop();    // arr = [1, 2, 3, 4]

// Adding elements to the beginning
arr.unshift(0);  // arr = [0, 1, 2, 3, 4]

// Removing the first element
arr.shift();  // arr = [1, 2, 3, 4]
```

### Splice and Slice:

```javascript
// Splice: removes elements starting from index 2
arr.splice(1, 2); // arr = [1, 4] (removes 2 and 3) // you to remove from 1 index, remove only 2 index

// Slice: returns a shallow copy from index 1 to 2
let newArr = arr.slice(1, 2); // newArr = [4]
```

### Array Iteration:

```javascript
// Using for loop
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}

// Using forEach
arr.forEach((item) => {
  console.log(item);
});

// Using map (returns a new array)
let doubled = arr.map((item) => item * 2);
console.log(doubled); // Output: [2, 4, 6, 8] 
```

### Searching Elements:

```javascript
// Find index of an element
console.log(arr.indexOf(3));  // Output: 2

// Check if an element exists
console.log(arr.includes(2)); // Output: true

// Find an element using a condition
let found = arr.find((item) => item > 3); // Output: 4

// Filter elements using a condition
let filtered = arr.filter((item) => item > 2); // Output: [3, 4]
```

### Sorting and Reversing:

```javascript
let arr = [2, 3, 4, 1];
// Sort the array
arr.sort((a, b) => a - b); // Output: [1, 2, 3, 4]

// Reverse the array
arr.reverse(); // Output: [4, 3, 2, 1]
```

### Joining Elements:

```javascript
let arr = ['apple', 'banana', 'cherry'];
let joined = arr.join(', '); // Output: "apple, banana, cherry"
console.log(joined);
```

### Array Implementation:
```javascript
let items = {}
let length = 0;
```
#### Add an element to the end:
```javascript
function push(value) {
    items[length] = value;
    length++;
}
push(10); // items = [10]
push(20); // items = [10, 20]
push(30); // items = [10, 20, 30]
```
#### Remove the last element
```javascript
function pop() {
    if (length === 0) return undefined;
    const lastItem = items[length - 1];
    delete items[length - 1];
    length--;
    return lastItem;
}
pop(); // output: 30
```

#### Get an element by index
```javascript
function get(index) {
    return items[index];
}
get(0); // output: 10
```

#### Print all elements
```javascript
function print() {
    console.log(Object.values(items));
}

print(); // output: [10, 20];
```

### important links
-----





