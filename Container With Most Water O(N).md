# [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

```
import (
"fmt"
)

func maxArea(height []int) int {
    //get two pointers 
    // one pointing to start(l) and pointing to end
    l:=len(height)-1
    r:=0
    
    max_vol:=0
    mix_height := 0
    
    //if there is only one line
    if l == 0 {
        return 0
    }
    
    for r<l {
        width := (l-r)
        
        //get min height form two and calulate volume
        //check if there is any vertical with max height.
        if height[l] < height[r] {
            mix_height = height[l]
            if max_vol < (width*mix_height) {
                max_vol = (l-r)*mix_height
            }
            l--
        }else {
            mix_height = height[r]
            if max_vol < (width*mix_height) {
                max_vol = (l-r)*mix_height
            }
            r++
        }
    }
    return max_vol
}
```
