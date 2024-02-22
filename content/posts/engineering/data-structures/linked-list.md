---
title: "Linked Lists in Go"
date: 2024-02-22
draft: false
categories: ["Engineering", "Data Structures"]
tags: ["go", "linked list", "ds", "data structures"]
---

I love the [5 rules of programming](https://users.ece.utexas.edu/~adnan/pike.html) by Rob Pike. Especially his last rule which points to the fact that data structures, not algorithms are central to programming. Every problem in software engineering is a data problem. In fact, we're paid to transform data from one form to another. At the end of the day, data is at the heart of software industry.

With that being said, I'm going to start the series of data structures using Go programming language. And why not start with plain and simple linked lists. Linked list is popular data structure that consists of zero or more nodes indexed starting from zero. Nodes themselves are two-part data structure which holds the data to be used and a pointer to the next node.

Let's first initialize Go module by typing the following at the root of our project directory:

```bash
$ go mod init linked-list.i33y.dev
```

We'll write our linked list API inside the ``list`` package. Good API must be ``easy to use and hard to misuse``. Therefore, it is best to make the internal detaials of our List un-exportable and keeping the length of the List invariant. Whenever an invalid index is given, the application will panic.

```go
package list

import "sync"

type node[T any] struct {
	data T
	next *node[T]
}

type List[T any] struct {
	head   *node[T]
	length int // keep the length invariant
	mu     sync.Mutex
}

func NewList[T any]() *List[T] {
	return &List[T]{
		head:   nil,
		length: 0,
		mu:     sync.Mutex{},
	}
}

func (l *List[T]) Insert(index int, data T) {
	l.mu.Lock()
	defer l.mu.Unlock()

	if index < 0 || index > l.length {
		panic("index out of boundaries")
	}

	if index == 0 {
		l.head = &node[T]{
			data: data,
			next: l.head,
		}
		l.length++

		return
	}

	temp := l.head
	for i := 0; i < index-1; i++ {
		temp = temp.next
	}

	temp.next = &node[T]{
		data: data,
		next: temp.next,
	}
	l.length++
}

func (l *List[T]) Get(index int) T {
	l.mu.Lock()
	defer l.mu.Unlock()

	if index < 0 || index > l.length-1 {
		panic("index out of boundaries")
	}

	temp := l.head
	for i := 0; i < index; i++ {
		temp = temp.next
	}

	return temp.data
}

func (l *List[T]) Update(index int, data T) {
	l.mu.Lock()
	defer l.mu.Unlock()

	if index < 0 || index > l.length-1 {
		panic("index out of boundaries")
	}

	temp := l.head
	for i := 0; i < index; i++ {
		temp = temp.next
	}

	temp.data = data
}

func (l *List[T]) Delete(index int) {
	l.mu.Lock()
	defer l.mu.Unlock()

	if index < 0 || index > l.length-1 {
		panic("index out of boundaries")
	}

	if index == 0 {
		l.head = l.head.next
		l.length--

		return
	}

	temp := l.head
	for i := 0; i < index-1; i++ {
		temp = temp.next
	}
	temp.next = temp.next.next
	l.length--
}

func (l *List[T]) Append(data T) {
	l.Insert(l.length, data)
}

func (l *List[T]) Prepend(data T) {
	l.Insert(0, data)
}
```

Let's test our linked list API by initializing, populating, and manipulating it.

```go
package main

import (
	"fmt"

	"linked-list.i33y.dev/list"
)

func main() {
	numbers := list.NewList[int]()

	// populate the list
	numbers.Append(12)
	numbers.Prepend(13)
	numbers.Prepend(5)
	numbers.Append(20)
	numbers.Prepend(23)

	second := numbers.Get(1)
	fmt.Printf("second number: %d\n", second)

	numbers.Update(1, 14)
	second = numbers.Get(1)
	fmt.Printf("new second number: %d\n", second)

	numbers.Delete(1)
	second = numbers.Get(1)
	fmt.Printf("final second number: %d\n", second)

	names := list.NewList[string]()

	// populate the list
	names.Prepend("abraham")
	names.Append("noah")
	names.Append("joseph")
	names.Prepend("moses")
	names.Insert(2, "jesus")

	third := names.Get(2)
	fmt.Printf("third name: %s\n", third)

	names.Update(2, "adam")
	third = names.Get(2)
	fmt.Printf("new third name: %s\n", third)

	names.Delete(1)
	third = names.Get(2)
	fmt.Printf("final third name: %s\n", third)
}
```

When you run the program, you should recieve something like:

```bash
$ go run main.go

second number: 5
new second number: 14
final second number: 13
third name: jesus
new third name: adam
final third name: noah
```

There's a lot to finetune. ``Get`` method of our List does not need to be pointer-reciever, but for consistency reasons, it was made in a such way.