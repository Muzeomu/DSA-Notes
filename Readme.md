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

### Insertion Sort Algorithm:
* Step 1: Start with the second element in the array (consider the first element as a sorted sub-array of one element).
* Step 2: Compare the current element with the elements in the sorted sub-array (left side) and find its correct position.
* Step 3: Shift all larger elements one position to the right to make space for the current element.
* Step 4: Insert the element into its correct position in the sorted sub-array.
* Step 5: Move to the next element and repeat the process until the entire array is sorted.

### Quick Sort Algorithm:
* Step 1: Choose a pivot element (can be the first, last, or middle element, or chosen randomly).
* Step 2: Partition the array: Rearrange the elements so that all elements smaller than the pivot are on its left and all elements larger than the pivot are on its right.
* Step 3: Recursively apply the partitioning to the sub-arrays on the left and right of the pivot.
* Step 4: Base case: If the sub-array has one or zero elements, it is already sorted.
* Step 5: Continue the recursive process until all sub-arrays are sorted, and the full array is sorted.

###  Merge Sort Algorithm:
* Step 1: Divide the array into two halves until each sub-array contains only a single element (i.e., divide recursively).
* Step 2: Once the sub-arrays contain a single element, start merging them back.
* Step 3: During the merge process, combine the sub-arrays by comparing their elements and sorting them in order.
* Step 4: Continue merging and sorting the sub-arrays until the entire array is sorted.
* Step 5: The array is now fully sorted after all sub-arrays have been merged.



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
