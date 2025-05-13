# Ex7 Priority Queue
## DATE: 11.03.2025
## AIM:
To formulate the C code to display the elements of the priority queue after insertion and deletion operation.

## Algorithm
1. Initialize an empty priority queue with size = 0.
2. Insert a new element in sorted order (descending), shifting elements if needed.
3. Delete the highest priority element (first element) and shift the rest left.
4. Display all elements from index 0 to size - 1.
5. Repeat the operations based on user choice until exit is selected.

## Program:
```
/*
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/
#include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int items[MAX];
    int size;
} PriorityQueue;

void insert(PriorityQueue *pq, int value) {
    if (pq->size == MAX) {
        printf("Priority Queue is full!\n");
        return;
    }
    int i = pq->size - 1;
    while (i >= 0 && pq->items[i] < value) {
        pq->items[i + 1] = pq->items[i];
        i--;
    }
    pq->items[i + 1] = value;
    pq->size++;
}

void delete(PriorityQueue *pq) {
    if (pq->size == 0) {
        printf("Priority Queue is empty!\n");
        return;
    }
    printf("Deleted element: %d\n", pq->items[0]);
    for (int i = 1; i < pq->size; i++) {
        pq->items[i - 1] = pq->items[i];
    }
    pq->size--;
}

void display(PriorityQueue *pq) {
    if (pq->size == 0) {
        printf("Priority Queue is empty!\n");
        return;
    }
    printf("Priority Queue elements: ");
    for (int i = 0; i < pq->size; i++) {
        printf("%d ", pq->items[i]);
    }
    printf("\n");
}

int main() {
    PriorityQueue pq;
    pq.size = 0;
    int choice, value;

    while (1) {
        printf("\n1. Insert\n2. Delete\n3. Display\n4. Exit\nEnter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value to insert: ");
                scanf("%d", &value);
                insert(&pq, value);
                display(&pq);
                break;
            case 2:
                delete(&pq);
                display(&pq);
                break;
            case 3:
                display(&pq);
                break;
            case 4:
                exit(0);
            default:
                printf("Invalid choice! Try again.\n");
        }
    }
    return 0;
}
```
## Output:
![Screenshot 2025-04-29 112025](https://github.com/user-attachments/assets/fa2d9cc6-910b-44ab-92a3-cf1086d7c715)

## Result:
Thus, the C program to display the elements of the priority queue after insertion and deletion operation is implemented successfully
