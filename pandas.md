# Just enough Pandas to poke yourself in the eye

## Standard Import Pandas 
```Python
import pandas as pd # Follow the norm! It makes your code more reusable.
```

## Reading Data
```Python
df = pd.read_csv(file_path) # Read in the data from 'file_path' and store it in a DataFrame df. 
```

## Data Frame settings-type commands. 
```Python
pd.set_option() # Set's certain options for the pandas environment. 
df.rename() # Can use to rename columns - df.rename(columns={key:val}) where key is the old name 
		    # and val is the new name. 
df.set_index('Column1') # Sets df index to 'Column1'. Supports multiple columns in 
						# a list: ['Column1', 'Column2']. 
df.reset_index('Foo') # Moves index Foo back into data frame as column.
```

## Basic visualization. 
```Python 
df.describe() # Lists summary stats for each variable in the data. 
df.shape # Outputs a tuple of the number of rows and columns in the DataFrame.  
df.columns # Outputs a list of the column names of the DataFrame. 
df.dtypes # Lists the data types of each of the variables in the DataFrame. 
df.head(n) # Show the first n rows of the data. 
df.tail(n) # Show the last n rows of the data. 
```

## Accessing Data. 
```Python
df['Column_Name'] # Pulls 'Column_Name' from data. Try not to put spaces in column names 
				  # if you can help it. There are number of functions where this will save you 
				  # some hassle. 
df.Column_Name # Pulls 'Column_Name' from data (serves same purpose as above). 
df.loc['foo'] # Allows you to access an index with a label - i.e. pull rows where index = 'foo'
df.iloc[n] # Allows you to access an index with a number - i.e. pull row n 
df.ix[] # Allows you to access an index with a number or label. It's primarily label based
	    # but will fall back to integer access unless the corresponding index is integer-based.
```

## Data Work 
```Python
df.groupby(['Column 1', 'Column 2']) # Groups the data by Column1 and Column2. From here, you can 
		   							 # chain any number of methods (sum(), count(), etc.) 
```

## Series Commands
```Python
series.nlargest(n) # Returns the n largest observations from Pandas series variable series. 
series.nsmallest(n) # Returns the n smallest observations from Pandas series variable series. 
```

## Your best friends. 
```Python
df.apply() # Applies a function.operation to a column of a databse. Can be used on the results 
		   # of groupby() and other functions. 
df.eval(string) # Evaluates the string using columns/info. from the database. The most useful time 
				# for this is when creating new columns: df['new_column'] = df.eval('Col1 / Col2')
df.query(string) # Pulls data from the database for which the conditions in 'string' are matched.
``` 
