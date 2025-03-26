```py
/* Part -A7sort a list of N elements quicksort */
#include<stdio.h>
#include<conio.h>
void quicksort(int[],int,int);
int partition(int[],int,int);
void main(){
int a[100],n,i;
clrscr();
printf("enter the size of an array \n");
scanf("%d",&n);
printf("enter the array elements \n");
for(i = 0; i < n ; i++)
{scanf("%d",&a[i]);
}printf("entered elements are \n");
for(i = 0; i < n; i++)
{printf("%d \n",a[i]);
}
quicksort(a,0,n - 1);
printf("sorted array \n");
for(i = 0; i < n ; i++)
{printf("%d \n",a[i]);
}getch();
}
void quicksort(int a[100], int low, int high)
{int j;
if (low < high) {
j = partition(a, low, high);  
quicksort(a, low, j - 1); 
quicksort(a, j + 1, high);  
}}
int partition(int a[100], int low, int high)
{int temp, key, i, j;
key = a[low];  
i = low + 1;   
j = high;      
while (i <= j) {
while (key >= a[i]) {
i++;}
while (key < a[j]) {
j--;}
if (i < j) {
temp = a[i];
a[i] = a[j];
a[j] = temp;
}}
if (a[j] < a[low]) {
temp = a[low];
a[low] = a[j];
a[j] = temp;
}return j;  }

```
```py
// lab-2 Develop a program to convert infix 
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
```py
/* Part - B 5  list of insertion sort using function*/
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
