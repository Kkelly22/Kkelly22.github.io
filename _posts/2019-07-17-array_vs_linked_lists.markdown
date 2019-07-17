---
layout: post
title:      "Array vs Linked Lists"
date:       2019-07-17 18:19:01 +0000
permalink:  array_vs_linked_lists
---


I recently learned of a new data structure I am unfamiliar with - a "linked list".  I have never worked with linked lists before, and wanted to tighten up my understanding of the term.  

Let's start by breaking down what a linked list is.  To quote [GeeksForGeeks](http://www.geeksforgeeks.org/data-structures/linked-list/):
> A LinkedList is a linear data structure which stores element in the non-contiguous location. The elements in a linked list are linked with each other using pointers. Or in other words, LinkedList consists of nodes where each node contains a data field and a reference(link) to the next node in the list.

This varies from an ordered list of elements, such as an array.  In order to access an element of a linked list, you need to access each element that comes before it (or all of the elements that it is linked to).  You could say a linked list relies of *references* or *pointers* to traverse the referential tree.  In order to access an element in an array, you can simply call upon the index of the element you're looking to access.  You could say an array relies on *indexes*.

Turning to an example to help our understanding:

**animals = [Dog, Cat, Bird, Snake, Bunny]**
If I want to access the third element of this array "animals", I simply use animals[2].

**linkedanimals = Head --> [Dog] --> [Cat] --> [Bird] --> [Snake] --> [Bunny]**
If I want to access the third element of this linked list, I need to read through the linked list, starting with "dog" which points to "cat" which points to "bird".  In the code below, notice the "next" keyword.  Each item in a linked list is equipped with a pointer, and the next keyword let's us call on that pointed direction.

```
public void printAllAnimals() {
    Node animal = head;
    while (animal != null) 
    {
        Console.WriteLine(animal.data);
        animal = animal.next;
    }
}
```






