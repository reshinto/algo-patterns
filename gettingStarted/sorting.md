# Sorting
- `stable sorting algorithm` means that when two elements have the same value, their relative order is maintained
  - e.g. if we are sorting a hand of cards, and we have a Seven of Hearts before a Seven of Spades in the initial hand
    - after a stable sort, the Seven of Hearts is still before the Seven of Spades because their values are the same
    - However, in an unstable algorithm, the Seven of Spades might appear before the Seven of Hearts
    - The above is only true when we are comparing the cards by value, not suit
    - That is, two cards of the same value can be different
- `in-place sorting algorithm` means that the algorithm does not use additional data structure to hold temporary data
  - Additional memory cannot be avoided (as swapping two elements involve additional memory)
    - but they should be something like a temporary variable that uses very little additional memory
## Insertion Sort
- idea of an insertion sort is initially, only the first item is considered sorted
  - Then, for each item in the sequence, we "insert" that item into the sorted list by swapping that item with the item before it
  - until the item before it is smaller than the current item
- Imagine you are sorting a hand of cards
  - What people usually do is maintain a pile of sorted cards
  - and inserting from the unsorted pile into the sorted pile in the correct position
- It is a `stable algorithm` because later elements will not swap with earlier elements unless the later element is smaller
- it is an `in-place algorithm` because no additional data structure is used to store intermediate values
### JavaScript
```javascript
function sortList(unsortedList) {
  for (let i=0; i<unsortedList.length; i++) {
    let current = i;
    while (current > 0 && unsortedList[current] < unsortedList[current - 1]) {
      let temp = unsortedList[current];
      [unsortedList[current], unsortedList[current - 1]] = [unsortedList[current - 1], unsortedList[current]];
      current--;
    }
  }
}

const test = [2, 1, 8, 5, 3];
const res = sortList(test)
console.log(test)
```
### time space complexity
- For each n item in the list, the time complexity to insert it into the sorted list is `O(i)`
  - where i is the index of that item
- Overall, the time complexity is `O(n * (n - 1) / 2)`
  - which is equivalent to `O(n^2)`
## Selection Sort
## Bubble Sort
## Merge Sort
## Quick Sort
