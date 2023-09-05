LAB PROGRAMS
1. C Program to find Mechanical Energy of a particle
using E=mgh+1/2 mv2
.
# include<stdio.h>
void main()
{
float m,h,v,me;
float g=9.8;
printf(“Enter the mass of the body:”);
scanf(“%f”,&m);
printf(“Enter the velocity of the body:”);
scanf(“%f”,&v);
printf(“Enter the displacement of the body:”);
scanf(“%f”,&h);
me=m*g*h+0.5*m*v*v;
printf(“The Mechanical Energy of the body= %d”,me);
}
2. C Program to convert Kilometres into Metres and
Centimetres .
# include<stdio.h>
void main()
{
float km,m,cm;
printf(“Enter the distance in Kilometres:”);
scanf(“%f”,&km);
m=km*1000;
cm=km*100000;
printf(“The given distance in metres =%f \n The given
distance in Centimetres =%f :”,m,cm);
}
3. C Program to check whether the given character is
an Uppercase or a Lowercase or a Special character.
# include<stdio.h>
void main()
{
char c;
printf(“Enter any Character:”);
scanf(“%c”,&c);
if(c>=65&&c<=90)
printf(“It is an Uppercase Character.”);
else if(c>=97&&c<=122)
printf(“It is an Lowercase Character.”);
else
printf(“It is an Special Character.”);
}
4. C Program to balance the given chemical equation
values x, y, p, q of a simple chemical equation of the
type: the task is to find out the values of constants b1,
b2, b3 such that the equation is balanced on both the
sides and it must be in the reduced form.
# include<stdio.h>
void main()
{
int x=2,y=3,p=4,q=5,b1,b2,b3,temp;
if(p%x==0&&q&y==0)
{
b1=p/x;
b2=q/y;
b3=1;
}
else
{
p=p*y;
q=q*x;
b3=x*y;
temp=gcd(p,gcd(q,b3));
b1=p/temp;
b2=q/temp;
b3=b3/temp;
}
printf(“The values of \n b1=%d \n b2=%d \n
b3=%d”,b1,b2,b3);
}
int gcd(int a, int b)
{
if(b==0)
return a;
return gcd(b,a%b);
}
5. C Program to implement Matrix Multiplication and
validate the rules of Multiplication.
# include<stdio.h>
void main()
{
int a[10][10], b[10][10], c[10][10],I,j,k,m,n,p,q;
printf(“\t Give the order of first matrix:\t\t m=”);
scanf(“%d”,&m);
printf(“\t\t n=”);
scanf(“%d”,&n);
printf(“\t Give the elements of first matrix:”);
for(i=0;i<m;i++)
{
for(j=0;j<n;j++)
{
scanf(“%d”,&a[i][j]);
}}
printf(“\t Give the order of second matrix:\t\t p=”);
scanf(“%d”,&mp);
printf(“\t\t q=”);
scanf(“%d”,&q);
printf(“\t Give the elements of second matrix:”);
for(i=0;i<p;i++)
{
for(j=0;j<q;j++)
{
scanf(“%d”,&b[i][j]);
}}
if(p!=n)
printf(“\t Such Matrix Multiplication is not possible.”);
else
{
for(i=0;i<m;i++)
{
for(j=0;i<q;j++)
{
C[i][j]=0;
for(k=0;k<n;k++)
{
c[i][j]+=a[i][k]*b[k][j];
}}}
printf(“The product of 2 Matrices is=”);
for(i=0;i<m;i++)
{
for(j=0;i<q;j++)
{
printf(“\t %d”,c[i][j];
}
printf(“\n”);
}}
6. C Program to Bubble Sort.
# include<stdio.h>
void main()
{
Int arr[100];
int i,j,temp,size;
printf(“\n Enter the size of the array:”);
scanf(“%d”,&size);
printf(“\n Enter the array elements:”);
for(i=0;i<size;i++)
{
scanf(“%d”,&arr[i]);
}
for(i=1;i<size;i++)
{
for(j=0;j<size-1;j++)
{
if (a[j]<a[j+1])
{
temp=a[j];
a[j]=a[j+1];
a[j+1]=a{j];
}}}
printf(“\n After Sorting:\n”);
for(i=0;i<size;i++)
{
printf(“%d”,arr[i]);
}
7.
a) C Program to compute cos(x) using Taylor’s Series
approximation. Compare your result with the built-in
math library function.
# include<stdio.h>
#include<math.h>
void main()
{
int i,n;
float x,sum=1,t=1;
printf(“Enter the values for x:”);
scanf(“%f”,&x);
printf(“\n Enter the values for n:”);
scanf(“%d”,&n);
x=x*3.14159/180;
for(i=1;i<=n;i++)
{
t=t*(-1)*x*x/(2*i*(2*i-1));
sum+=t;
}
printf(“The value of cos(%f) is =%.4f”,x,sum);
printf(“Using Library function, the value of cos(%f) is
=%.f”,x,cos(x));
}
b) C Program to compute sin(x) using Taylor’s Series
approximation. Compare your result with the built-in
math library function.
# include<stdio.h>
#include<math.h>
void main()
{
int i,n;
float x,sum=x,t=1;
printf(“Enter the values for x:”);
scanf(“%f”,&x);
printf(“\n Enter the values for n:”);
scanf(“%d”,&n);
x=x*3.14159/180;
for(i=1;i<=n;i++)
{
t=t*(-1)*x*x/(2*i*(2*i-1));
sum+=t;
}
printf(“The value of sin(%f) is =%.4f”,x,sum);
printf(“Using Library function, the value of sin(%f) is
=%.f”,x,sin(x));
}
8. C Program to implement String operations such as
compare, concatenate and string length.
# include<stdio.h>
# include<stdlib.h>
int length(char str[]);
int compare(char str1[],char str2[]);
void concatenate(char str1[],char str2[]);
void main()
{
char str1[30], str2[30];
int a;
printf(“enter string 1 \n”);
scanf(“%s”,&str1);
a=length(str1);
printf(“length of %s =%d \n”,str1,a);
printf(“enter string 2 \n”);
scanf(“%s”,&str2);
a=compare(str1,str2);
if(a==0)
{
printf((“%s and %s are identical \n”, str1,str2);
}
else
{
printf((“%s and %s are not identical \n”, str1,str2);}
concatenate(str1,str2);
}
int length(char str[])
{
int len=0;
while(str[len]!=’\0’)
len++;
return len;
}
int compare(char str1[], char str2[])
{
int i=0;
while(str1[1]==str2[i])
{if(str1[i]==’\0’ || str2[i]== ’\0’)
break;
i++;
}
return str1[i]-str2[i];
}
void concatenate(char str1[],char str2[])
{
int i=0,j=0;
while(str1[i]!= ’/0’)
{
i++;
}
while(str2[j]!= ’/0’)
{
(str1[i]= str2[j];
i++;
j++;
}
str1[i]=’\0’;
printf((“concatenated string is %s \n”,str1);
}
9.C Program to read, write and compute average
marks and the students scoring above and below
average marks for a class of N students.
# include<stdio.h>
struct student
{
int marks;
}st[10];
void main()
{
int i,n;
float total=0,avgmarks;
printf(“Enter the number of students in class(<=10):”);
scanf(“%d”,&n);
for(i=0;i<n;i++)
{
printf(“Enter the Student %d marks:”,i+1);
scanf(“%d”,&st[i].marks);
total+=st[i].marks;
}
avgmarks=total/n;
printf(“\n Average Marks = %.2f”,avgmarks);
for(i=0;i<n;i++)
{
if(st[i].marks>=avgmarks)
{
printf(“\n Student %d marks =%d above
average”,i+1,st[i].marks);
}
else
{
printf(“\n Student %d marks =%d below
average”,i+1,st[i].marks);
}}
10. C Program using pointers to compute the sum,
mean and standard deviation of all elements stored in
an array of N real elements.
# include<stdio.h>
#include<math.h>
int main()
{
float a[100],sum=0.00,mean,variance=0.00,stddev,*p;
int i,n;
printf(“Enter the number of data:”);
scanf(“%d”,&n);
printf(“Enter the data elements:”);
p=a;
for(i=0;i<n;i++)
{
scanf(“%f”,p);
sum+=*p;
p++;
}
mean=sum/n;
p=a;
for(i=0;i<n;i++)
{
variance+=(mean-p)(mean-*p);
p++;
}
stddev=sqrt(variance);
printf(“\n From the above given data:\n Sum=%.2f\n
Mean=%.2f\nVariance=%.2f\n Standard
Deviation=%.2f”,sum,mean,variance,stddev);
}


