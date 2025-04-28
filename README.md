# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
### Step1 :
Input the number of unknowns n and the augmented matrix elements (coefficients + constants).
### Step 2:
Apply Forward Elimination: eliminate variables step-by-step to create an upper triangular matrix.
### Step 3:
Apply Back Substitution: solve for variables starting from the last equation upwards.
### Step 4:
Display the solutions for each variable.

## Program:
```
/*
Program to find the solution of a matrix using Gaussian Elimination.
Developed by: Tamil Pavalan
RegisterNumber: 212223110058
*/
import numpy as np
import sys
n=int(input())
a=np.zeros((n,n+1))
x=np.zeros(n)

for i in range(n):
    for j in range(n+1):
        a[i][j]=float(input())

for i in range(n):
    if a[i][j]==0.0:
        sys.exit('Divide by zero detected!')
    
    for j in range(i+1,n):
        ratio=a[j][i]/a[i][i]
        
        for k in range(n+1):
            a[j][k]=a[j][k]-ratio*a[i][k]
            
x[n-1]=a[n-1][n]/a[n-1][n-1]

for i in range(n-2,-1,-1):
    x[i]=a[i][n]
    
    for j in range(i+1,n):
        x[i]=x[i]-a[i][j]*x[j]
        
    x[i]=x[i]/a[i][i]

for i in range(n):
    print('X%d = %0.2f'%(i,x[i]),end=' ')
```

## Output:

![image](https://github.com/user-attachments/assets/aafa21f3-fd4f-42fb-91f0-6a522c1d20db)



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

