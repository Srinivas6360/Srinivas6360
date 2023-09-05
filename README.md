//1.C Program to find Mechanical Energy of a particle using E=mgh+1/2
mv2.
#include<stdio.h>
void main()
{
 float m,h,v,energy;
 float g=9.8;
 printf("Enter the mass of the body:\n");
 scanf("%f",&m);
 printf("Enter the velocity of the body:\n");
 scanf("%f",&v);
 printf("Enter the displacement of the body:\n");
 scanf("%f",&h);
 energy=m*g*h+0.5*m*v*v;
 printf("The Mechanical Energy of the body= %f\n",energy);
}
/*Output
student@student-virtual-machine:~$ cc Energy.c
student@student-virtual-machine:~$ ./a.out
Enter the mass of the body:
2
Enter the velocity of the body:
4
Enter the displacement of the body:
5
The Mechanical Energy of the body= 114.000000
*/


//2. C Program to convert Kilometres into Metres and Centimetres .
# include<stdio.h>
void main()
{
 float km,m,cm;
 printf("Enter the distance in Kilometres:\n");
 scanf("%f",&km);
 m=km*1000;
 cm=km*100000;
 printf("The given distance in metres =%f\nThe given distance in
Centimetres =%f\n",m,cm);
}
/*Output
student@student-virtual-machine:~$ cc kilo.c
student@student-virtual-machine:~$ ./a.out
Enter the distance in Kilometres:
100
The given distance in metres =100000.000000
The given distance in Centimetres =10000000.000000
*/


//3.C Program to check whether the given character is an Uppercase or a
Lowercase or a Special character
# include<stdio.h>
void main()
{
 char c;
 printf("Enter any Character:\n");
 scanf("%c",&c);
 if(c>=65&&c<=90)
 printf("It is an Uppercase Character\n");
 else if(c>=97&&c<=122)
 printf("It is an Lowercase Character\n");
 else
 printf("It is an Special Character\n");
}
/*Output
student@student-virtual-machine:~$ cc character.c
student@student-virtual-machine:~$ ./a.out
Enter any Character:
e
It is an Lowercase Character
student@student-virtual-machine:~$ ./a.out
Enter any Character:
E
It is an Uppercase Character
*/


//5.C Program to implement Matrix Multiplication and validate the rules
of Multiplication.
#include<stdio.h>
#include<stdlib.h>
void main()
{
 int m,n,p,q,i,j,k,a[10][10],b[10][10],c[10][10];
 printf("enter the order of matrix A\n");
 scanf("%d%d",&m,&n);
 printf("enter the order of matrix B\n");
 scanf("%d%d",&p,&q);
 if(n!=p)
 {
 printf("matrix multiplication not possible\n");
 exit(0);
 }
else
{
 printf("enter the elements of the first matrix \n");
 for(i=0;i<m;i++)
 for(j=0;j<n;j++)
 scanf("%d",&a[i][j]);

printf("enter the elements of the second matrix \n");
 for(i=0;i<p;i++)
 for(j=0;j<q;j++)
 scanf("%d",&b[i][j]);

for(i=0;i<m;i++)
{
 for(j=0;j<q;j++)
 {
 c[i][j]=0;
 for(k=0;k<n;k++)
 {
 c[i][j]= c[i][j]+a[i][k]*b[k][j];
 }
 }
}
printf("the product of 2 matrices are : \n");
for(i=0;i<m;i++)
{
 for(j=0;j<q;j++)

 printf("%d\t",c[i][j]);

printf("\n");
}
}
}
/*Output
student@student-virtual-machine:~$ cc matrix.c
student@student-virtual-machine:~$ ./a.out
enter the order of matrix A
2 2
enter the order of matrix B
2 2
enter the elements of the first matrix
1 2 3 4
enter the elements of the second matrix
1 1 1 1
the product of 2 matrices are :
3 3
7 7
student@student-virtual-machine:~$ ./a.out
enter the order of matrix A
2 2
enter the order of matrix B
3 2
matrix multiplication not possible
*/


//6. C Program to Bubble Sort
#include<stdio.h>
void main()
{
 int n,i,j,a[20],temp;
 printf("enter the number of elements\n");
 scanf("%d",&n);
 /*read or input the elements to sort*/

 printf("read the elements\n");
 for(i=0;i<n;i++)
 scanf("%d",&a[i]);

 /*method to sort the elements in ascending order*/
 for (i=1 ; i<n ; i++) //outer loop
 {
 for (j = 0 ; j <n-i ; j++) // inner loop
 { if (a[j] > a[j+1])
 { temp = a[j];
 a[j] = a[j+1];
 a[j+1] = temp;
 }
 }
 }

 /* print the sorted array*/

 printf("the sorted elements are\n");
 for(i=0;i<n;i++)
 printf("%d\n",a[i]);
}
/*student@student-virtual-machine:~$ cc bubble.c
student@student-virtual-machine:~$ ./a.out
enter the number of elements
5
read the elements
50 40 30 20 10
the sorted elements are
10
20
30
40
50
student@student-virtual-machine:~$ cc bubble.c
student@student-virtual-machine:~$ ./a.out
enter the number of elements
3
read the elements
2 1 8
the sorted elements are
1
2
8
*/


/7a)C Program to compute cos(x) using Taylorâ€™s Series approximation.
//Compare your result with the built-in math library function.
# include<stdio.h>
#include<math.h>
void main()
{
 int i,n;
 float x,sum=1,t=1;
 printf("Enter the values for x:");
 scanf("%f",&x);
 printf("\n Enter the values for n:");
 scanf("%d",&n);
 x=x*3.14159/180;
 for(i=1;i<=n;i++)
 {
 t=t*(-1)*x*x/(2*i*(2*i-1));
 sum+=t;
 }
 printf("The value of cos(%f) is =%.4f\n",x,sum);
 printf("Using Library function, the value of cos(%f) is
=%.4f\n",x,cos(x));
}
/*output
student@student-virtual-machine:~$ cc labcosine2.c -lm
student@student-virtual-machine:~$ ./a.out
Enter the values for x:45
Enter the values for n:5
The value of cos(0.785398) is =0.7071
Using Library function, the value of cos(0.785398) is =0.7071
*/


//7b)C Program to compute sin(x) using Taylorâ€™s Series approximation.
//Compare your result with the built-in math library function.
#include<stdio.h>
#include<math.h>
void main()
{
 int i, n;
 float x, sum, t;


 printf(" Enter the value for x in degree : ");
 scanf("%f",&x);

 printf(" Enter the value for n : ");
 scanf("%d",&n);

 x=x*3.14159/180;
 t=x;
 sum=x;

 /* Loop to calculate the value of Sine */
 for(i=1;i<=n;i++)
 {
 t=(t*(-1)*x*x)/(2*i*(2*i+1));
 sum=sum+t;
 }

 printf(" The value of Sin(%f) = %.4f\n",x,sum);
 printf("using library function sin(%f)=%.4f\n",x,sin(x));


}
/*Output
student@student-virtual-machine:~$ cc labsine2.c -lm
student@student-virtual-machine:~$ ./a.out
Enter the value for x in degree : 45
Enter the value for n : 5
The value of Sin(0.785398) = 0.7071
using library function sin(0.785398)=0.7071
*/



//8. C Program to implement String operations such as compare,
concatenate and string length -- 1st method.
# include<stdio.h>
int length(char s1[]);
void compare(char s1[], char s2[]);
void concat(char s1[], char s2[]);
void main()
{
 char s1[200], s2[100];
 int len;
 printf("\nEnter the String s1: ");
 gets(s1);
 printf("\nEnter String s2 :");
 gets(s2);
len = length(s1);
printf("Length of the String s1 is : %d\n", len);
compare(s1,s2);
concat(s1, s2);
}
//to find the length of the string
int length(char s1[])
{
 int i = 0;
 while (s1[i] != '\0')
 i++;
 return (i);
}
void compare(char s1[], char s2[])
{
 int i = 0;
 while (s1[i] == s2[i] && s1[i] != '\0')
 i++;
 if (s1[i] > s2[i])
 printf("String Not equal\n");
 else if (s1[i] < s2[i])
 printf("String Not equal\n");
 else
 printf("Strings are equal\n");
}
void concat(char s1[], char s2[])
{
 int i, j;
 i = length(s1);
 s1[i]=' ';
 i=i+1;
 for (j = 0; s2[j] != '\0';i++,j++)
 {
 s1[i] = s2[j];
 }
 s1[i] = '\0';
 printf("Concatenated String: %s\n",s1);
}
/*Output
student@student-virtual-machine:~$ cc strings.c
strings.c: In function â€˜mainâ€™:
strings.c:14:1: warning: â€˜getsâ€™ is deprecated (declared at
/usr/include/stdio.h:638) [-Wdeprecated-declarations]
gets(s1);
^
strings.c:16:1: warning: â€˜getsâ€™ is deprecated (declared at
/usr/include/stdio.h:638) [-Wdeprecated-declarations]
gets(s2);
^
/tmp/ccxgvhDc.o: In function `main':
strings.c:(.text+0x34): warning: the `gets' function is dangerous and
should not be used.
student@student-virtual-machine:~$ ./a.out
Enter the String s1: water
Enter String s2 :air
Length of the String s1 is : 5
String Not equal
Concatenated String: water air
student@student-virtual-machine:~$ ./a.out
Enter the String s1: air
Enter String s2 :air
Length of the String s1 is : 3
Strings are equal
Concatenated String: air air
*/


//8.C Program to implement String operations such as compare, concatenate
and string length -- 2nd method
# include<stdio.h>
//to find the length of the string
int length(char s1[])
{
int i = 0;
while (s1[i] != '\0')
i++;
return (i);
}
//to campare two strings
void compare(char s1[], char s2[])
{
 int i = 0;
 while (s1[i] == s2[i] && s1[i] != '\0')
 i++;
 if (s1[i] > s2[i])
 printf("String Not equal\n");
 else if (s1[i] < s2[i])
 printf("String Not equal\n");
 else
 printf("Strings are equal\n");

}
//to join two strings
void concat(char s1[], char s2[])
{
int i, j;
i = length(s1);
 s1[i]=' ';
 i=i+1;
for (j = 0; s2[j] != '\0';i++,j++) {
s1[i] = s2[j];
}
s1[i] = '\0';
printf("Concatenated String: %s\n",s1);
}
void main()
{
 char s1[200], s2[100];
 int len;
 printf("\nEnter the String s1: ");
 scanf("%s",s1);
 printf("\nEnter String s2 :");
 scanf("%s",s2);
 len = length(s1);
 printf("Length of the String s1 is : %d\n", len);
 compare(s1,s2);
 concat(s1, s2);
}
/*Output
student@student-virtual-machine:~$ cc strings2.c
student@student-virtual-machine:~$ ./a.out
Enter the String s1: cat
Enter String s2 :rat
Length of the String s1 is : 3
String Not equal
Concatenated String: cat rat
student@student-virtual-machine:~$ ./a.out
Enter the String s1: cat
Enter String s2 :cat
Length of the String s1 is : 3
Strings are equal
Concatenated String: cat cat
*/


//9.C Program to read, write and compute average marks and the students
scoring above and
//below average marks for a class of N students.
#include<stdio.h>
struct student
{
char name[20];
int stdid;
float marks;
char grade[1];
};
void main()
{
int i,n;
float sum=0, average;
struct student std[100];
printf("\nEnter the number of student in class\n");
scanf("%d",&n);
for(i=0;i<n;i++)
{
 printf("Details of students are\n");
 scanf("%s",std[i].name);
 scanf("%d",&std[i].stdid);
 scanf("%f",&std[i].marks);
 scanf("%s",std[i].grade);
}
sum=0;
for(i=0;i<n;i++)
 sum=sum+std[i].marks;
average=sum/n;
printf("The average marks is %f\n",average);
printf("\n\ndetails of the students above average are\n");
for(i=0;i<n;i++)
{
 if(std[i].marks>average)
 {
 printf("name of the student is %s\n",std[i].name);
 printf("id of the student is %d\n",std[i].stdid);
 printf("marks of the student is %f\n",std[i].marks);
 printf("grade of the student is %s\n",std[i].grade);
 }
}
printf("\n\ndetails of the students below average are\n");
for(i=0;i<n;i++)
{
 if(std[i].marks<average)
 {
 printf("name of the student is %s\n",std[i].name);
 printf("id of the student is %d\n",std[i].stdid);
 printf("marks of the student is %f\n",std[i].marks);
 printf("grade of the student is %s\n",std[i].grade);
 }
}
}
/*OUtput
student@student-virtual-machine:~$ cc student.c
student@student-virtual-machine:~$ ./a.out
Enter the number of student in class
2
Details of students are
AAA 1 90 A
Details of students are
BBB 2 56 C
The average marks is 73.000000
details of the students above average are
name of the student is AAA
id of the student is 1
marks of the student is 90.000000
grade of the student is A
details of the students below average are
name of the student is BBB
id of the student is 2
marks of the student is 56.000000
grade of the student is C
*/


//10. C Program using pointers to compute the sum, mean and standard
deviation of all elements stored in an array of N real //elements.
#include<stdio.h>
#include<math.h>
void main()
{
 int arr[10],n,i,sum=0;
 float mean, variance, std_deviation;
//Assigning array to pointer
 int *ptr=arr;
 printf("Enter the number of elements you want to use(<=10):\n");
 scanf("%d",&n);
 printf("Enter %d Elements:\n",n);
 for (i=0;i<n;i++)
 scanf("%d",&arr[i]);
//sum of elements of array using pointer
 for(i=0;i<n;i++)
 {
 sum+=*ptr;
 *ptr++;
 }
 mean=sum/n;
//Display sum,mean and standard deviation on screen
 printf("Sum = %d\n mean = %0.2f\n",sum,mean);
 variance = sum / (float)n;
 std_deviation = sqrt(variance);
 printf("variance of all elements = %.2f\n", variance);
 printf("Standard deviation = %.2f\n", std_deviation);
}
/*Output
student@student-virtual-machine:~$ cc mean.c -lm
student@student-virtual-machine:~$ ./a.out
Enter the number of elements you want to use(<=10):
3
Enter 3 Elements:
2 3 1
Sum = 6
mean = 2.00
variance of all elements = 2.00
Standard deviation = 1.41
*/
