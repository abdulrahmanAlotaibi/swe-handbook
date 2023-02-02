# Data Structures ADTs Implementation (In Go)

## Data Structures ADTs Implementation (In Go)

## Linked list

```go
package main 

import "fmt"

func main (){

	var l = LinkedList{}
	var p Person= Person{"Abdulrahman",3} 

	l.insert(&p)
	l.insert(&Person{"John", 19})
	l.insert(&Person{"Bob", 19})
	l.insert(&Person{"Jack", 19})
	l.insert(&Person{"Martin", 19})

	l.remove()
	
	l.display()

}

type Person struct {
	name string
	age int
}

var p = Person{"",3}

type Node struct {
	data *Person
	next *Node
}

type LinkedList struct {
	head *Node
	current *Node
}

func (l *LinkedList) isEmpty() bool {
	return l.head == nil
} 

func (l *LinkedList) findNext(){
	l.current = l.current.next
}

func (l *LinkedList) insert(val *Person){
	if l.head == nil {
		l.current = &Node{val,nil}	
		l.head = l.current
	} else {
		tmp:= l.current.next
		
		n:= Node{val, tmp}
		
		l.current.next = &n

		l.current = l.current.next
		
	}

}

func (l *LinkedList) remove() {
	if l.current == l.head {
		l.head = l.head.next
	} else {
        	temp:= l.head
        	for temp.next != l.current {
                	temp = temp.next
        	}
		temp.next = l.current.next
	}
	if l.current.next == nil {
		l.current = l.head 
	}else{
		l.current = l.current.next
	}

}

func (l *LinkedList) display(){
	p:= l.head
	for p != nil {
		fmt.Printf("%v -> ", p.data)
		
		p = p.next
	}
	fmt.Println()
}
```

## Stack (Array-based)

```go
package main 

import (
	"fmt"
	"errors"
	"log"
)

func Check(err error) {
	if err != nil {
		log.Fatal(err)
	}
	
}

type Stack [] string

func main (){

	var stack Stack

	stack.Push("John Wick")
	stack.Push("Spiderman")
	stack.Push("Mary Jane")
	stack.Push("Superman")

	stack.Display()

  item ,err:=stack.peek()
  Check(err)
  fmt.Println("Peek Item value: ", item)
  
	item1, err :=stack.Pop()
	Check(err)

	fmt.Println("Item1 value: ", item1)

	stack.Display()

	item2, err :=stack.Pop()
	Check(err)

	fmt.Println("Item2 value: ", item2)

	item3,err :=stack.Pop()

	Check(err)
	fmt.Println("Item3 value: ", item3)

	// Empty stack : This will throw an error
	item4,err :=stack.Pop() 
	Check(err)
	
	fmt.Println("Item4 value: ", item4)

	// Display the stack items
	stack.Display()

}

func (stack *Stack) Pop () (string, error){
	 
  stack.isEmpty()	

	item := (*stack)[len(*stack) - 1]

	*stack = (*stack)[:len(*stack) - 1]
	fmt.Println("Item has been popped out successfully")

	return item, nil
}

func (stack *Stack) Push(item string) {

	*stack = append(*stack, item)

	fmt.Println("Item has been pushed successfully")
}

func (stack *Stack) Display(){

	for i, item := range *stack {
		fmt.Printf("[%d] : %s\n", i, item)
	}
	
}

func (stack *Stack) isEmpty() {
  if len(*stack) == 0 {
		errors.New("The stack is empty")
	}  
}

func (stack *Stack) peek()(string, error) {
  stack.isEmpty()
	item := (*stack)[len(*stack) - 1]
  return item, nil
}
```

## Stack (linked-list based)

## Binary Tree

