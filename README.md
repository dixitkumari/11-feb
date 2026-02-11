# 11-feb

#QUESTION 1::
write a C++ program to implement a singly linked list using struct for the node and dyamic memmory allocation with new and delete . Implement the following operations :
insertion of a node at the beginning 
insertion of a node at the end 
deletion of a node 
display the entire list
use new to allocate memory for each node , and delete to free memory when deleting nodes


#CODE



#include <iostream>
using namespace std;

// Define structure for a node
struct Node {
    int data;
    Node* next;
};

// Function to insert at the beginning
void insertAtBeginning(Node*& head, int value) {
    Node* newNode = new Node;     // allocate memory
    newNode->data = value;
    newNode->next = head;
    head = newNode;
}

// Function to insert at the end
void insertAtEnd(Node*& head, int value) {
    Node* newNode = new Node;     // allocate memory
    newNode->data = value;
    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
        return;
    }

    Node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }

    temp->next = newNode;
}

// Function to delete a node by value
void deleteNode(Node*& head, int value) {
    if (head == NULL) {
        cout << "List is empty.\n";
        return;
    }

    Node* temp = head;
    Node* prev = NULL;

    // If head node holds the value
    if (temp != NULL && temp->data == value) {
        head = temp->next;
        delete temp;   // free memory
        cout << "Node deleted.\n";
        return;
    }

    // Search for the node to delete
    while (temp != NULL && temp->data != value) {
        prev = temp;
        temp = temp->next;
    }

    // If value not found
    if (temp == NULL) {
        cout << "Value not found in list.\n";
        return;
    }

    prev->next = temp->next;
    delete temp;   // free memory
    cout << "Node deleted.\n";
}

// Function to display the list
void display(Node* head) {
    if (head == NULL) {
        cout << "List is empty.\n";
        return;
    }

    Node* temp = head;
    while (temp != NULL) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL\n";
}

// Main function
int main() {
    Node* head = NULL;
    int choice, value;

    do {
        cout << "\n--- Singly Linked List Menu ---\n";
        cout << "1. Insert at Beginning\n";
        cout << "2. Insert at End\n";
        cout << "3. Delete a Node\n";
        cout << "4. Display List\n";
        cout << "5. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter value: ";
                cin >> value;
                insertAtBeginning(head, value);
                break;

            case 2:
                cout << "Enter value: ";
                cin >> value;
                insertAtEnd(head, value);
                break;

            case 3:
                cout << "Enter value to delete: ";
                cin >> value;
                deleteNode(head, value);
                break;

            case 4:
                display(head);
                break;

            case 5:
                cout << "Exiting program.\n";
                break;

            default:
                cout << "Invalid choice.\n";
        }

    } while (choice != 5);

    // Free remaining memory before exit
    while (head != NULL) {
        Node* temp = head;
        head = head->next;
        delete temp;
    }

    return 0;
}


<img width="794" height="803" alt="image" src="https://github.com/user-attachments/assets/477dddc7-b488-40ce-b598-bea4ec299094" />

#QUESTION 2:

**Write a C++ program that dynamically allocates memory for an array of integers using new based on the size input by the user. The program should:

Allow the user to enter the size of the array.

Allow the user to enter the values for the array.

Print the array.

Free the dynamically allocated memory using delete[].**
\

#CODE
<img width="1588" height="726" alt="image" src="https://github.com/user-attachments/assets/e2514fdd-7f02-4716-9d09-9ab52dc894a6" />


#QUESTION 3:
Swap Two Numbers Using Pointers
Write a C++ program that swaps two numbers using pointers. The program should:

Declare two integer variables.

Use a pointer to swap their values.

Print the swapped values.
<img width="1417" height="827" alt="image" src="https://github.com/user-attachments/assets/bd3e1c3f-965b-4951-a08b-3bd2715d0ad4" />


#QUESTION 4:Write a C++ program that dynamically allocates memory for an array of strings (an array of pointers). The program should:

Allow the user to input multiple strings.

Print all the strings using the array of pointers.

Free the allocated memory for each string and the array of pointers using delete[].


#CODE
#include <iostream>
using namespace std;

