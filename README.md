#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

int main() {
    struct node *head = NULL, *newnode, *temp;
    int choice = 1;

    while (choice) {
        newnode = (struct node*) malloc(sizeof(struct node));

        if (newnode == NULL) {
            printf("Memory allocation failed!\n");
            return 1;
        }

        printf("Enter data: ");
        scanf("%d", &newnode->data);

        newnode->next = NULL;

        if (head == NULL) {
            head = newnode;
        } else {
            temp = head;
            while (temp->next != NULL) {
                temp = temp->next;
            }
            temp->next = newnode;
        }

        printf("Do you want to continue? (1/0): ");
        scanf("%d", &choice);
    }

    // Display the linked list
    temp = head;
    printf("\nLinked List: ");
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");

    return 0;



Good 👏 let’s go through the corrected program line by line so you fully understand what’s happening.


---

#include <stdio.h>

👉 Includes standard input/output functions like printf() and scanf().

#include <stdlib.h>

👉 Needed for malloc() (dynamic memory allocation).


---

1️⃣ Structure Definition

struct node {
    int data;
    struct node *next;
};

struct node → defines a new data type (a node).

int data; → stores the value.

struct node *next; → pointer to the next node in the list.


This is what makes it a linked list — each node points to the next node.


---

2️⃣ Main Function

int main() {

Program execution starts here.


---

3️⃣ Variable Declarations

struct node *head = NULL, *newnode, *temp;

head → points to the first node of the list.

newnode → used to create a new node.

temp → used for traversal.

head = NULL → initially list is empty.



---

int choice = 1;

Controls the loop. If choice = 1, loop continues. If choice = 0, loop stops.


---

4️⃣ While Loop (Creating Nodes)

while (choice) {

Loop runs as long as user wants to add nodes.


---

5️⃣ Allocate Memory

newnode = (struct node*) malloc(sizeof(struct node));

malloc() → allocates memory in heap.

sizeof(struct node) → allocates correct size.

Typecast to (struct node*) → converts void pointer to node pointer.


Now memory space for one node is created.


---

if (newnode == NULL) {
    printf("Memory allocation failed!\n");
    return 1;
}

Checks if memory allocation failed. If yes → exit program.


---

6️⃣ Input Data

printf("Enter data: ");
scanf("%d", &newnode->data);

newnode->data → access data part of the node.

-> is used because newnode is a pointer.



---

7️⃣ Set Next Pointer

newnode->next = NULL;

Since this is the last node (for now), its next is NULL.


---

8️⃣ Insert Into Linked List

if (head == NULL) {
    head = newnode;
}

If list is empty:

Make head point to newnode.

This becomes the first node.



---

else {
    temp = head;

If list is not empty:

Start traversal from head.



---

while (temp->next != NULL) {
    temp = temp->next;
}

Traverse until the last node. Condition: temp->next != NULL Meaning: keep moving until next is NULL.


---

temp->next = newnode;

Attach the new node at the end.


---

9️⃣ Ask User to Continue

printf("Do you want to continue? (1/0): ");
scanf("%d", &choice);

If user enters:

1 → continue

0 → stop loop



---

🔟 Display the Linked List

temp = head;
printf("\nLinked List: ");

Start printing from head.


---

while (temp != NULL) {
    printf("%d -> ", temp->data);
    temp = temp->next;
}

Traverse and print each node.


---

printf("NULL\n");

Shows end of list.


---

return 0;
}

Program ends successfully.


---

🧠 Important Concepts You Should Notice

1. Dynamic Memory Allocation → malloc()


2. Pointer to structure → struct node *next


3. Arrow operator (->) → used for pointers


4. Traversal → moving from one node to another


5. Head pointer → always stores first node




