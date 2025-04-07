```py
/* 8th linear search and binary search */
#include<stdio.h>
void lsearch();
void bsearch();
void main()
{int op;
do{
printf("1.Linear search \n");
printf("2.Binary seach \n");
printf("3.Exit \n \n");
printf("enter option \n");
scanf("%d",&op);
switch(op)
{case 1:
lsearch();
break;
case 2:
bsearch();
break;
}} while(op != 3);
}
void lsearch()
{
int a[20],n,i,key,f = 0;
printf("enter size of an array \n");
scanf("%d",&n);
printf("enter array elements \n");
for(i = 0; i < n; i++)
{ scanf("%d",&a[i]);
}printf("enter the key to be searched \n");
scanf("%d",&key);
for(i = 0; i < n; i++)
{  if(a[i] == key)
{ f = 1;
break;} }
if(f == 1)
{ printf("key found \n");
}else {
printf("key not found \n");
} }
void bsearch()
{ int a[20],n,i,key,low,high,mid,f = 0;
printf("enter size of an array \n");
scanf("%d",&n);
printf("enter array elements in ascending order \n");
for(i = 0; i < n; i++)
{scanf("%d",&a[i]);
}
printf("enter the key to be searched \n");
scanf("%d",&key);
low = 0;
high = n - 1;
while(low <= high)
{
mid = (low + high) / 2;
if(a[mid] == key)
{ f = 1;
break;}
else if(key < a[mid])
{ high = mid - 1;
} else {
low = mid + 1;
} }
if(f == 1)
{ printf("key found \n");
}else{
printf("key not found \n");
}}
```
# STACK
```py
#include <stdio.h>
#define MAX 5
int stack[MAX];
int top = -1; 
void push(int value) {
if (top == MAX - 1) {
printf("Stack Overflow! Cannot push %d\n", value);
} else {
top++;
stack[top] = value; 
printf("%d pushed to stack\n", value);
}   }
int pop() {
if (top == -1) {
printf("Stack Underflow! Cannot pop\n");
return -1;
} else {
int value = stack[top]; 
top--; 
return value;
} }
void display() {
if (top == -1) {
printf("Stack is empty\n");
} else {
printf("Stack elements: ");
for (int i = top; i >= 0; i--) { //loop from top to bottom
printf("%d ", stack[i]);
}  printf("\n"); //print a new line
}   }
int main() {
int choice, value;
while (1) {
printf("\n--- Stack Operations ---\n");
printf("1. Push\n2. Pop\n3. Display\n4. Exit\n");
printf("Enter your choice: ");
scanf("%d", &choice);

switch (choice) {
case 1:
printf("Enter value to push: ");
scanf("%d", &value);
push(value); 
break;
case 2:
value = pop(); 
if (value != -1) {
printf("%d popped from the stack\n", value);
}   break;
case 3:
display();
break;
case 4:
printf("Exiting...\n");
return 0; // Exit the program
default:
printf("Invalid choice, please try again\n");
}   }
}
```
# lab-2 t infix 
```py
 #include<stdio.h>
#include<string.h>
#include<ctype.h>
#include<conio.h>
void main() {
char infix[50],postfix[50],s[50],ch;
int top = -1,len,i,j = 0;   
clrscr();
printf("enter infix expression \n");
scanf("%s",infix);
len = strlen(infix);
s[++top] = '#';
for(i = 0; i < len; i++) {
ch = infix[i];
if(isalpha(ch) || isdigit(ch))
{  postfix[j++] = ch; }
else if(ch == '^') {
while(s[top] == '^') {
postfix[j++] = s[top--]; }
s[++top] = ch;}
else if(ch == '*'|| ch == '/'){
while(s[top] == '^'|| s[top] == '*'|| s[top] == '/')
{ postfix[j++] = s[top--];
} s[++top] = ch; }
else if(ch == '+' || ch == '-')
{ while(s[top] == '^'|| s[top] == '*'|| s[top] == '/' || s[top] == '+' || s[top] == '-')
{ postfix[j++] = s[top--]; }
s[++top] = ch; }
else if(ch == '(') {
s[++top] = '('; }
else if(ch == ')') {
while(s[top] != '(')
{ postfix[j++] = s[top--];
} top = top - 1; }
} while(s[top] != '#')
{  postfix[j++] = s[top--];
} postfix[j] = '\0';
printf("postfix expression = %s",postfix);
getch(); }
```
## 3rd circulr
```py
/* Part-B 3 Develop a program to simulate the working
   of circular queue providing the following operations
   Insert,Delete and Display */

#include<stdio.h>
#include<conio.h>
#define SIZE 4
void cqinsert(int);
void cqdelete();
void cqdisplay();
int cq[SIZE],front = - 1,rear = -1;
void main()
{
 int item,op;
 clrscr();
  do
  {
printf("1.Insert \n");
 printf("2.Delete \n");
 printf("3.Display \n");
 printf("4.Exit \n \n");
 printf("enter option \n");
 scanf("%d",&op);
  switch(op)
{   case 1:
 printf("enter item to be inserted \n");
scanf("%d",&item);
 cqinsert(item);
break;
 case 2:
cqdelete();
break;
case 3:	  cqdisplay();
break;
}
 } while(op != 4)  }
void cqinsert(int item)
  {
if(((front == 0) && (rear == SIZE - 1)) || (front == rear + 1))
{
printf("circular queue is full \n");
return;
}
if(front == -1) {
front = 0;
rear = 0;
 }else if(rear == SIZE - 1)
{
rear = 0;
 }  else {
 rear = rear + 1;
 }   cq[rear] = item;
   }
void cqdelete() {
if(front == -1)
 {
 printf("circular queue is empty \n");
return; }
printf("delted element = %d \n",cq[front]);
if(front == rear)
{
 front = -1;
 rear = -1;
 }
else if(front == SIZE - 1) {
 front = 0; }else
{
front = front + 1;}
     }
void cqdisplay() {
 int i;
 if(front == -1)  {
printf("circular queue is empty \n");
 return;   }
 printf("contents of circular queue \n");
  if(front <= rear)
{   for(i = front; i <= rear; i++){
 printf("%d \n",cq[i]);
 }  } else
{
 for(i = front; i <= SIZE - 1; i++){
 printf("%d \n",cq[i]);
 }
for(i = 0; i <= rear; i++){
 printf("%d \n",cq[i]);
 }    }     }


```
# Part - B 5 function*/
```py
#include<stdio.h>
#include<conio.h>
void insertion_sort(int a[], int n)
{int pass,key,j;
for(pass = 1; pass < n; pass++)
{key = a[pass];
for(j = pass-1; j >= 0 && key < a[j]; j--)
{ a[j + 1] = a[j];
}a[j + 1] = key;
}}
void main(){
int a[20],n,i;
clrscr();
printf("enter the size of an array \n");
scanf("%d",&n);
printf("enter the array elements \n");
for(i = 0; i < n ; i++)
{ scanf("%d",&a[i]);}
printf("entered elements are \n");
for(i = 0; i < n; i++)
{ printf("%4d",a[i]);
}
insertion_sort(a,n);
printf("\nsorted array \n");
for(i = 0; i < n ; i++)
{printf("%4d",a[i]);
}getch();
}
```
# 6th inorder preorder 
```py
#include<stdio.h>
#include<alloc.h>
#include<conio.h>
struct node  {
int data;
struct node *llink;
struct node *rlink;
};
typedef struct node* NODE;
NODE create(NODE,int);
void preorder(NODE);
void inorder(NODE);
void postorder(NODE);
void main()  {
 int item,op;
 NODE root = NULL;
 clrscr();
 do
 {
  printf("1.Create \n");
  printf("2.Preorder \n");
  printf("3.Inorder \n");
   printf("4.Postorder \n");
   printf("5.Exit \n \n");
   printf("enter option \n");
   scanf("%d",&op);
   switch(op)   {
case 1:
printf("enter the item to be inserted \n");
scanf("%d",&item);
root = create(root,item);
break;
case 2:
if(root == NULL)
 {
printf("NULL Tree \n");
}  else   {
printf("Preorder traversal \n");
preorder(root);
}
break; 
case 3:
if(root == NULL)
{
printf("NULL Tree \n");
}  else  {
printf("Inorder traversal \n");
 inorder(root);
}
break;
case 4:
if(root == NULL)
 {
printf("NULL Tree \n");
}
else  {
 printf("Postorder traversal \n");
postorder(root);  }
break;  }
 } while(op != 5);
}
NODE create(NODE root,int item)
 {
  NODE temp,cur,prev;
  temp = (NODE) malloc(sizeof(struct node));
  temp->data = item;
  temp->llink = NULL;
  temp->rlink = NULL;
 if(root == NULL)
  {
return temp;
 }
 cur = root;
 while(cur != NULL)
 {
   prev = cur;
    if(item < cur->data)
{
  cur = cur->llink;
 }
  else{
cur = cur->rlink;
}    }
 if(item < prev->data)
 {
prev->llink = temp;  }
 else  {
prev->rlink = temp;
}  return root;
}
void preorder(NODE root)
    {
  if(root != NULL)
{
printf("%d \t",root->data);
preorder(root->llink);
preorder(root->rlink);
}   }
void inorder(NODE root)
{
 if(root != NULL) {
inorder(root->llink);
printf("%d \t",root->data);
 inorder(root->rlink);
}  }
 void postorder(NODE root)
 {
   if(root != NULL)
{
postorder(root->llink);
postorder(root->llink);
printf("%d \t",root->data);
	}  }
```
