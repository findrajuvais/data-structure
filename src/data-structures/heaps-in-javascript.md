# Heaps

A heap is a special tree-based data structure that satisfies the heap property. A heap is typically implemented as a binary tree, where each parent node follows a specific order with respect to its children. Heaps are commonly used to implement priority queues, and they can be either a min-heap or a max-heap.

1. Min-Heap: The parent node is smaller than its children, meaning the smallest element is at the root.
2. Max-Heap: The parent node is larger than its children, meaning the largest element is at the root.

#### Basic Operations on Heaps:

1. Insertion: Add an element while maintaining the heap property.
2. Deletion (Extract Min/Max): Remove the root element (either min or max) and restore the heap property.
3. Heapify: Reorganize the heap to maintain the heap property after insertion or deletion.

#### Min-Heap Implementation:

##### Define heap:

```javascript
let heap = [];
```

##### Helper methods for heap operations:

```javascript
function parent(index) {
  return Math.floor((index - 1) / 2);
}

function leftChild(index) {
  return 2 * index + 1;
}

function rightChild(index) {
  return 2 * index + 2;
}
```

##### Swap two elements in the heap:

```javascript
function swap(index1, index2) {
  [heap[index1], heap[index2]] = [heap[index2], heap[index1]];
}
```

##### Insert a value into the heap:

```javascript
function insert(value) {
  heap.push(value); // Add the new value at the end of the heap
  heapifyUp(heap.length - 1); // Restore heap property
}
```

##### Heapify upwards (reorder the heap):

```javascript
function heapifyUp(index) {
  while (index > 0 && heap[index] < heap[parent(index)]) {
    swap(index, parent(index));
    index = parent(index);
  }
}
```

##### Extract the minimum value (remove the root):

```javascript
function extractMin() {
  if (heap.length === 0) return null;

  // The root is the minimum value
  const min = heap[0];
  // Replace the root with the last element
  heap[0] = heap.pop();
  // Restore heap property by heapifying down
  heapifyDown(0);
  return min;
}
```

##### Heapify down to restore the heap property after extraction:

```javascript
function heapifyDown(index) {
  let smallest = index;
  const left = leftChild(index);
  const right = rightChild(index);

  if (left < heap.length && heap[left] < heap[smallest]) {
    smallest = left;
  }

  if (right < heap.length && heap[right] < heap[smallest]) {
    smallest = right;
  }

  if (smallest !== index) {
    swap(index, smallest);
    heapifyDown(smallest);
  }
}
```

##### Peek at the root value (minimum value for Min-Heap):

```javascript
function peek() {
  return heap.length > 0 ? heap[0] : null;
}
```

##### Return the size of the heap:

```javascript
function size() {
  return heap.length;
}
```

##### Check if the heap is empty

```javascript
function isEmpty() {
  return heap.length === 0;
}
```

#### Max-Heap Implementation:

##### Define heap:

```javascript
let heap = [];
```

##### Helper method to get the parent index of a node:

```javascript
function getParentIndex(index) {
  return Math.floor((index - 1) / 2);
}
```

##### Helper method to get the left child index of a node:

```javascript
function getLeftChildIndex(index) {
  return 2 * index + 1;
}
```

##### Helper method to get the right child index of a node:

```javascript
function getRightChildIndex(index) {
  return 2 * index + 2;
}
```

##### Helper method to check if a node has a left child

```javascript
function hasLeftChild(index) {
  return getLeftChildIndex(index) < heap.length;
}
```

##### Helper method to check if a node has a right child

```javascript
function hasRightChild(index) {
  return getRightChildIndex(index) < this.heap.length;
}
```

##### Helper method to check if a node has a parent

```javascript
function hasParent(index) {
  return getParentIndex(index) >= 0;
}
```

##### Helper method to swap two elements in the heap

```javascript
function swap(index1, index2) {
  [heap[index1], heap[index2]] = [heap[index2], heap[index1]];
}
```

##### Method to insert a value into the heap

```javascript
function insert(value) {
  heap.push(value);
  heapifyUp();
}
```

##### Method to "bubble up" the inserted value to maintain heap property

```javascript
function heapifyUp() {
  let index = heap.length - 1;

  while (hasParent(index) && heap[getParentIndex(index)] < heap[index]) {
    swap(getParentIndex(index), index);
    index = getParentIndex(index);
  }
}
```

##### Method to remove and return the maximum value (root)

```javascript
function extractMax() {
  if (heap.length === 0) {
    throw new Error("Heap is empty");
  }

  const max = heap[0];
  heap[0] = heap[heap.length - 1];
  heap.pop();
  heapifyDown();
  return max;
}
```

##### Method to "bubble down" the root element to maintain heap property

```javascript
function heapifyDown() {
  let index = 0;

  while (hasLeftChild(index)) {
    let largerChildIndex = getLeftChildIndex(index);

    if (
      hasRightChild(index) &&
      heap[getRightChildIndex(index)] > heap[largerChildIndex]
    ) {
      largerChildIndex = getRightChildIndex(index);
    }

    if (heap[index] > heap[largerChildIndex]) {
      break;
    }

    swap(index, largerChildIndex);
    index = largerChildIndex;
  }
}
```

##### Method to peek at the maximum value (root)

```javascript
function peek() {
  if (heap.length === 0) {
    throw new Error("Heap is empty");
  }
  return heap[0];
}
```

##### Method to check the size of the heap:

```javascript
function size() {
  return heap.length;
}
```

##### Max-heap Tests:

```javascript
insert(10);
insert(20);
insert(5);
insert(30);

console.log(peek()); // 30 (maximum element)
console.log(extractMax()); // 30 (extract maximum)
console.log(peek()); // 20 (new maximum)
console.log(size()); // 3 (heap size)
```


#### Next:
- [Priority Queue Implementation](priority-queue-implementation.md)
