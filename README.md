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
def gaussian_elimination(input_data):
    import numpy as np

    # Parse the input
    data = list(map(float, input_data.strip().split()))
    n = int(data[0])
    matrix = np.array(data[1:]).reshape((n, n + 1))

    for i in range(n):
        pivot = matrix[i][i]
        if pivot == 0:
            raise ValueError("Zero pivot encountered; partial pivoting needed.")
        matrix[i] = matrix[i] / pivot
        for j in range(i + 1, n):
            factor = matrix[j][i]
            matrix[j] = matrix[j] - factor * matrix[i]

    x = np.zeros(n)
    for i in range(n - 1, -1, -1):
        x[i] = matrix[i][-1] - sum(matrix[i][j] * x[j] for j in range(i + 1, n))

    result = " ".join([f"X{i} = {x[i]:.2f}" for i in range(n)])
    return result

input_data = "3 1 2 4 18 2 12 -2 9 5 26 5 14"
print(gaussian_elimination(input_data))
```

## Output:

![image](https://github.com/user-attachments/assets/c513ad55-262d-47dc-baa0-f9eee81443a8)




## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

