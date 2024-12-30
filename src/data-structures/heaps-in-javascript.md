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