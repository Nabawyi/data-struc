#include <iostream>
using namespace std;
//================================================================================
struct node
{
	int data;
	node* next;
};
node* front = NULL;
node* rear = NULL;
//================================================================================
void enqueue(int value);
void dequeue();
int peek();
void display();
//================================================================================
int main()
{
	enqueue(1);
	enqueue(2);
	enqueue(3);
	enqueue(4);
	enqueue(5);
	display();
	dequeue();
	display();
	cout << "peek = " << peek();
}
//================================================================================
void enqueue(int value)
{
	node* newnode = new node;
	newnode->data = value;
	newnode->next = NULL;
	if (front == NULL)
	{
		front = rear = newnode;
	}
	else 
	{
		rear->next = newnode;
		rear = newnode;
	}
}
//================================================================================
void dequeue()
{
	if (rear == NULL)
	{
		cout << "queue is empty";
	}
	else if (front == rear)
	{
		node* ptr = front;
		rear = front = NULL;
		delete(ptr);
	}
	else
	{
		node* ptr = front;
        front = front->next;
		delete(ptr);
	}
}
//================================================================================
int peek()
{
	if (front == NULL)
	{
		cout << " queue is empty " << endl;
	}
	return front->data;
}
//================================================================================
void display()
{
	if (front == NULL)
	{
		cout << "qeueu is empty"<<endl;
	}
	else
	{
		node* cur = front;

		while (cur != NULL)
		{
			cout << cur->data << "\n"<<endl;
			cur = cur->next;
		}
	}
}
//================================================================================
