# DSA Notes

## Unit -1 Introduction

### ADT - Abstract data type 
Data type which are used to solve real life problems where user is only aware about the options or operations available to use and unaware about how those operations are taking place.

### Asymptotic Notations

* Asymptotic Notations are mathematical representation used to describe the time complexity (or space complexity) of an algorithm

* Types of Asymptotic Notations
1. Big O Notation (O): Describes the worst-case time complexity.
2. Big Omega Notation (Ω): Describes the best-case time complexity.
3. Theta Notation (Θ): Describes the average-case or tight bound time complexity.

### Types of Data Structures

* Primitive DS - int, float, char, pointer

1. Linear Data Structures:
    * Arrays
    * Linked Lists 
    * Stacks
    * Queues 

2. Non-Linear Data Structures:
    * Trees
    * Graphs 

### Sorting Algorithms

1. Insertion Sort
    * Best -  O(n)
    * Average - O(n^2)
    * Worst - O(n^2)
2. Quick sort
    * Best -  O(nlogn)
    * Average - O(nlogn)
    * Worst - O(n^2)
3. Merge sort
    * Best -  O(nlogn)
    * Average - O(nlogn)
    * Worst - O(nlogn)

### Static Memory Allocation
* Memory is allocated at compile time and cannot be changed during runtime.
* The size of memory is fixed once the program starts.
* The memory is allocated on the stack.

### Dynamic Memory Allocation
* Memory is allocated at runtime using dynamic memory functions.
* The size of memory can be changed during execution.
* The memory is allocated on the heap.
* More flexible as you can allocate memory as needed, but it's less efficient than static allocation due to manual management.

### Functions
* malloc() -  allocates a block of memory of a given size at runtime, but the memory is uninitialized, meaning it contains garbage values. 
* calloc() - also allocates memory but initializes all elements to zero, making it ideal for arrays. 
* realloc() - is used to resize a previously allocated memory block, either expanding or shrinking the memory while preserving the existing data. 
* free() - releases the memory previously allocated with malloc(), calloc(), or realloc() to avoid memory leaks.


## Unit -3 Stacks 

1. In the array implementation of a stack, a fixed-size array is used to hold the stack elements. The stack follows the LIFO (Last In, First Out) principle, meaning that the last element added to the stack is the first one to be removed.

2. Components of Array-Based Stack:
* Array: The stack is represented using an array of a fixed size. This array will store the stack elements.
* Top Pointer: A variable, often called top, is used to keep track of the index of the top element in the stack.
Initially, the top is set to -1, indicating the stack is empty.

### Overflow and Underflow
* Stack overflow:
The condition resulting from trying to push an element onto a full stack.
* Stack underflow:
The condition resulting from trying to pop an empty stack.


## Algorithm to Push()
* Step 1 − Checks if the stack is full.
* Step 2 − If the stack is full, produces an error and exit.
* Step 3 − If the stack is not full, increments top to point next empty space.
* Step 4 − Adds data element to the stack location, where top is pointing.
* Step 5 − Returns success.

## Algorithm to Pop()
* Step 1 − Checks if the stack is empty.
* Step 2 − If the stack is empty, produces an error and exit.
* Step 3 − If the stack is not empty, accesses the data element at which top is
pointing.
* Step 4 − Decreases the value of top by 1.
* Step 5 − Returns success.

```c
#include <stdio.h>
#include <ctype.h>

#define MAX 5

int stack[MAX];
int top = -1;

int isfull() {
    if(top == MAX-1)
        return 1;
    else
        return 0;
}

int isempty() {
    if(top == -1)
        return 1;
    else
        return 0;
}

void push(int data) {
    if(!isfull()) {
        top = top + 1;
        stack[top] = data;
    }
    else {
        printf("Could not insert data, Stack is full.\n");
    }
}

int pop() {
    int data;
    if(!isempty()) {
        data = stack[top];
        top = top - 1;
        return data;
    }
    else {
        printf("Could not retrieve data, Stack is empty.\n");
    }
}

int main(){
    push(3);
    push(5);
    push(9);
    push(1);
    pop();
    push(12);

    while(!isempty()) {
        int data = pop();
        printf("%d\n",data);
    }

    return 0;
}
```
## Algorithm for infix to postfix

1. Initialize an empty stack for operators and an empty string for the postfix expression.
2. Scan the infix expression from left to right:
* If the scanned character is an operand, append it to the postfix expression.
* If the scanned character is '('(left parenthesis), push it to the stack.
* If the scanned character is ')'(right parenthesis), pop and append operators from the stack to the postfix expression until a '(' is encountered. Remove the '(' from the stack.
3. If the scanned character is an operator:
* While there is an operator at the top of the stack with greater or equal precedence, pop it and append to the postfix expression.
* Push the current operator to the stack.
4. After scanning the expression, pop all the operators from the stack and append them to the postfix expression.
5. End.
