# Word Break
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

Note:

The same word in the dictionary may be reused multiple times in the segmentation.
You may assume the dictionary does not contain duplicate words.
Example 1:

Input: s = "leetcode", wordDict = ["leet", "code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".

```
import(
"fmt"
)

func trace(s string, wordDict []string, hash map[string]int) bool {
    if hash[s] != 0 {
        return false
    }
    
    hash[s] = 1
    
    for _, word := range wordDict {
        if len(word) <= len(s) && s[0:len(word)] == word {
            if len(s[len(word):]) == 0 {
                return true
            }
            
            if trace(s[len(word):], wordDict[:], hash) == true {
                return true
            }
        }
    }
    return false
}

func wordBreak(s string, wordDict []string) bool {
    hash:=make(map[string]int)
    return trace(s, wordDict[:], hash)
}
```
