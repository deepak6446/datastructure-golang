Given a string, find the length of the longest substring without repeating characters.

Input: "abcabcbb" </br>
Output: 3 </br>
Explanation: The answer is "abc", with the length of 3. </br>

# Sliding Window 

```
import (
    "fmt"
)

//sliding window algorithm O(n)
func lengthOfLongestSubstring(s string) int {
    l, r := 0, 0 
    hash := make(map[byte]int) 
    max_sub_len := 0  
        
    for r < len(s)  {
        //check if character contains in substring
        if hash[s[r]] != 1  {
            //add substring
            hash[s[r]] = 1
            r = r + 1
            //check if substring has max length
            if r-l > max_sub_len {
                max_sub_len = r-l
            }
        } else {
            //shift left counter
            hash[s[l]] = 0
            l = l + 1
        }
    }
    return max_sub_len
}
```
