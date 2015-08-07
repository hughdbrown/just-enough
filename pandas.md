# Just enough Pandas to poke yourself in the eye

## Standard Import Pandas 
```Python
import pandas as pd # Follow the norm! It makes your code more reusable.
```

## Reading Data
```Python
df = pd.read_csv(file_path) # Read in the data from the csv at 'file_path' and store it in DataFrame df. 
df = pd.read_pickle(file_path) # Read in the data from the pickle at 'file_path' and store it in DataFrame df. 
```

## Saving Data 

There are loads of to_x methods on dfs, but these are the ones that I think are most useful. 

```
df.to_dict() # Outputs a nested dictionary from DataFrame df.
df.to_csv() # Outputs a CSV from DataFrame df. 
df.to_pickle() # Outputs a pickle object from DataFrame df. 
df.to_html() # Outputs DataFrame df in HTML format. 
df.to_json() # Outputs DataFrame df in JSON format. 
df.to_sql() # Outputs DataFrame df in SQL format. 
df.to_excel() # Outputs DataFrame df in excel format. 
```

## Data Frame settings-type commands. 
```Python
pd.set_option() # Set's certain options for the pandas environment. 
df.rename() # Can use to rename columns - df.rename(columns={key:val}) where key is the old name 
		    # and val is the new name. 
df.set_index('Column1') # Sets df index to 'Column1'. Supports multiple columns in 
						# a list: ['Column1', 'Column2']. 
df.reset_index('Foo') # Moves index Foo back into data frame as column. Will throw all levels of 
					  # of the index into the df if left empty. 
```

## Basic visualization. 
```Python 
df.describe() # Lists summary stats for each variable in the data. 
df.shape # Outputs a tuple of the number of rows and columns in the DataFrame.  
df.columns # Outputs a list of the column names of the DataFrame. 
df.index # Outputs a list of the indicies of the DataFrame. 
df.dtypes # Lists the data types of each of the variables in the DataFrame. 
df.head(n) # Show the first n rows of the data. 
df.tail(n) # Show the last n rows of the data. 
```

## Accessing Data. 
```Python
df['Column_Name'] # Pulls 'Column_Name' from data. Try not to put spaces in column names 
				  # if you can help it. There are number of functions where this will save you 
				  # some hassle. This returns a Pandas Series. 
df.Column_Name # Pulls 'Column_Name' from data (serves same purpose as above), and returns 
		       # a Pandas Series. 
df.Column_Name.values # Pulls 'Column_Name' from data, but returns a numpy array. The .values 
				      # also works when accesing columns through brackets (i.e. df['Column_Name']).
df.loc['foo'] # Allows you to access an index with a label - i.e. pull rows where index = 'foo'
df.iloc[n] # Allows you to access an index with a number - i.e. pull row n 
df.ix[] # Allows you to access an index with a number or label. It's primarily label based
	    # but will fall back to integer access unless the corresponding index is integer-based.
	    # This also allows you to access a column - df.ix[:, 'Column1']. 
```

## Data Work 
```Python
df.groupby(['Column1', 'Column2']) # Groups the data by Column1 and Column2. From here, you can 
		   							 # chain any number of methods (sum(), count(), etc.) 
df.sort(['Column1','Column2']) # Returns the DataFrame df sorted first by column1 and then column2.								  # 								   # Note if you want to sort in place you need to set inplace = True. 
df.drop('Column1', inplace=True) # Drop column1 from DataFrame df, inlace. If inplace=False, then it 
								 # returns a new DataFrame with the column dropped, and the original 
								 # DataFrame df remains unchanged. 
df1.join(df2) # Join df1 to df2 on the index/indicies (must be the same). Returns a new joined 	
			  # DataFrame.
pd.merge(df1, df2, on='column') # Merged df1 and df2 by 'column'. Returns a new merged DataFrame. 
```

## Series Commands
```Python
series.nlargest(n) # Returns the n largest observations from Pandas series variable series. 
series.nsmallest(n) # Returns the n smallest observations from Pandas series variable series. 
series.value_counts() # Returns the count of each of the unique values from Pandas series variable 
					 # series. 
series.sort()  # Sorts the series in ascending order. Note if this is a column from a dataframe
			   # you must make a copy first. 
```

## Your best friends. 
```Python
df.apply() # Applies a function.operation to a column of a databse. Can be used on the results 
		   # of groupby() and other functions. 
df.eval(string) # Evaluates the string using columns/info. from the database. The most useful time 
				# for this is when creating new columns: df['new_column'] = df.eval('Col1 / Col2')
df.query(string) # Pulls data from the database for which the conditions in 'string' are matched.
``` 

## Other random commands. 
```Python
dummies = pd.get_dummies(df['Category']) # Returns dummy variables for the column 
										 # 'Category' from the df. 
```
