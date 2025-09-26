---
## Double-Linked-List Using C++
### You have all Control in Your List ==> Insert-Update-Delete-Display Just Run The Program
---
``` C++
#include <iostream>
using namespace std;

struct node
{
    int data;
    node* next;
    node* previous;
};

node* head = NULL;

void InsertNode(int value)
{
    node* new_node = new node;
    new_node->data = value;
    new_node->next = NULL;
    new_node->previous = NULL;
    if (head == NULL)
    {
        head = new_node;
    }
    else 
    {
        node* last = head;
        while (last->next != NULL) 
        {
            last = last->next;
        }
        last->next = new_node;
        new_node->previous = last;
    }
    cout << value << " is Added into Linked-List\n";
}

void Display_Linked_List()
{
    if (head == NULL) 
    {
        cout << "Linked List is Empty\n";
        return;
    }
    node* current = head;
    while (current != NULL)
    {
        cout << current->data << "  ";
        current = current->next;
    }
    cout << endl;
}

void Insert_At_Front(int value)
{
    node* new_node = new node;
    new_node->data = value;
    new_node->next = head;
    new_node->previous = NULL;
    if (head != NULL)
        head->previous = new_node;
    head = new_node;
    cout << value << " is Added in front of Linked-List\n";
}

void Insert_At_Between(int value, int aftervalue)
{
    node* current = head;
    while (current != NULL && current->data != aftervalue)
        current = current->next;

    if (current == NULL) 
    {
        cout << "Node with value " << aftervalue << " not found.\n";
        return;
    }

    node* new_node = new node;
    new_node->data = value;
    new_node->next = current->next;
    new_node->previous = current;
    if (current->next != NULL)
        current->next->previous = new_node;
    current->next = new_node;
    cout << value << " is Added After " << aftervalue << " in Linked-List\n";
}

void Delete_Node(int value)
{
    if (head == NULL) 
    {
        cout << "Linked List is Empty\n";
        return;
    }

    node* current = head;

    if (current->data == value) 
    {
        head = current->next;
        if (head != NULL)
            head->previous = NULL;
        delete current;
        cout << value << " is deleted from the linked list\n";
        return;
    }

    while (current != NULL && current->data != value)
        current = current->next;

    if (current == NULL) 
    {
        cout << "Node with value " << value << " not found.\n";
        return;
    }

    if (current->next != NULL)
        current->next->previous = current->previous;
    if (current->previous != NULL)
        current->previous->next = current->next;
    delete current;
    cout << value << " is deleted from the linked list\n";
}

int main()
{
    int choise, value;
    cout << "\t(Welcome To My Program)\n";
    cout << "       -------------------------\n";
    cout << "1) INsert To Linked-List\n" << "2) INsert At Front For Linked-List\n" << "3) INsert At Between For Linked-List\n"
        << "4) DElete Element From Linked-List\n" << "5) Display Linked-List\n" << "6) EXit\n";
    cout << "=========================\n";
    do
    {
        cout << "Enter Your Choise\n";
        cin >> choise;
        cout << "=========================\n";
        switch (choise)
        {
        case 1:
            cout << "Enter Element To Add it in Linked-List\n";
            cin >> value;
            InsertNode(value);
            cout << "=========================\n";
            break;
        case 2:
            cout << "Enter Element To Add it in Front of Linked-List\n";
            cin >> value;
            Insert_At_Front(value);
            cout << "=========================\n";
            break;
        case 3:
            int aftervalue;
            cout << "Enter Element To Add it in Between\n";
            cin >> value;
            cout << "Choise Element Of Your Linked-List To Add Your Element After This\n";
            cin >> aftervalue;
            Insert_At_Between(value, aftervalue);
            cout << "=========================\n";
            break;
        case 4:
            cout << "Enter Element To Delete it From Linked-List\n";
            cin >> value;
            Delete_Node(value);
            cout << "=========================\n";
            break;
        case 5:
            cout << "Your Linked-List is\n";
            Display_Linked_List();
            cout << "=========================\n";
            break;
        case 6:
            cout << "EXiting...\n";
            break;
        default:
            cout << "Invalid Choise..!! Please Try again\n";
            cout << "=========================\n";
            break;
        }
    } while (choise != 6);
    return 0;
}```