```go
package main

import "fmt"

const  (
  PreOrder  = "preOrder"
  InOrder  = "inOrder"
  PostOrder = "postOrder"
  Root = "root"
  LeftChild = "leftChild"
  RightChild = "rightChild"
  Parent = "parent"
)

type node struct {
  data int 
  left *node
  right *node
}

type binaryTree struct {
  root *node 
  current *node
}

func main(){
    var bt binaryTree = binaryTree{nil, nil}
    
    bt.insert(90, Root)
    fmt.Println(bt.current)
    bt.insert(20, RightChild)
    bt.find(Parent)
    bt.insert(16, LeftChild)
    bt.find(Parent)
  
    fmt.Println(bt.current)

    bt.find(LeftChild)
    
    bt.deleteSubTree()

    fmt.Println(bt.current)
}

func (bt *binaryTree) insert(data int, relative string ) bool {
  switch relative {
    case Root:
      if !bt.isTreeEmpty() {
        return false
      }
      n := node{data,nil,nil}
      bt.root = &n
      bt.current = bt.root
      return true
    case Parent:{
      // You can't find the parent of the root
      if bt.current == bt.root {
        return false 
      }
      bt.current = findParent(bt.current, bt.root)
      return true
    }
    case LeftChild:
      if bt.current.left != nil {
        return false
      }
      n := node{data, nil, nil}
      bt.current.left = &n
      bt.current = bt.current.left
      return true
    case RightChild:
      if bt.current.right != nil {
        return false
      }
      n := node{data, nil, nil}
      bt.current.right = &n
      bt.current = bt.current.right
      return true
    default:
      return false
  }
}

func (bt *binaryTree) deleteSubTree() {
  if bt.current == bt.root {
    bt.root = nil
    bt.current = bt.root
  } else {
    n := bt.current
    bt.find(Parent)
    if(bt.current.left == n){
      bt.current.left = nil
    } else if (bt.current.right == n){
      bt.current.right = nil
    }
    bt.current = bt.root
  }
  
}

func (bt *binaryTree) update(data int){
  bt.current.data = data
}

func (bt *binaryTree) retrieve(data int) *node{
  return bt.current
}

func  (bt *binaryTree) find(relative string)bool{
  switch relative{
    case Root :{
      bt.current = bt.root
      return true
    }
    case Parent:{
      if bt.current == bt.root {
        return false
      }
      bt.current = findParent(bt.current, bt.root)
      return true
    }
    case LeftChild:{
      if bt.current.left == nil {
        return false
      }
      bt.current  = bt.current.left
      return true
    }
    case RightChild:{
      if bt.current.right == nil {
        return false
      }
      bt.current  = bt.current.right
      return true
    }
    default:{
      return false
    }
  }

}

func findParent (n *node, root *node)*node{
  if root == nil {
    return nil
  }
  if root.right == nil && root.left == nil {
    return nil
  } else if root.right == n || root.left == n {
      return root
  }else {
    tmp:= findParent(n, root.right)
    if tmp != nil {
      return tmp.left
    }else {
      return findParent(n, root.left)
    }
  }
} 

func (bt *binaryTree) isTreeEmpty() bool {
  return bt.root == nil
}
```

## Queue

```go
package main
import "fmt"

type node struct {
  data int 
  next *node
}

type queue struct {
  head *node
  tail *node
  size int
}

func main(){
  q:= queue{nil,nil,10}
  fmt.Println(q)

  q.enqueue(10)
  q.enqueue(20)
  q.enqueue(0)

  fmt.Println(*q.find(10))

  q.display()
} 

func (q *queue) enqueue(data int){
  n:= node{data, nil}
  if q.head == nil {
    q.head = &n
    q.tail = &n
  }else {  
    q.tail.next = &n
    q.tail = q.tail.next
  }
  q.size++
}

func (q *queue) dequeue () int {
  data := q.head.data
  q.head = q.head.next
  q.size--
  if q.size == 0 {
    q.tail = nil
  }
  return data
}

func (q *queue) find(data int) *node{
  tmp := q.head

  for tmp != nil {
    if tmp.data == data {
      return tmp
    }
    tmp = tmp.next
  }
  return nil
}

func (q *queue) display(){
  tmp := q.head
  for tmp.next != nil {
    fmt.Print(tmp.data ," --> ")
    tmp = tmp.next
  }
  if &tmp != nil {
    fmt.Print(tmp.data )
  }
}
```

## Ring Buffer (Circular Queue)

```go
type MyCircularQueue struct {
    size int
    head int
    queue []int
}

func Constructor(k int) MyCircularQueue {
    queue := make([]int, k)
    size := 0
    head := 0
    
    return MyCircularQueue{
        queue:queue,
        size:size,
        head:head,
    }
}

func (this *MyCircularQueue) EnQueue(value int) bool {
    if this.IsFull(){
        return false
    }
    
    this.queue[(this.head + this.size) % cap(this.queue)] = value
    
    this.size++
    
    return true
}

func (this *MyCircularQueue) DeQueue() bool {
    if this.IsEmpty(){
        return false
    }
    
    this.head = (this.head+1) % cap(this.queue)
   
    this.size--
    return true
}

func (this *MyCircularQueue) Front() int {
    if this.IsEmpty(){
        return -1
    }
    return this.queue[this.head]   
}

func (this *MyCircularQueue) Rear() int {
     if this.IsEmpty(){
        return -1
    }
    return this.queue[(this.head + this.size -1) % cap(this.queue)] 
}

func (this *MyCircularQueue) IsEmpty() bool {
    return this.size == 0
}

func (this *MyCircularQueue) IsFull() bool {
    return this.size == cap(this.queue)
}

/**
 * Your MyCircularQueue object will be instantiated and called as such:
 * obj := Constructor(k);
 * param_1 := obj.EnQueue(value);
 * param_2 := obj.DeQueue();
 * param_3 := obj.Front();
 * param_4 := obj.Rear();
 * param_5 := obj.IsEmpty();
 * param_6 := obj.IsFull();
 */
```
