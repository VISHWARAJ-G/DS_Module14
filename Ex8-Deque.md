#  EXERCISE 8: Deque

##  DATE: 11-03-2025

##  AIM:
To write a C function to **count the number of elements** present in the **deque**.

---

##  Algorithm:
1. Start the program.
2. Define the deque with a fixed size array, `front`, and `rear` pointers.
3. Initialize the deque as empty (`front = -1`, `rear = -1`).
4. Implement `insertFront` and `insertRear` functions to add elements.
5. Create a function `countDeque`:
   - If deque is empty, count is 0.
   - If `rear >= front`, count = `rear - front + 1`.
   - Else, count = `(SIZE - front) + (rear + 1)`.
6. Display the number of elements.
7. End the program.

---

## Program:
```c
/*
Program to count the number of elements present in the deque
Developed by: Vishwaraj G
RegisterNumber: 212223220125
*/

#include <stdio.h>
#define SIZE 5

int deque[SIZE];
int front = -1, rear = -1;

// Insert at rear
void insertRear(int value) {
    if ((front == 0 && rear == SIZE - 1) || (rear == (front - 1 + SIZE) % SIZE)) {
        printf("Deque is full!\n");
        return;
    }
    if (front == -1) { // Empty deque
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }
    deque[rear] = value;
    printf("Inserted at rear: %d\n", value);
}

// Insert at front
void insertFront(int value) {
    if ((front == 0 && rear == SIZE - 1) || (rear == (front - 1 + SIZE) % SIZE)) {
        printf("Deque is full!\n");
        return;
    }
    if (front == -1) { // Empty deque
        front = rear = 0;
    } else if (front == 0) {
        front = SIZE - 1;
    } else {
        front--;
    }
    deque[front] = value;
    printf("Inserted at front: %d\n", value);
}

// Function to count elements
int countDeque() {
    if (front == -1)
        return 0;
    if (rear >= front)
        return (rear - front + 1);
    else
        return (SIZE - front) + (rear + 1);
}

// Display function
void displayDeque() {
    if (front == -1) {
        printf("Deque is empty\n");
        return;
    }
    printf("Deque elements: ");
    int i = front;
    while (1) {
        printf("%d ", deque[i]);
        if (i == rear)
            break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    insertRear(10);
    insertRear(20);
    insertFront(5);
    insertRear(30);

    printf("\nCurrent Deque:\n");
    displayDeque();

    printf("\nNumber of elements in deque: %d\n", countDeque());

    return 0;
}
```

## Output:

![image](https://github.com/user-attachments/assets/eb136ec8-fa83-4200-9fd8-ca21918bb87b)

## Result:
Thus, the C code to count the number of elements present in the deque is implemented successfully.
