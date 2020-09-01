# Find First and Last Position of Element in Sorted Array

Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]

```
import (
"fmt"
)

var max, min int

func assign_min_max(index int) {
    if min == -1 {
        min = index
        max = index
    }else if index < min {
        min = index
    }else if index > max {
        max = index
    }
}

func binary_search(nums []int, target int, left int, right int) {
    
    if left == right && nums[left] != target {
        return
    }
    
    if left == right && nums[left] == target {
        assign_min_max(left)
        assign_min_max(right)
        return
    }
    
    if right-left == 1  {
        if nums[left] == target {
            assign_min_max(left)    
        }
        if nums[right]==target{
            assign_min_max(right)
        }
        return 
    }
    
    mid := left+right
    if mid%2 == 0 {
        mid = mid/2
    }else {
        mid = (mid+1)/2
    }
    
    if nums[mid] == target {
        assign_min_max(mid)
        binary_search(nums[:], target, left, mid-1) 
        binary_search(nums[:], target, mid+1, right) 
        return 
    }
    
    if target < nums[mid]   {
        binary_search(nums[:], target, left, mid-1) 
        return 
    }else if target > nums[mid] {
        binary_search(nums[:], target, mid+1, right) 
        return 
    }
}

func searchRange(nums []int, target int) []int {
    max, min = -1, -1
    
    if len(nums) != 0 {
        binary_search(nums[:], target, 0, len(nums)-1)
    }
    
    fmt.Println(min, max)
    output := []int{min, max}
    return output
}
```
