# Arrays:

An array is a linear data structure that stores a collection of elements of the same data type in contiguous memory locations. It provides a way to access and manipulate a group of related data efficiently.

## Characteristics:

1. Homogeneous Elements: Arrays store elements of the same data type (e.g., integers, characters, objects).
2. Fixed Size: In many programming languages, arrays have a fixed size defined at the time of creation, which cannot be changed later.
3. Contiguous Memory: Elements in an array are stored in adjacent memory locations, allowing for efficient access and traversal.
4. Zero-Based Indexing: Array indices start from 0 in most programming languages.
5. Random Access: Elements can be accessed directly using their indices, leading to constant-time access.

## Operations:

1. Insertion/Deletion: Inserting or deleting elements from an array can be inefficient because it may require shifting other elements to accommodate the change. Insertions and deletions at the end of the array are usually faster.
2. Access/Update: Accessing and updating elements in an array is fast and takes constant time, O(1), because of direct indexing.
3. Traversal: Elements can be traversed sequentially using loops, visiting each element exactly once.
4. Search: Linear search (O(n)) or binary search (O(log n)) can be performed on sorted arrays.
5. Sorting: Arrays can be sorted using various sorting algorithms, such as quicksort, mergesort, or bubblesort.
6. Merging: Two sorted arrays can be merged into a single sorted array in O(n) time.
7. Copying: Copying elements between arrays can be time-consuming depending on the number of elements.

## Complexities:

1. Access Time: O(1)
2. Insertion Time (at the end): O(1)
3. Insertion Time (at the beginning): O(n)
4. Insertion Time (in the middle): O(n)
5. Deletion Time (at the end): O(1)
6. Deletion Time (at the beginning): O(n)
7. Deletion Time (in the middle): O(n)
8. Search Time (Unsorted): O(n)
9. Search Time (Sorted - Binary Search): O(log n)

## Pros:

1. Fast and constant-time access using indices.
2. Simple and intuitive structure.
3. Suitable for situations where size is known and remains fixed.
4. Efficient for small-sized collections.

## Cons:

1. Fixed size can lead to memory wastage or insufficient space.
2. Inefficient insertion and deletion operations.
3. Dynamic resizing (in languages with dynamic arrays) can lead to performance overhead.

## Languages with Built-in Arrays:

Most programming languages provide built-in support for arrays, including:

1. Java: int[] arr = new int[5];
2. Python: arr = [1, 2, 3, 4, 5]
3. C++: int arr[5];
4. JavaScript: let arr = [1, 2, 3, 4, 5];

In modern languages like Python and JavaScript, dynamic arrays automatically resize as needed.

Note: Some languages provide arrays with different characteristics, like resizable arrays (ArrayList in Java) and associative arrays (dictionaries/maps in Python/JavaScript), which are implemented as hash tables.

Arrays are fundamental data structures that play a crucial role in computer programming due to their efficiency in access and various applications in algorithms and problem-solving.

# Algorithms

## Binary Search

```
// Binary Search (Sorted Array)
// TC: O(logN) SC: O(1)

const binarySearch = (nums, target) => {
  let start = 0, end = nums.length - 1;
  while(start <= end) {
    const mid = Math.floor(start + (end - start) / 2);
    if(nums[mid] === target) return mid;
    else if(nums[mid] < target) start = mid + 1;
    else end = mid - 1;
  }
  return -1;
}


const nums = [1,2,3,4,4,10,10,20,30,80, 100, 100, 200, 1000];

console.log(binarySearch(nums, 30));
console.log(binarySearch(nums, 1000));
console.log(binarySearch(nums, 1));
console.log(binarySearch(nums, 60));
console.log(binarySearch(nums, 80));
```

## Merge Sort

```
// Merge Sort
// TC: O(NlogN) SC: O(N)

const merge = (nums, start, mid, end) => {
  let indexStart = start;
  let indexMid = mid + 1;
  const merged = [];
  while(indexStart <= mid && indexMid <= end) {
    if(nums[indexStart] < nums[indexMid]) merged.push(nums[indexStart++]);
    else merged.push(nums[indexMid++]);
  }
  while(indexStart <= mid) merged.push(nums[indexStart++]);
  while(indexMid <= end) merged.push(nums[indexMid++]);
  for(let i=0; i<merged.length; i++) {
    nums[start] = merged[i];
    start++;
  }
}

const mergeSort = (nums, start, end) => {
  if(start >= end) return;
  const mid = Math.floor(start + (end - start) / 2);
  mergeSort(nums, start, mid);
  mergeSort(nums, mid + 1, end);
  merge(nums, start, mid, end);
}

const nums = [10,40, 20, 60, 50, 50, 100, 80, 90, 10];

mergeSort(nums,0, nums.length - 1);

console.log(nums);
```
