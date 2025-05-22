# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm

Step 1: Input the Data

Read a single line of space-separated values from input_data.

The first number n represents the number of variables (size of the system).

The remaining n*(n+1) values represent the augmented matrix of the system (A|b), which includes coefficients of the equations and the constants.

Step 2: Reshape Input

Convert the flat list of numbers into an n x (n+1) matrix (augmented matrix).

Step 3: Forward Elimination (Make Upper Triangular Matrix)

For each row i from 0 to n-1:

Check for zero pivot: If the pivot element matrix[i][i] is 0, raise an error (partial pivoting not implemented).

Normalize pivot row: Divide the entire row i by the pivot element.

Eliminate below: For each row j > i, eliminate the i-th coefficient by subtracting an appropriate multiple of the i-th row from the j-th row.

Step 4: Back Substitution

Initialize solution vector x of size n with zeros.

For each row i from n-1 to 0 (bottom to top):

Calculate:

x[i]=RHS value− j=i+1∑n−1(coefficient×x[j])

Step 5: Format Output

Format the solution x into strings like X0 = val, X1 = val, ..., rounded to two decimal places.

Step 6: Return the Result




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

