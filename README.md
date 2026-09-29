Q1. Design and implement a stack using an array

A stack is a linear data structure that follows the LIFO (Last In, First Out) principle. This means that the element inserted last is removed first.
Insertion and deletion take place at only one end of the stack, called the TOP.
For example, if the elements 10, 20, and 30 are inserted into a stack in that order, 30 will be removed first, followed by 20 and then 10.

Representation of a stack

Stack (LIFO)
30
20
10
Top - 30
Bottom - 10

Basic operations -

PUSH(x): Inserts element x at the top of the stack.
POP(): Removes and returns the top element.
PEEK(): Returns the top element without removing it.
DISPLAY(): Displays all elements present in the stack.

Stack overflow and underflow -

Stack Overflow occurs when an element is inserted into a full stack.

Stack Underflow occurs when an element is removed from an empty stack.

In an array-based stack, the capacity is fixed. If the array has a capacity of 5, it can store a maximum of 5 elements. Attempting to insert a sixth element causes Stack Overflow.

Algorithms - 

PUSH(x)
Check whether TOP = MAX − 1.
If true, display Stack Overflow.
Otherwise, increment TOP.
Insert x at STACK[TOP].

POP()
Check whether TOP = −1.
If true, display Stack Underflow.
Otherwise, display STACK[TOP].
Decrement TOP.

PEEK()
Check whether TOP = −1.
If true, display that the stack is empty.
Otherwise, display STACK[TOP].

DISPLAY()
Check whether TOP = −1.
If true, display that the stack is empty.
Otherwise, print elements from TOP to 0.

Program for Stack representation using arrays in C -

#include <stdio.h>
#define MAX 5

int stack[MAX];
int top = -1;

void PUSH(int x)
{
    if (top == MAX - 1)
    {
        printf("Stack Overflow!\n");
    }
    else
    {
        top++;
        stack[top] = x;
        printf("%d pushed into stack.\n", x);
    }
}

void POP()
{
    if (top == -1)
    {
        printf("Stack Underflow!\n");
    }
    else
    {
        printf("Popped element: %d\n", stack[top]);
        top--;
    }
}

void PEEK()
{
    if (top == -1)
    {
        printf("Stack is empty.\n");
    }
    else
    {
        printf("Top element: %d\n", stack[top]);
    }
}

void DISPLAY()
{
    int i;

    if (top == -1)
    {
        printf("Stack is empty.\n");
    }
    else
    {
        printf("Stack elements:\n");

        for (i = top; i >= 0; i--)
        {
            printf("%d\n", stack[i]);
        }
    }
}

int main()
{
    int choice, x;

    do
    {
        printf("\n--- STACK MENU ---\n");
        printf("1. PUSH\n");
        printf("2. POP\n");
        printf("3. PEEK\n");
        printf("4. DISPLAY\n");
        printf("5. EXIT\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
            case 1:
                printf("Enter element: ");
                scanf("%d", &x);
                PUSH(x);
                break;

            case 2:
                POP();
                break;

            case 3:
                PEEK();
                break;

            case 4:
                DISPLAY();
                break;

            case 5:
                printf("Exiting program.\n");
                break;

            default:
                printf("Invalid choice!\n");
        }

    } while (choice != 5);

    return 0;
}

Sample Output 1 - Normal Stack Operations 

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 10
10 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 20
20 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 30
30 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 4
Stack elements:
30
20
10

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 3
Top element: 30

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 2
Popped element: 30

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 5
Exiting program.

Sample Output 2 - Stack Underflow

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 2
Stack Underflow!

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 5
Exiting program.

Sample Output 3 - Stack Overflow 

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 10
10 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 20
20 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 30
30 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 40
40 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 50
50 pushed into stack.

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 60
Stack Overflow!

--- STACK MENU ---
1. PUSH
2. POP
3. PEEK
4. DISPLAY
5. EXIT
Enter your choice: 5
Exiting program.

Time and Space Complexity

Let n be the number of elements currently present in the queue.
Operation Time Complexity Auxiliary Space
ENQUEUE O(1)    O(1)
DEQUEUE O(1)    O(1)
FRONT O(1)       O(1)
DISPLAY O(n)     O(1)

The total space complexity of the circular queue is O(MAX), because the array has a fixed capacity of MAX elements.

Additional Task: Fixed stack capacity

When a stack has a fixed size, it can store only a limited number of elements. If the stack is full and the user attempts to insert another element, Stack Overflow occurs.
The program checks whether TOP = MAX − 1 before insertion. If the condition is true, the insertion is rejected and the existing stack remains unchanged.




Q2. Implement a Circular Queue using an array

A queue is a linear data structure that follows the FIFO (First In, First Out) principle. 
This means the element inserted first is removed first.

A circular queue is a type of queue in which the last position is connected back to the first position. 
It allows the reuse of empty positions created after deletion.

A circular queue uses two variables:
• FRONT: Points to the first element of the queue.
• REAR: Points to the last element of the queue.

The circular queue uses the modulo operator (%) to move FRONT and REAR circularly through the array.
For example, if the array size is 5 and REAR reaches index 4, the next position becomes index 0, provided that position is available.

Circular Queue
10   20   30   Empty  Empty
0    1     2    3        4

FRONT → 10 REAR → 30
The next available position after index 4 is index 0

Basic operations
ENQUEUE(x): Inserts an element x at the rear of the queue.
DEQUEUE(): Removes the element from the front of the queue.
FRONT(): Returns the first element without removing it.
DISPLAY(): Displays all elements present in the queue.

Full and Empty Conditions

In this implementation, FRONT and REAR are initialized to −1.
Empty Queue: The queue is empty when: FRONT = -1

