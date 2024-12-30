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
function hash(key){
    let hashValue = 0;
    for (let i = 0; i < key.length; i++) {
      hashValue += key.charCodeAt(i);
    }
    return hashValue % size;
}
```

##### Insert a key-value pair into the hash table:
```javascript
function insert(key, value){
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
    return undefined;  // Return undefined if the key doesn't exist
}
```

##### Remove a key-value pair from the hash table:
```javascript
function remove(key){
    const index = hash(key);
    const bucket = table[index];
    
    if (bucket) {
      for (let i = 0; i < bucket.length; i++) {
        if (bucket[i][0] === key) {
          bucket.splice(i, 1);  // Remove the key-value pair from the bucket
          return true;
        }
      }
    }
    return false;  // Return false if the key doesn't exist
}
```

##### Check if a key exists in the hash table:
```javascript
function has(key){
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
console.log(get("age"));  // Output: 30
console.log(get("job"));  // Output: Engineer

remove("age");
console.log(get("age"));  // Output: undefined

console.log(has("name")); // Output: true
console.log(has("age"));  // Output: false

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
console.log(map.get("name"));  // Output: Alice

// Check key is exists or not into Map
console.log(map.has("age"));   // Output: true

// Remove value using key from Map
map.delete("job");
console.log(map.has("job"));   // Output: false
```

#### Time Complexity:
Insert: Average time complexity is O(1) but can degrade to O(n) in case of a collision (if many keys hash to the same index).
Get: Average time complexity is O(1) but can degrade to O(n) in case of a collision.
Remove: Average time complexity is O(1) but can degrade to O(n) in case of a collision.
Contains: Average time complexity is O(1) but can degrade to O(n) in case of a collision.