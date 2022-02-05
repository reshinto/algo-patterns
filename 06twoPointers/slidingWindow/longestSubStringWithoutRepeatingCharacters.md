# Two Pointers: Sliding Window
## Longest Substring Without Repeating Characters
```
Find the length of the longest substring of a given string without repeating characters.

Input: abccabcabcc

Output: 3

Explanation: longest substrings are abc, cab, both of length 3


Input: aaaabaaa

Output: 2

Explanation: ab is the longest substring, length 2
```
```javascript
function longestSubstringWithoutRepeatingCharacters(s) {
  let slow = 0;
  let fast = 0;
  let result = 1;
  const memo = {};
  while (fast < s.length) {  // check fast because it will reach the end first
    const char = s[fast];
    if (!memo[char]) {
      memo[char] = true;
      fast++;
    } else {
      delete memo[char];  // remove from memory so that fast can continue to move forward
      slow++;
    }
    result = Math.max(result, fast - slow);
  }
  return result;
}
```
```
f                   longest: 1, add A
A B C D B E A
s

  f                 longest: 2, add B
A B C D B E A
s

    f               longest: 3, add C
A B C D B E A
s

      f             longest: 4, add D
A B C D B E A
s

        f           delete B
A B C D B E A
s

        f           longest: 4, add B
A B C D B E A
  s
  
          f         longest: 5, add E
A B C D B E A
  s

            f       delete A
A B C D B E A
  s
  
            f       longest: 5, add A
A B C D B E A
    s
    
              f     loop breaks
A B C D B E A
    s
```
### Explanation
- For a substring starting with start that already contains one duplicate character we want to stop checking more substrings with start index
- When this happens we want to increment start and look at next set of substrings
- This makes it a classic sliding window problem
  - A sliding window is defined by two pointers
    - We move the window (incrementing pointers) whiles maintaining a certain variant
    - For this particular problem, the variant is the characters inside the window being unique
      - We use a set to record what's in the window
        - And when we encounter a character that's already in the window
        - we want to move the left pointer until it goes past the last occurrence of that character
- Time Complexity: `O(n)`
