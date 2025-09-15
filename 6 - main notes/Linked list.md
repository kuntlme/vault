## Index: [[codehelp DSA]]

#dsa #coding #placement

## singly LL insertion & deletion and traversion

```
#include <iostream>

using namespace std;



class Node

{

public:

int data;

Node *next;



Node(int data)

{

this->data = data;

this->next = NULL;

}

~Node()

{

int value = this->data;

if(this->next != NULL){

delete next;

this->next = NULL;

}

cout << "deleting the value " << value << endl;

}

};



void insertAtHead(Node *&head, int data)

{

Node *temp = new Node(data);

temp->next = head;

head = temp;

}



void insertAtTail(Node *&tail, int data)

{

Node *curr = new Node(data);

Node *temp = tail;

temp->next = curr;

tail = curr;

}



void insertAtPosition(Node *&head, Node *&tail, int position, int data)

{

cout << "inserting at " << position << " with " << data << endl;

if (position == 1)

{

insertAtHead(head, data);

return;

}

int count = 1;

Node *temp = head;

while (count < position - 1)

{

temp = temp->next;

count++;

}

if (temp->next == NULL)

{

insertAtTail(tail, data);

return;

}

Node *curr = new Node(data);

curr->next = temp->next;

temp->next = curr;

}



void deleteAtHead(Node* &head){

Node* temp = head;

head = head->next;

temp->next = NULL;

delete temp;

}

void deleteAtTail(Node* &tail, Node* prev){

Node* curr = tail;

prev->next = curr->next;

tail = prev;

delete curr;

}



void deleteAtPosition(Node *&head, Node *&tail, int position){

if(position == 1){

deleteAtHead(head);

return;

}

int count = 1;

Node* prev = NULL;

Node* curr = head;

while (count < position)

{

prev = curr;

curr = curr->next;

count++;

}

if(curr->next == NULL){

deleteAtTail(tail, prev);

return;

}

prev->next = curr->next;

curr->next = NULL;

delete curr;

}



void printLL(Node *&head)

{

Node *temp = head;



while (temp != NULL)

{

cout << temp->data << " ";

temp = temp->next;

}

cout << endl;

}



int main()

{



Node *node1 = new Node(10);

Node *head;

Node *tail;



head = node1;

tail = node1;

insertAtPosition(head, tail, 1, 22);

insertAtPosition(head, tail, 3, 40);

insertAtPosition(head, tail, 2, 12);

insertAtPosition(head, tail, 2, 65);

insertAtPosition(head, tail, 2, 87);

insertAtPosition(head, tail, 2, 43);



printLL(head);

cout << "head is " << head->data << endl;

cout << "tail is " << tail->data << endl;

deleteAtPosition(head, tail, 3);

printLL(head);

cout << "head is " << head->data << endl;

cout << "tail is " << tail->data << endl;



return 0;

}
```

### [138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

```c++
/*

// Definition for a Node.

class Node {

public:

int val;

Node* next;

Node* random;

Node(int _val) {

val = _val;

next = NULL;

random = NULL;

}

};

*/



class Solution {

public:

void insertAtClone(Node* &head, Node* &tail, int value){

Node* temp = new Node(value);

if(head == NULL){

head = temp;

tail = temp;

}

else{

tail -> next = temp;

tail = temp;

}

}

Node* copyRandomList(Node* head) {

//create a clone

Node* cloneHead;

Node* cloneTail;



//copy to that clone

Node* temp = head;

while(temp != NULL){

insertAtClone(cloneHead, cloneTail, temp -> val);

temp = temp -> next;

}

//create a map

Node* originalNode = head;

Node* cloneNode = cloneHead;

unordered_map<Node* , Node*>oldToNew;

while(originalNode != NULL && cloneNode != NULL){

oldToNew[originalNode] = cloneNode;

originalNode = originalNode -> next;

cloneNode = cloneNode -> next;



}

//map the random pointer

cloneNode = cloneHead;

originalNode = head;

while(cloneNode != NULL){

cloneNode -> random = oldToNew[originalNode -> random];

cloneNode = cloneNode -> next;

originalNode = originalNode -> next;

}

//return clone

return cloneHead;

}

};
```

```
/*

// Definition for a Node.

class Node {

public:

int val;

Node* next;

Node* random;

Node(int _val) {

val = _val;

next = NULL;

random = NULL;

}

};

*/



class Solution {

public:

void insertAtClone(Node* &head, Node* &tail, int value){

Node* temp = new Node(value);

if(head == NULL){

head = temp;

tail = temp;

}

else{

tail -> next = temp;

tail = temp;

}

}

Node* copyRandomList(Node* head) {

//create a clone

Node* cloneHead;

Node* cloneTail;



//copy to that clone

Node* temp = head;

while(temp != NULL){

insertAtClone(cloneHead, cloneTail, temp -> val);

temp = temp -> next;

}


//marge original to the copy



Node* originalNode = head;

Node* cloneNode = cloneHead;

while(originalNode != NULL && cloneNode != NULL){

Node* next = originalNode -> next;

originalNode -> next = cloneNode;

originalNode = next;

next = cloneNode -> next;

cloneNode -> next = originalNode;

cloneNode = next;

}

//set random pointer

temp = head;

while(temp != NULL){

if(temp -> next != NULL){

if(temp -> random != NULL){

temp -> next -> random = temp -> random -> next;

}

else{

temp -> next -> random = NULL;

}

}



temp = temp -> next -> next;



}



// detatch original and clone

originalNode = head;

cloneNode = cloneHead;

while(originalNode != NULL && cloneNode != NULL){

Node* next = originalNode -> next;

originalNode -> next = cloneNode -> next;

originalNode = originalNode -> next;



next = cloneNode -> next;

if(originalNode != NULL)

cloneNode -> next = originalNode -> next;

cloneNode = cloneNode -> next;



}



//return clone

return cloneHead;

}

};
```

## mergesort

```
/**

* Definition for singly-linked list.

* struct ListNode {

* int val;

* ListNode *next;

* ListNode() : val(0), next(nullptr) {}

* ListNode(int x) : val(x), next(nullptr) {}

* ListNode(int x, ListNode *next) : val(x), next(next) {}

* };

*/

class Solution {

public:

ListNode* merge(ListNode* left, ListNode* right){

if(left == NULL){

return right;

}

if(right == NULL){

return left;

}



ListNode* ans = new ListNode(-1);

ListNode* temp = ans;



while(left != NULL && right != NULL){

if(left -> val < right -> val){

temp -> next = left;

temp = left;

left = left -> next;

}

else{

temp -> next = right;

temp = right;

right = right -> next;

}

}



while(left != NULL){

temp -> next = left;

temp = left;

left = left -> next;

}

while(right != NULL){

temp -> next = right;

temp = right;

right = right -> next;

}



return ans -> next;

}



ListNode* findMid(ListNode* head) {

ListNode* slow = head;

ListNode* fast = head -> next;

while(fast != NULL && fast -> next != NULL){

slow = slow -> next;

fast = fast -> next -> next;



}

return slow;

}



ListNode* sortList(ListNode* head) {

if(head == NULL || head -> next == NULL ){

return head;

}



// break two part of LL

ListNode* mid = findMid(head);





ListNode* left = head;

ListNode* right = mid -> next;

mid -> next = NULL;



// recursive calls to sord both halves

left = sortList(left);

right = sortList(right);



//merge

ListNode* result = merge(left, right);



return result;




}

};
```
