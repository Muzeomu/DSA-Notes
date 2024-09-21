# DSA Notes

## Stacks 

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
