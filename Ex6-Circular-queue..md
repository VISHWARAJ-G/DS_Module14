# Ex6 Dequeue Elements from Circular Queue

## DATE: 10.03.2025
## AIM:
To write a C program to delete three elements from the filled circular queue.

## Algorithm
1. Initialize front and rear to -1.
2. Fill the queue using circular enqueue logic.
3. Check if the queue is empty before deletion.
4. Delete three elements using circular dequeue.
5. Display the queue from front to rear.

## Program:
```
/*
Program to delete three elements from the filled circular queue
Developed by:Vishwaraj G.
RegisterNumber: 212223220125
*/
#include <stdio.h>
#define SIZE 5

int queue[SIZE];
int front = -1, rear = -1;

void enqueue(int value) {
    if ((front == 0 && rear == SIZE - 1) || (rear == (front - 1 + SIZE) % SIZE)) {
        printf("Queue is Full\n");
        return;
    } else if (front == -1) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }
    queue[rear] = value;
}

int dequeue() {
    if (front == -1) {
        printf("Queue is Empty\n");
        return -1;
    }

    int data = queue[front];
    if (front == rear) {
        front = rear = -1;  
    } else {
        front = (front + 1) % SIZE;
    }

    return data;
}

void displayQueue() {
    if (front == -1) {
        printf("Queue is Empty\n");
        return;
    }

    printf("Queue: ");
    int i = front;
    while (1) {
        printf("%d ", queue[i]);
        if (i == rear) break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    enqueue(40);
    enqueue(50);
    printf("Initial ");
    displayQueue();

    printf("\nDeleting 3 elements:\n");
    for (int i = 0; i < 3; i++) {
        int removed = dequeue();
        if (removed != -1) {
            printf("Deleted: %d\n", removed);
        }
    }

    printf("\nAfter Deletion ");
    displayQueue();

    return 0;
}
```


## Output:

![image](https://github.com/user-attachments/assets/8155a124-4ac4-4ca3-9ac1-b57aba7ca2a1)


## Result:
Thus, the C program to delete three elements from the filled circular queue is implemented successfully.
