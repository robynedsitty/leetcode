# 1768. Merge Strings Alternately

## About the problem
- *Problem Number* : 1768
- *Problem Name* :  [Merge Strings Alternately]([[https://leetcode.com/problems/find-words-containing-character/description/ "https://leetcode.com/problems/find-words-containing-character/description/](https://leetcode.com/problems/candy/description/?envType=daily-question&envId=2025-06-02)](https://leetcode.com/problems/merge-strings-alternately/description/?envType=study-plan-v2&envId=programming-skills)")
- *Problem difficulty* : Easy 🟢
- *Programming language used* - Java

## Problem

You are given two strings `word1` and `word2`. 
Merge the strings by adding letters in alternating order, starting with `word1`. 
If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the *the merged string*.

**Example 1:**

```
Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Explanation: The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
```

**Example 2:**

```
Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Explanation: Notice that as word2 is longer, "rs" is appended to the end.
word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s
```

**Example 3:**

```
Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Explanation: Notice that as word1 is longer, "cd" is appended to the end.
word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d
```

**Constraints:**

-   `1 <= word1.length, word2.length <= 100`
-   `word1` and `word2` consist of lowercase English letters.

## Answer
**Java Attempt 1 - Runtime 7ms:**
-   while loop with two pointers to go through both words.
-   add character to the string ans
-   `ans += char` creates a new String object everytime it is appended in Java.
```
class Solution {
    public String mergeAlternately(String word1, String word2) {
        
        String ans = "";

        int i = 0, j=0;

        while( i < word1.length() || j < word2.length()){
            if( i < word1.length()){
                ans += word1.charAt(i);
                i++;
            }
            if( j < word2.length()){
                ans += word2.charAt(j);
                j++;
            }
        }
        return ans;
    }
}
```

**Java Attempt 2 - Runtime 1ms - Complexity O(N+M):**
-   use StringBuilder, which is designed for efficient string concatenation
-   StringBuilder modifies the same buffer internally instead of creating a new String everytime.
-   reduces memory overhead and runtime.
```
class Solution {
    public String mergeAlternately(String word1, String word2) {
        
        StringBuilder ans = new StringBuilder();

        int i = 0, j=0;

        while( i < word1.length() || j < word2.length()){
            if( i < word1.length()){
                ans.append(word1.charAt(i));
                i++;
            }
            if( j < word2.length()){
                ans.append(word2.charAt(j));
                j++;
            }
        }
        return ans.toString();
    }
}
```
