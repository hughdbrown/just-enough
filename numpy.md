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

## Useful methods
```Python
.mean(axis = 0/1) # Calculates the mean of the entire array, or by rows if axis = 0 and columns 
				  # if axis = 1. 
.std(axis = 0/1) # Calculates the standard deviation of the entire array, or by rows if axis = 0
				 # and columns if axis = 1. 
.shape() # Returns the shape of the matrix in a tuple: (m, n): m is the # rows and n # columns. 
.transpose() # Returns the transpose of the matrix. 
.reshape(m, n) # Reshapes the matrix to have m rows and n columns. 
```

## Indexing - suppose A is a 4 x 3 matrix, and remember indexing starts at 0.
```Python
A[1, 2] # Get the element at row 1, column 2. 
A[1][2] # Another way of getting the element at row 1, column 2.
A[1] # Get row 1. 
A[:, 1] # Get Column 1. 
A[0:2, 1:3] # Get elements from rows 0-1 and columns 1-2.
```