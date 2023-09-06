1)   Find Inverse Laplace transform of F(s)*G(s) for the following: F(s) = 1/s , G(s) = 1/((s^2)+(a^2))
clc
clear
syms t a s u F G
F=1/s
G=1/(s^2+a^2)
f(t)=ilaplace(F)
g(t)=ilaplace(G)
convl=int((f(u)*g(t-u)),u,0,t)
pretty(convl)

OUTPUT:
F =1/s
G =1/(a^2 + s^2)
f(t) =1
g(t) =sin(a*t)/a
convl =-(cos(a*t) - 1)/a^2
 cos(a t) - 1
- ------------
 2
 a
1)  Find the inverse Laplace transform of 𝑭(𝒔) =
𝒔−𝟓
𝒔 (𝒔−𝟐)𝟐
clc
clear
syms t s
F = input('enter first func')
f(t)=ilaplace(F)

OUTPUT:
enter first func
(s-5)/(s*(s-2)^2)
F =(s - 5)/(s*(s - 2)^2)
f(t) =
(5*exp(2*t))/4 - (3*t*exp(2*t))/2 - 5/4


3)  Write and execute the MATLAB code to find the gradient vector of f(x,y)=xe^(x^2-y^2) with
respect to vector [x,y] and also plot the contour lines and vectors.
x = -2:0.2:2;
y = x';
z = x .* exp(-x.^2 - y.^2);
[px,py] = gradient(z);
%Plotting the contour lines and vectors
in the same figure.
figure
contour(x,y,z)
hold on
quiver(x,y,px,py)
hold off

OUTPUT:
Gradient of f is given by
ans =
exp(- x^2 - y^2) - 2*x^2*exp(- x^2 - y^2)
-2*x*y*exp(- x^2 - y^2)


3)  Write and execute the MATLAB code to find divergence and show that the divergence of the curl of
the vector field V=(x, 2 y^2, 3 z^3) is 0.
syms x y z
V = [x 2*y^2 3*z^3];
X = [x y z];
divCurl = divergence(curl(V,X),X)

OUTPUT:
div = 1 + 9*z^2 + 4*y
divCurl = 0