Full Queue: The queue is full when: (REAR + 1)%MAX = FRONT

This condition means the next position after REAR is already occupied by FRONT.

Algorithms -

ENQUEUE(x)
1)Check whether the queue is full.
2)If full, display Queue Overflow.
Otherwise, if the queue is empty, set FRONT = 0.
3)Update REAR using (REAR + 1) % MAX.
4)Insert x at QUEUE[REAR].

DEQUEUE()
1)Check whether the queue is empty.
2)If empty, display Queue Underflow.
3)Otherwise, display the element at QUEUE[FRONT].
4)If FRONT = REAR, set both FRONT and REAR to −1.
5)Otherwise, update FRONT using (FRONT + 1) % MAX.

FRONT()
1)Check whether the queue is empty.
2)If empty, display that the queue is empty.
3)Otherwise, display QUEUE[FRONT].

DISPLAY()
1)Check whether the queue is empty.
2)If empty, display that the queue is empty.
3)Otherwise, start from FRONT.
4)Print each element until REAR is reached.
5)Move to the next position using (i + 1) % MAX.

PROGRAM - 

#include <stdio.h>
#define MAX 5

int queue[MAX];
int front = -1;
int rear = -1;

int isFull()
{
    return (rear + 1) % MAX == front;
}

int isEmpty()
{
    return front == -1;
}

void ENQUEUE(int x)
{
    if (isFull())
    {
        printf("Queue Overflow!\n");
    }
    else
    {
        if (isEmpty())
        {
            front = 0;
        }

        rear = (rear + 1) % MAX;
        queue[rear] = x;

        printf("%d inserted into queue.\n", x);
    }
}

void DEQUEUE()
{
    if (isEmpty())
    {
        printf("Queue Underflow!\n");
    }
    else
    {
        printf("Deleted element: %d\n", queue[front]);

        if (front == rear)
        {
            front = rear = -1;
        }
        else
        {
            front = (front + 1) % MAX;
        }
    }
}

void FRONT()
{
    if (isEmpty())
    {
        printf("Queue is empty.\n");
    }
    else
    {
        printf("Front element: %d\n", queue[front]);
    }
}

void DISPLAY()
{
    int i;

    if (isEmpty())
    {
        printf("Queue is empty.\n");
    }
    else
    {
        printf("Queue elements: ");

        i = front;

        while (1)
        {
            printf("%d ", queue[i]);

            if (i == rear)
            {
                break;
            }

            i = (i + 1) % MAX;
        }

        printf("\n");
    }
}

int main()
{
    int choice, x;

    do
    {
        printf("\n--- CIRCULAR QUEUE MENU ---\n");
        printf("1. ENQUEUE\n");
        printf("2. DEQUEUE\n");
        printf("3. FRONT\n");
        printf("4. DISPLAY\n");
        printf("5. EXIT\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
            case 1:
                printf("Enter element: ");
                scanf("%d", &x);
                ENQUEUE(x);
                break;

            case 2:
                DEQUEUE();
                break;

            case 3:
                FRONT();
                break;

            case 4:
                DISPLAY();
                break;

            case 5:
                printf("Exiting program.\n");
                break;

            default:
                printf("Invalid choice!\n");
        }

    } while (choice != 5);

    return 0;
}

SAMPLE OUTPUT - 

--- CIRCULAR QUEUE MENU ---
1. ENQUEUE
2. DEQUEUE
3. FRONT
4. DISPLAY
5. EXIT
Enter your choice: 1
Enter element: 10
10 inserted into queue.

Enter your choice: 1
Enter element: 20
20 inserted into queue.

Enter your choice: 1
Enter element: 30
30 inserted into queue.

Enter your choice: 4
Queue elements: 10 20 30

Enter your choice: 3
Front element: 10

Enter your choice: 2
Deleted element: 10

Enter your choice: 4
Queue elements: 20 30

OUTPUR FOR CIRCULAR QUEUE OVERFLOW - 
Enter your choice: 1
Enter element: 10
10 inserted into queue.

Enter your choice: 1
Enter element: 20
20 inserted into queue.

Enter Q1. Design and implement a stack using an array

A stack is a linear data structure that follows the LIFO (Last In, First Out) principle. This means that the element inserted last is removed first.
Insertion and deletion take place at only one end of the stack, called the TOP.
For example, if the elements 10, 20, and 30 are inserted into a stack in that order, 30 will be removed first, followed by 20 and then 10.

Representation of a stack

Stack (LIFO)
30
20
10
Top - 30
Bottom - 10

Basic operations -

PUSH(x): Inserts element x at the top of the stack.
POP(): Removes and returns the top element.
PEEK(): Returns the top element without removing it.
DISPLAY(): Displays all elements present in the stack.

Stack overflow and underflow -

Stack Overflow occurs when an element is inserted into a full stack.

Stack Underflow occurs when an element is removed from an empty stack.

In an array-based stack, the capacity is fixed. If the array has a capacity of 5, it can store a maximum of 5 elements. Attempting to insert a sixth element causes Stack Overflow.

Algorithms - 

PUSH(x)
Check whether TOP = MAX − 1.
If true, display Stack Overflow.
Otherwise, increment TOP.
Insert x at STACK[TOP].

POP()
Check whether TOP = −1.
If true, display Stack Underflow.
Otherwise, display STACK[TOP].
Decrement TOP.

PEEK()
Check whether TOP = −1.
If true, display that the stack is empty.
Otherwise, display STACK[TOP].

DISPLAY()
Check whether TOP = −1.
If true, display that the stack is empty.
Otherwise, print elements from TOP to 0.

Program for Stack representation using arrays in C -
