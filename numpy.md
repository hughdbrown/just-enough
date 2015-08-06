# Just Enough numpy to poke yourself in the eye

## Standard numpy import
```Python
import numpy as np # Follow the norm! It makes code more reusable. 
```

## Load .txt with numpy
```Python
loaded_txt = np.loadtxt('path') # Loaded_txt now holds the .txt file located at 'path'
```

## Creating Arrays
```Python
mat = np.array([[4, -5], [-2, 3]]) # Create a 2 x 2 matrix with given values. 
row_vect = np.array([-13, 9]) # Create a row vector with given values. 
column_vect = np.array([[13], [9]]) # Create a column vector with given values. 

row_vect = np.array(i_array) # Create a row vector from array variable i_array.
column_vect = np.array(i_array).reshape(len(i_array), 1) # Create a column 
														 # vector from array variable
														 # i_array. 
mat = np.array(i_array).reshape(m, n) # Create a matrix with m rows and n columns from 
									  # array variable i_array.
feature_mat = df.values # Create a feature matrix with the data values from dataframe df 
						# (This is effectively just an m x n matrix where m is the number of
						# obs in your df and n is the number of variables). 

np.zeros(m,n) # Create a matrix of zeros with m rows and n columns. 
np.ones(m,n) # Create a matrix of ones with m rows and n columns.
np.identity(n) # Create an identity matrix with n rows and n columns.  
```

## Creating Matricies 

These have some different methods/properties than numpy arrays. They are two different
kinds of objects. 

```Python
np.matrix(i_array) # Create a numpy matrix from variable i_array. 
```

## Useful methods of arrays/matricies. 
```Python
.mean(axis = 0/1) # Calculates the mean of the array/matrix, or by columns if axis = 0 and rows 
				  # if axis = 1. 
.std(axis = 0/1) # Calculates the standard deviation of the array/matrix, or by columns if 
				 # axis = 0 and rows if axis = 1. 
.shape() # Returns the shape of the matrix in a tuple: (m, n): m is the # rows and n # columns. 
.transpose() # Returns the transpose of the array/matrix. 
.T # Also returns the transpose of the array/matrix. 
.reshape(m, n) # Reshapes the array/matrix to have m rows and n columns. 
```

## Indexing - suppose A is a 4 x 3 matrix, and remember indexing starts at 0.
```Python
A[1, 2] # Get the element at row 1, column 2. 
A[1][2] # Another way of getting the element at row 1, column 2.
A[1] # Get row 1. 
A[:, 1] # Get Column 1. 
A[0:2, 1:3] # Get elements from rows 0-1 and columns 1-2.
```

## Matrix Math 

Assume A and B are both 2-D numpy arrays, and d is a scalar. If we are going element-wise here, A and B must have 1-dimension in common. If we are doing matrix multiplication or getting the inner/dot product, then A must have the same number of columns as B does rows. 

```Python
C = A [+ -] d # Add/Subtract d to each element in A.
C = A [ * /] d # Multiply/Divided each element in A by d. 
C = A [+ -] B # Perform element-wise addition/subtraction between A and B. 
C = A [* /] B # Perform element-wise multiplication/division between A and B. 
C = np.dot(A, B) # Perform matrix-multplication/get the inner/dot product between A and B.
C = A ** n # Raise every element in A to the nth power. 
C = np.linalg.matrix_power(A, n) # Raise the square matrix A to the nth power. This is 
								 # different than simply raising each element to the nth power. 
``` 

Now assume that A and B are both numpy matricies. 

```Python
C = A * B # Perform matrix-multplication/get the inner/dot product between A and B.
C = A ** n # Raise the square matrix A to the nth power. This is 
		   # different than simply raising each element to the nth power. 
```

## Useful numpy functions. 

```
np.argsort(C) # Return the indicies of sorted elements in C. This returns the same shape as 	
			  # C, sorting within rows if axis argument is not passed in. Sorts within rows if 
			  # axis = 1, within columns if axis = 0. 
np.column_stack((A, B)) # Stack arrays/lists A and B as columns. A and B must have the same 
						   # number of rows. 
np.argmax(A) # Returns the index/indicies of the maximum element in A. This returns the index 
			 # of the maximum element in A if no axis is specified (where indicies are counted
			 # sequentially across rows and down columns if A is 2D). If axis is 0, it returns
			 # the max index within columns, and within rows if axis = 1. 
np.argmin(A) # The min. analog of np.argmax(). 
np.ravel(A) # Flattens any 2-D array into 1-D. 
np.random.choice(A, 10, replace = False) # Select 10 random elements from A, without replacement.  
np.where(A == 0) # Returns the indicies where the values in the numpy array/matrix A are equal to 0. 
np.delete(A, [1, 2, 3]) # Deletes the elements at the indicies 1, 2, 3 from the 1-D numpy array A. 
						# This works on matricies and 2-D arrays as well; just be careful to pass it 
						# the right indicies and/or specify which axis to delete from. 
```