// Function to swap two numbers using pointers
void swapNumbers(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int num1, num2;

    // Input two numbers
    cout << "Enter first number: ";
    cin >> num1;

    cout << "Enter second number: ";
    cin >> num2;

    // Display original values
    cout << "\nBefore swapping:\n";
    cout << "First number = " << num1 << endl;
    cout << "Second number = " << num2 << endl;
#include <iostream>
#include <cstring>
using namespace std;

int main() {
    int n;

    cout << "Enter number of strings: ";
    cin >> n;
    cin.ignore();  // Clear newline from input buffer

    // Dynamically allocate array of pointers
    char** arr = new char*[n];

    // Input strings
    for (int i = 0; i < n; i++) {
        char temp[100];  // Temporary buffer

        cout << "Enter string " << i + 1 << ": ";
        cin.getline(temp, 100);

        // Allocate exact memory for the string
        arr[i] = new char[strlen(temp) + 1];

        // Copy string into dynamically allocated memory
        strcpy(arr[i], temp);
    }

    // Display strings
    cout << "\nEntered strings are:\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << endl;
    }

    // Free memory for each string
    for (int i = 0; i < n; i++) {
        delete[] arr[i];
    }

    // Free memory for array of pointers
    delete[] arr;

    return 0;
}

    // Swap using pointers
    swapNumbers(&num1, &num2);

    // Display swapped values
    cout << "\nAfter swapping:\n";
    cout << "First number = " << num1 << endl;
    cout << "Second number = " << num2 << endl;

    return 0;
}


#OUTPUT
<img width="417" height="354" alt="image" src="https://github.com/user-attachments/assets/619deb3f-4b2c-493f-95c9-2db1a3bc81db" />

#QUESTION 5:
Write a C++ program that implements a circular buffer using a dynamically allocated array. The program should:

Dynamically allocate memory for the buffer.

Allow the user to add and remove elements.

Handle overflow and underflow conditions.

Properly deallocate the memory used by the buffer.


#CODE
#include <iostream>
using namespace std;

class CircularBuffer {
private:
    int *buffer;
    int front;
    int rear;
    int capacity;
    int count;

public:
    // Constructor
    CircularBuffer(int size) {
        capacity = size;
        buffer = new int[capacity];  // Dynamic allocation
        front = 0;
        rear = -1;
        count = 0;
    }

    // Insert element
    void enqueue(int value) {
        if (count == capacity) {
            cout << "Buffer Overflow! Cannot add element.\n";
            return;
        }

        rear = (rear + 1) % capacity;
        buffer[rear] = value;
        count++;
        cout << "Element added.\n";
    }

    // Remove element
    void dequeue() {
        if (count == 0) {
            cout << "Buffer Underflow! Cannot remove element.\n";
            return;
        }

        cout << "Removed element: " << buffer[front] << endl;
        front = (front + 1) % capacity;
        count--;
    }

    // Display buffer
    void display() {
        if (count == 0) {
            cout << "Buffer is empty.\n";
            return;
        }

        cout << "Buffer elements: ";
        for (int i = 0; i < count; i++) {
            cout << buffer[(front + i) % capacity] << " ";
        }
        cout << endl;
    }

    // Destructor to free memory
    ~CircularBuffer() {
        delete[] buffer;  // Proper deallocation
        cout << "Memory deallocated.\n";
    }
};

int main() {
    int size;
    cout << "Enter buffer size: ";
    cin >> size;

    CircularBuffer cb(size);

    int choice, value;

    do {
        cout << "\n--- Circular Buffer Menu ---\n";
        cout << "1. Add Element\n";
        cout << "2. Remove Element\n";
        cout << "3. Display Buffer\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter value: ";
                cin >> value;
                cb.enqueue(value);
                break;

            case 2:
                cb.dequeue();
                break;

            case 3:
                cb.display();
                break;

            case 4:
                cout << "Exiting program.\n";
                break;

            default:
                cout << "Invalid choice.\n";
        }

    } while (choice != 4);

    return 0;
}



#OUTPUT
<img width="327" height="828" alt="image" src="https://github.com/user-attachments/assets/4cf96a49-0031-471b-9cde-7f0aeaaad424" />


#QUESTION 6:
Write a C++ program that demonstrates the use of a pointer to a constant variable. The program should:

Declare a constant variable and a pointer to it.

Show how you can read the value pointed to by the pointer, but not modify it.

#CODE
<img width="1574" height="516" alt="image" src="https://github.com/user-attachments/assets/48e12fb3-10cb-4a5e-b88a-ee841195d3d9" />

#QUESTION7:
Write a C++ program where a function returns a reference to a local variable. What are  potential problems and how to avoid them. Implement a version where the function returns a reference to a static or globally declared variable.

#CODE
**LOCAL VARIABLE**
   <img width="1541" height="611" alt="image" src="https://github.com/user-attachments/assets/cb081a99-e51f-4770-a821-12092306984b" />

**GLOBAL Variable**
<img width="1437" height="603" alt="image" src="https://github.com/user-attachments/assets/e318d9e8-595b-43dd-a4db-babe85d37e39" />
