---
title: "Linkedlist Implementation In Javascript"
tag: "programming"
---

# Implement LinkedList in JavaScript

_January 27, 2022 by Ulan Rakymzhanov_

**LinkedList** is one of the hardest data structures to learn for beginners.

Some languages support it but in some languages we have to implement the LL class ourselves.

Implementing LinkedList is not hard in terms of coding but finding patterns to solve questions or implement it can be confusing and against our typical way of thinking.

That is the reason i wanted to write this blog — not about actual coding but more of a pseudo coding with some graphics.

First and foremost let's create our base **Node** class:

## Node class

- It has `value` and `next` properties

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
```

General tasks performed in LinkedList: `Insert` and `Delete` (maybe `Reverse`)

**Insert**: addToStart, addToEnd, addAtIndex

**Delete**: removeFromStart, removeFromEnd, removeFromIndex

**General**: getAtIndex, setAtIndex

Now let's also create our LinkedList class:

## LinkedList class

- It has `head`, `tail` and `size` properties

```js
class LinkedList {
  constructor(value) {
    const new_node = new Node(value);
    this.head = new_node;
    this.tail = this.head;
    this.size = 1;
  }
  // your method implementations go here
}
```

#### Implement `addToEnd` method:

1. Create a new node based on value
2. Check if head is null, if yes assign new node to head and tail
3. Else, assign tail next to new node and move tail pointer to new node
4. Increase the size of ll
5. Return ll

#### Implement `removeFromEnd` method:

1. Check if head is null, if yes return undefined
2. Check if only single node exists, if yes point head and tail to null
3. Decrease the size of ll

Then simply test them out:

```js
const ll = new LinkedList(1);
ll.addToEnd(2);
ll.addToEnd(3);
ll.removeFromEnd();
console.log(ll);
```

**Note:** For beginners, being able to implement these 2 methods in LinkedList will help them understand the implementation of other methods such as: `addToBeginning`, `removeFromBeginning`, `getAtIndex`, `setAtIndex`, `removeAtIndex`, `reverse`, etc.

I strongly advise doing this kind of pseudo coding before writing the actual coding part.

Now it's your turn to implement the rest of the methods in this manner.
