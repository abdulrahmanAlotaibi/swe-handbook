# Techniques for Solving Data Structures Problems

## Techniques for Solving Data Structures Problems with Examples

## General

* You can use a map (hash table) to decrease time-complexity by sacrificing space-complexity
* Two pointer techniques
* Middle point is n/2 where n is the length of the list

## Arrays

*   Two pointers technique

    ```go
    /*  Explaining two pointers technique
    - 1 pointer starts from the begging and the second pointer 
    	starts from the end , they move toward each 
    */

    func reverseString(s []byte)  {
        for i, j:= 0, len(s)-1 ; i < j && i < len(s) ; i,j= i+1, j-1 {
            s[i], s[j] = s[j], s[i]
        }
        
    }
    ```

## Linked lists

#### 1. Keep a dummy pointer

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func hasCycle(head *ListNode) bool {
    
		// Keeping the head pointer in its own original place and looping with dummy pointer
    dummy := head 
    arr := []*ListNode{}
    for dummy != nil {
        for _, n := range arr {
            if dummy.Next == n {
                return true
            } 
        }
        arr = append(arr, dummy)
        dummy = dummy.Next
    }
    
    return false
}
```

#### 2. Slow runner runner and fast runner

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func hasCycle(head *ListNode) bool {
    
    dummy := head 
    arr := []*ListNode{}
    for dummy != nil {
        for _, n := range arr {
            if dummy.Next == n {
                return true
            } 
        }
        arr = append(arr, dummy)
        dummy = dummy.Next
    }
    
    return false
}
```

#### 3. Sentinel node doesn’t contain any value

#### 4. Looping with linked list

```go
// To loop through the whole list
for dummy != nil{
    dummy = dummy.Next
}

// To stop at the end of the list
for dummy.Next != nil{
    dummy = dummy.Next
}
```

#### 5. Try to keep state outside the loop if needed , for example in reversing list

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    dummy := head
    **var prev *ListNode**
    for dummy != nil {
        nextTemp := dummy.Next
        dummy.Next = prev
        prev = dummy
        dummy = nextTemp
    }

    return prev
}
```
