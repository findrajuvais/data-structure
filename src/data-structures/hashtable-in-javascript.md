# Hash Tables

In JavaScript, a hash table is a data structure that maps keys to values. It allows for fast retrieval, insertion, and deletion of key-value pairs based on the key.

Build-in hashtable - Map

### Hash Tables implementations:

##### Implementation of basic hash tables define:

```javascript
let size = 100; // default size:100
let table = new Array(size);
```

##### Hash function to calculate index based on key:

```javascript
function hash(key) {
  let hashValue = 0;
  for (let i = 0; i < key.length; i++) {
    hashValue += key.charCodeAt(i);
  }
  return hashValue % size;
}
```

##### Insert a key-value pair into the hash table:

```javascript
function insert(key, value) {
  const index = hash(key);
  if (!table[index]) {
    table[index] = [];
  }
  table[index].push([key, value]);
}
```

##### Retrieve the value associated with a key:

```javascript
function get(key) {
  const index = hash(key);
  const bucket = table[index];

  if (bucket) {
    for (let i = 0; i < bucket.length; i++) {
      if (bucket[i][0] === key) {
        return bucket[i][1];
      }
    }
  }
  return undefined; // Return undefined if the key doesn't exist
}
```

##### Remove a key-value pair from the hash table:

```javascript
function remove(key) {
  const index = hash(key);
  const bucket = table[index];

  if (bucket) {
    for (let i = 0; i < bucket.length; i++) {
      if (bucket[i][0] === key) {
        bucket.splice(i, 1); // Remove the key-value pair from the bucket
        return true;
      }
    }
  }
  return false; // Return false if the key doesn't exist
}
```

##### Check if a key exists in the hash table:

```javascript
function has(key) {
  const index = hash(key);
  const bucket = table[index];

  if (bucket) {
    for (let i = 0; i < bucket.length; i++) {
      if (bucket[i][0] === key) {
        return true;
      }
    }
  }
  return false;
}
```

##### Display the hash table:

```javascript
function display() {
  console.log(table);
}
```

##### Tests:

```javascript
insert("name", "Alice");
insert("age", 30);
insert("job", "Engineer");

console.log(get("name")); // Output: Alice
console.log(get("age")); // Output: 30
console.log(get("job")); // Output: Engineer

remove("age");
console.log(get("age")); // Output: undefined

console.log(has("name")); // Output: true
console.log(has("age")); // Output: false

display();
```

#### Using Build-in Hash Tables in Javascript:

```javascript
//Initiated Map
const map = new Map();

// Insert into Map
map.set("name", "Alice");
map.set("age", 30);
map.set("job", "Engineer");

// Get value using key from Map
console.log(map.get("name")); // Output: Alice

// Check key is exists or not into Map
console.log(map.has("age")); // Output: true

// Remove value using key from Map
map.delete("job");
console.log(map.has("job")); // Output: false
```

#### Sets are a built-in data structure in JavaScript, available since ECMAScript 6 (ES6):

##### Creating a sets:

```javascript
const mySet = new Set();
mySet.add(1);
mySet.add(2);
mySet.add(3);

console.log(mySet); // Output: Set { 1, 2, 3 }
```

##### Checking if a Value Exists:

```javascript
console.log(mySet.has(3)); // Output: true
console.log(mySet.has(10)); // Output: false
```

##### Removing Values:

```javascript
mySet.delete(3); // Removes 3 from the set
console.log(mySet); // Output: Set { 1, 2 }

mySet.clear(); // Clears the entire set
console.log(mySet); // Output: Set {}
```

##### Iterating Over a Set:

```javascript
// using for..of loop
for (const value of mySet) {
  console.log(value); // Output: 1, 2, 3 (each on a new line)
}

// using .forEach loop
mySet.forEach((value) => {
  console.log(value); // Output: 1, 2, 3 (each on a new line)
});
```

##### Check Set size:

```javascript
console.log(mySet.size); // Output: 3
```

##### Set for Unique Values in an Array:

```javascript
const arr = [1, 2, 2, 3, 4, 4, 5];
const uniqueSet = new Set(arr);
console.log([...uniqueSet]); // Output: [1, 2, 3, 4, 5]
```

#### Time Complexity:

1. Insert: Average time complexity is O(1) but can degrade to O(n) in case of a collision (if many keys hash to the same index).
2. Get: Average time complexity is O(1) but can degrade to O(n) in case of a collision.
3. Remove: Average time complexity is O(1) but can degrade to O(n) in case of a collision.
4. Contains: Average time complexity is O(1) but can degrade to O(n) in case of a collision.

#### Advantages of Hash Tables:

1. Fast Lookups: The average time complexity for searching, inserting, and deleting entries in a hash table is O(1), making them very efficient.
2. Memory Efficiency: Hash tables provide an efficient way to store and access data compared to other data structures like arrays or linked lists.

#### Disadvantages:

1. Collision Handling: Hash tables may experience collisions (when two different keys hash to the same index), and the implementation of collision resolution methods (like chaining or open addressing) can complicate their use.
2. Space Complexity: Hash tables can require extra memory for handling collisions and maintaining the hash table itself, especially when the hash table size is larger than necessary for the number of entries.

#### Applications of Hash Tables:

1. Caching
2. Database Indexing
3. Symbol Tables in Compilers
4. Associative Arrays / Dictionaries
5. Set Operations
6. Load Balancing
7. Cryptography (Hash Functions)
8. Counting and Frequency Analysis
9. Finding Duplicates
10. Routing Tables in Networks
11. Autocomplete and Spell Checker
12. Graph Algorithms (Adjacency List)
13. Distributed Systems (Sharding)
14. Unique Identification
