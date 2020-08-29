You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

[Example](https://leetcode.com/problems/add-two-numbers/):

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4) </br>
Output: 7 -> 0 -> 8 </br>
Explanation: 342 + 465 = 807.

```
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

import (
"fmt"
)

func addTwoNumbers(l1 *ListNode, l2 *ListNode)  *ListNode {
    sum, carry := 0, 0
    head := &ListNode{Val:11}
    curr := &ListNode{}
    
    for(l1 != nil || l2 != nil) {
        
        if(l1!=nil) {
            sum = sum + l1.Val
            l1 = l1.Next
        }
        if(l2!=nil) {
            sum = sum + l2.Val
            l2 = l2.Next
        }
        sum = sum + carry
        carry=0
        if(sum>=10) {
           sum = sum - 10
           carry = 1 
        }
        l3 := &ListNode{Val:sum, Next:nil}
        if(head.Val == 11) {
            head = l3    
        }else {
            curr.Next = l3
        }
        
        curr = l3
        sum = 0
    }
    
    if(carry != 0) {
        l3 := &ListNode{Val:carry, Next:nil}
        curr.Next = l3
    }
    
    if(head.Val == 11){
        return nil
    }
    
    return head
}

```
