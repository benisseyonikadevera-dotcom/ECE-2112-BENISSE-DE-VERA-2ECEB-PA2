# **⋆˙⟡*WELCOME TO BENISSE YONIKA'S NOTEBOOK! ⋆˙⟡**

## **ECE 2112**: *ADVANCED COMPUTER PROGRAMMING AND ALGORITHMS*

### PROGRAMMING ASSIGNMENT #2 

> **Name**: Benisse Yonika De Vera

> **Section**: 2ECE-B

> **Date Submitted**: August 29, 2026

*This repository contains my Programming Assignment #2 for the course "Advanced Computer Programming and Algorithms."*

## **PROBLEM A: REPRODUCIBLE NORMALIZATION PROBLEM**
- Create a reproducible random 5 × 5 integer **ndarray** named **X**. Use the following two statements before performing any calculation:

> `np.random.seed(2112)`

> `X = np.random.randint(10, 101, size=(5,5))`

- Normalize the complete array using **Z = (X - x̄)/σ**, where **x̄** is the mean of all 25 elements and **σ** is their population standard deviation as returned by NumPy's default **std()** call. Store the normalized array in **X_normalized**.

> **Required Checks**: Display **X**, **X_normalized**, its mean, and its standard deviation. Up to floating-point rounding, the normalized mean must be 0, and the normalized standard deviation must be 1.

> **Save the normalized array as**: `X_normalized.npy`


### **Code Explanation:**
- `np.random.seed(2112)` sets a fixed seed to ensure that `np.random.randint(10, 101, size=(5,5))` generates the exact same 5 × 5 matrix everytime.

- `X.mean()` calculates the overall mean (x̄) of all 25 elements, while `X.std()` computes the population standard deviation (σ).

- `(X - X.mean()) / X.std()` performs vectorized normalization on every element, resulting in a normalized mean of approximately 0 and a standard deviation of 1.

- `np.save('X_normalized.npy', X_normalized)` saves the normalized array binary file to disk.


### **Actual Code**:
```python
import numpy as np

np.random.seed(2112)
X = np.random.randint(10, 101, size=(5,5))

X_mean = X.mean()
X_std = X.std()
X_normalized = (X-X_mean) / X_std

print("Original Matrix X:\n", X) 
print("\nNormalized Matrix (X_normalized):\n", X_normalized)
print("\nNormalized Mean:", X_normalized.mean())
print("Normalized Standard Deviation:", X_normalized.std())

np.save("X_normalized.npy", X_normalized)
```

## **PROBLEM B: CUBES DIVISIBLE BY 4 PROBLEM**
- Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 **ndarray** named **C**. Thus, *C* begins with $1^3$ and ends with $100^3$.

- Use a Boolean condition on C to obtain every cubed value divisible by 4. Store the selected values in **div_by_4**. Preserve NumPy's normal row-major selection order.

> **Required Checks**: Display the shape of **C**, the array **div_by_4**, and the number of selected elements. A correct solution has 50 selected elements, the first is **8**, and the last is **1,000,000**.

> **Save the selected array as**: `div_by_4.npy`


### **Code Explanation**: 
- `np.arange(1, 101) ** 3` generates the first 100 positive integers (1 to 100) and cubes each element individually via vectorization.

- `.reshape(10, 10)` transforms the 1D array into a 2D 10 × 10 matrix named `C`.

- `C[C % 4 == 0]` applies a Boolean condition to select only elements with a remainder of zero when divided by 4.

- `np.save('div_by_4.npy', div_by_4)` exports the filtered array to disk.


### **Actual Code**:
```python
import numpy as np

C = (np.arange(1, 101) ** 3).reshape(10, 10)

div_by_4 = C[C % 4 == 0]

print("Shape of C:", C.shape)
print("\nArray div_by_4:\n", div_by_4)
print("\nNumber of selected elements:", div_by_4.size)

np.save("div_by_4.npy", div_by_4)
```

## **PROBLEM C: ABOVE-MEAN SQUARES PROBLEM**

- Create a 6 × 6 **ndarray** named **S** containing the squares of the first 36 positive integers in increasing row-major order. Compute the mean of all elements of S and store it in **S_mean**. Then use Boolean filtering to select only the elements strictly greater than **S_mean**. Store these values in **above_mean**.

> **Required Checks**: Display **S**, **S_mean**, **above_mean**, and the number of selected elements. A correct solution has 15 selected elements, the first is **484**, and the last is **1296**.

> **Save the selected array as**: `above_mean.npy`


### **Code Explanation:**
- `(np.arange(1.37) ** 2).reshape(6, 6)` generates the squares of integers 1 through 36 and shapes them into a 6 × 6 matrix named `S`.

- `S.mean()` computes the average value of all 36 elements in the matrix and assigns it to `S_mean`.

- `S[S > S_mean]` filters out all elements less than or equal to `S_mean`, keeping only values strictly greater than the mean.

- `np.save('above_mean.npy', above_mean)` saves the resulting 1D array to disk.


### **Actual Code**:
```python
import numpy as np

S = (np.arange(1, 37) ** 2).reshape(6, 6)

S_mean = S.mean()
above_mean = S[S > S_mean]

print("Matrix S:\n", S)
print("\nMean (S_mean):", S_mean)
print("\nArray (above_mean):\n", above_mean)
print("\nNumber of selected elements:", above_mean.size)

np.save("above_mean.npy", above_mean)
```

*You have reached the end of this programming assignment. Thank you for reading!*


**Jupyter Notebook File Link**: 

### **README File Version History**:
- August 29, 2026: First draft uploaded.