4)  Write and execute the MATLAB code to find the dimension a n d b a s i s of subspace spanned by the
vectors (1, 2, 1, -1),(3,1,0,5) and (0,5,3,-8).
clc;
V1 = [1;2;1;-1]; V2 = [3;1;0;5]; V3 =
[0;5;3;-8];
V = [V1 V2 V3];
[R,basiccol]=rref(V);
R_1=rank(rref(V));
fprintf('Dimension of subspace spanned
by the given vectors is given by');
R_1
fprintf('Basis of subspace is given
by');
B=V(:,basiccol)

OUTPUT:
Dimension of subspace spanned by the
given vectors is given by
R = 2
Basis of subspace is given by
B = 1 3
 2 1
 1 0
 -1 5

 
5)  Write and execute the MATLAB code to verify the rank-nullity theorem for the linear transformation T: R
3
→ R
3 defined by T(x,y,z) = (x + 4y + 7z,2x + 5y + 8z,3x + 6y + 9z).
clc;
fprintf('Matrix of Linear
Transformation is given by');
A=[1 4 7; 2 5 8; 3 6 9]
rref(A);
fprintf('Echelon form of A is given
by');
rref(A)
U=rank(rref(A));
fprintf('Rank of Linear Transformation
is given by');
U
null(A);
fprintf('Null space is given by');
null(A)
V=size(null(A),2);
fprintf('Dimension of Null space is
given by');
V
 if U + V == 3
fprintf('Rank Nullity Theorem holds');
 else
fprintf('Rank Nullity Theorem does not
hold');
 end
 
OUTPUT:
Matrix of Linear Transformation is given
by
A =
 1 4 7
 2 5 8
 3 6 9
Echelon form of A is given by
E = 1 0 -1
 0 1 2
 0 0 0
Rank of Linear Transformation is given by
U = 2
Null space is given by
N_S = 0.4082
 -0.8165
 0.4082
Dimension of Null space is given by
V = 1
Rank Nullity Theorem holds


6)  Write and execute the MATLAB code to find the root of y=cos(x) near 1 with tolerance 0.0001. Carry out
four iterations by Newton- Raphson method
f = @(x) (cos(x));
fd = @(x) (-sin(x));
x0 = input('Enter initial approximaation:
');
n = input('Enter no. of iterations, n:
');
tol = input('Enter tolerance, tol: ');
i = 1;
while i <= n
 d=f(x0)/fd(x0);
 x0 = x0 - d
 if abs(d) < tol
fprintf('\nApproximate solution xn= %0.4f
\n\n',x0)
 break;
 else
i = i+1;
 end
end

OUTPUT:
Enter initial approximaation: 1
Enter no. of iterations, n: 5
Enter tolerance, tol: 0.00001
x0 = 1.6421
x0 = 1.5707
x0 = 1.5708
x0 = 1.5708
Approximate solution xn= 1.5708  


7 )  Write and execute the MATLAB code to find the root of y=sin(x)+cos(x)+exp(x)-8 at 2 and 3 with tolerable
error 0.00001 by Regula-Falsi method
syms x;
% Input Section
y = input('Enter non-linear equations: ');
a = input('Enter first guess: ');
b = input('Enter second guess: ');
e = 0.00001 ; %input('Tolerable error: ');
% Finding Functional Value
fa = eval(subs(y,x,a));
fb = eval(subs(y,x,b));
% Implementing the Method
if fa*fb > 0
 disp('Given initial values do not
bracket the root.');
else
 c = (a*fb-b*fa)/(fb-fa);
 fc = eval(subs(y,x,c));

fprintf('\n\na\t\t\tb\t\t\tc\t\t\tf(c)\n')
;
 while abs(fc)>e
fprintf('%f\t%f\t%f\t%f\n',a,b,c,fc);
 if fa*fc< 0
 b =c;
 fb = eval(subs(y,x,b));
 else
 a =c;
 fa = eval(subs(y,x,a));
 end
 c = (a*fb-b*fa)/(fb-fa);
 fc = eval(subs(y,x,c));
 end
 fprintf('\nRoot is: %f\n', c);
end

OUTPUT:
Enter non-linear equations:
sin(x)+cos(x)+exp(x)-8
Enter first guess: 2
Enter second guess: 3
a b c f(c)
2.000000 3.000000 2.010374 -0.054516
2.010374 3.000000 2.015152 -0.025119
2.015152 3.000000 2.017349 -0.011551
2.017349 3.000000 2.018358 -0.005306
2.018358 3.000000 2.018821 -0.002437
2.018821 3.000000 2.019034 -0.001119
2.019034 3.000000 2.019132 -0.000514
2.019132 3.000000 2.019177 -0.000236
2.019177 3.000000 2.019197 -0.000108
2.019197 3.000000 2.019207 -0.000050
2.019207 3.000000 2.019211 -0.000023
2.019211 3.000000 2.019213 -0.000010
Root is: 2.019214


8)   Write and execute the MATLAB code that uses Newton's forward interpolation formula and find the
approximate value of f (9) given the following data points (x,y) = (8,10), (10,19), (12,32.5), (14,54),
(16,89.5) & (18,154).
clc;
clear all;
x=[8,10,12,14,16,18];
y=[10,19,32.5,54,89.5,154];
n=length(x);
X=9;
h=x(2)-x(1);
F=zeros(n,n);
F(:,1)=y;
for j=2:n
 for i=j:n
F(i,j)=F(i,j-1)-F(i-1,j-1);
 end
end
F
p=(X-x(1))/h;
d=F(1,1)+p*F(2,2)+p*(p1)*F(3,3)/factorial(2)+p*(p-1)*(p2)*F(4,4)/factorial(3)+p*(p-1)*(p-2)*(p3)*F(5,5)/factorial(4)+p*(p-1)*(p-2)*(p3)*(p-4)*F(6,6)/factorial(5);
fprintf('f(%0.4f)= %0.4f \n', X, d);

OUTPUT:
F =
 10.0000 0 0 0 0 0
 19.0000 9.0000 0 0 0 0
 32.5000 13.5000 4.5000 0 0 0
 54.0000 21.5000 8.0000 3.5000 0 0
 89.5000 35.5000 14.0000 6.0000 2.5000 0
 154.0000 64.5000 29.0000 15.0000 9.0000 6.5000
f(9.0000)= 14.2363


9)  Write and execute the MATLAB code that uses Newton's backward interpolation formula and find the
approximate value of f(17) given the following data points (x,y) = (8,10), (10,19), (12,32.5), (14,54),
(16,89.5) & (18,154).
clc;
clear all;
x=[8,10,12,14,16,18];
y=[10,19,32.5,54,89.5,154];
n=length(x);
X=17;
h=x(2)-x(1);
F=zeros(n,n);
F(:,1)=y;
for j=2:n
 for i=j:n
F(i,j)=F(i,j-1)-F(i-1,j-1);
 end
end
F
p=(X-x(n))/h;
d=F(6,1)+p*F(6,2)+p*(p+1)*F(6,3)/factoria
l(2)+p*(p+1)*(p+2)*F(6,4)/factorial(3)+p*
(p+1)*(p+2)*(p+3)*F(6,5)/factorial(4)+p*(
p+1)*(p+2)*(p+3)*(p+4)*F(6,6)/factorial(5
);
fprintf('f(%0.4f)= %0.4f \n', X, d);

OUTPUT:
 10.0000 0 0 0 0 0
 19.0000 9.0000 0 0 0 0
 32.5000 13.5000 4.5000 0 0 0
 54.0000 21.5000 8.0000 3.5000 0 0
 89.5000 35.5000 14.0000 6.0000 2.5000 0
 154.0000 64.5000 29.0000 15.0000 9.0000 6.5000
f(17.0000)= 116.6582


10)  Write and execute the MATLAB code to evaluate ∫ √(sin(x) + cos(x))
1
0
dx with 6 sub intervals by using
Simpson’s 1/3rd Rule
clc
clear all
close all
f=@(x)(sqrt(sin(x)+cos(x)));
a=input('Enter the lower limit a:');
b=input('Enter the upper limit b:');
n=input('Enter the number of subintervals n:');
h=(b-a)/n;
if rem(n,2)==1
fprintf('\n Please enter valid n !!');
n=input('\n Enter n as even number:');
end
k=1:1:n-1;
S=f(a+k.*h);
out=(h/3).*(f(a)+f(b)+4.*(S(1)+S(3)+S(5))
+2.*(S(2)+S(4)));
fprintf('The value of the integration is
%.4f',out)

OUTPUT:
Enter the lower limit a:
0
Enter the upper limit b:
1
Enter the number of sub-intervals n:
6
The value of the integration is 1.1394


11)  Write and execute the MATLAB code to evaluate ∫ √sin(x)
𝜋⁄2
0
dx with 6 subintervals by using Simpson’s
3/8th
 Rule
clc
clear all
close all
f=@(x)(sqrt(sin(x)));
a=input('Enter the lower limit a:');
b=input('Enter the upper limit b:');
n=input('Enter the number of subintervals n:');
h=(b-a)/n;
if rem(n,2)==1
fprintf('\n Please enter valid n !!');
n=input('\n Enter n as even number:');
end
k=1:1:n-1;
S=f(a+k.*h);
out=(3*h/8).*(f(a)+f(b)+3.*(S(1)+S(2)+S(4
)+S(5))+2.*S(3));
fprintf('The value of the integration is
%.4f',out)

OUTPUT:
Enter the lower limit a:
0
Enter the upper limit b:
pi/2
Enter the number of sub-intervals n:
6
The value of the integration is 1.1849


12)  Write and execute the MATLAB code to solve 𝑑𝑦
𝑑𝑥
= 3𝑥 + 𝑦/2, 𝑦(0) = 1 by Runge Kutta method for 𝑦(0.5)
taking h=0.1. Display output for each value of x upto 0.5.
clc;
f = @(x,y)3.*x+(y./2) ;
x=0; %initial value of x
y = 1; %initial value of y
h=0.1; % step length
xn=0.5;%final value of x
n=(xn-x)/h; % number of iterations
for i=1:n
 fprintf("Interation number=%f\n",i)
 disp(" x y")
 z=[x y];
 disp(z)
 k1 = h*f(x,y)
 k2 = h*f(x+h/2,y+k1/2)
 k3 = h*f(x+h/2,y+k2/2)
 k4 = h*f(x+h, y+k3)
 y= y+(k1 + 2* k2 +2*k3+k4 )/6
 x =x+h;
 end

 OUTPUT:
Interation number=1.000000
 x y
 0 1
k1 = 0.0500 k2 = 0.0663
k3 = 0.0667 k4 = 0.0833
 y = 1.0665
Interation number=2.000000
 x y
 0.1000 1.0665
k1 = 0.0833 k2 = 0.1004
k3 = 0.1008 k4 = 0.1184
 y = 1.1672
Interation number=3.000000
 x y
 0.2000 1.1672
k1 = 0.1184k2 = 0.1363
k3 = 0.1368k4 = 0.1552
 y = 1.3038
Interation number=4.000000
 x y
 0.3000 1.3038
k1 = 0.1552k2 = 0.1741
k3 = 0.1745k4 = 0.1939
 y = 1.4782
Interation number=5.000000
 x y
 0.4000 1.4782
k1 = 0.1939k2 = 0.2138
k3 = 0.2143k4 = 0.2346
 y = 1.6923

 
13)  Write and execute the MATLAB code to solve 𝑑𝑦
𝑑𝑥
= 𝑙𝑜𝑔𝑒(𝑥 + 𝑦), 𝑦(1) = 2 by Modified Euler’s method for
𝑦(1.4)taking h=0.1. Display output for each value of x upto 1.4. Perform 4 modifications at every step.
clear all
clc
f =@(x,y) log(x+y);
x0=1; %initial value of x
y0 =2; %initial value of y
h=0.1; % step length
xn=1.4;%final value of x
n=(xn-x0)/h; % number of iterations
for i=1:n+1
 fprintf("Interation number=%f\n",i)
y1E=y0+h*f(x0,y0)
for j=1:3
y1=y0+h/2*(f(x0,y0)+f(x0+h,y1E))
y1E=y1;
j=j+1;
end
y0=y1;
x0=x0+h;
n=n+1;
end
x=[x0(:)];
y=[y0(:)];
disp(" x y")
z=[x y];
disp(z)

OUTPUT:
Interation number=1.000000
y1E = 2.1099
y1 = 2.1132
y1 = 2.1133
y1 = 2.1133
Interation number=2.000000
y1E = 2.2300
y1 = 2.2333
y1 = 2.2333
y1 = 2.2333
Interation number=3.000000
y1E = 2.3567
y1 = 2.3598
y1 = 2.3599
y1 = 2.3599
Interation number=4.000000
y1E = 2.4896
y1 = 2.4927
y1 = 2.4927
y1 = 2.4927
 x y
 1.4000 2.4927
