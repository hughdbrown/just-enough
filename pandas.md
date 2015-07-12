# Just enough Pandas to poke yourself in the eye

## Import Pandas 
```Python
import pandas as pd
```

## Reading Data
```Python
df = pd.read_csv(file_path) # Read in the data from 'file_path' and store it in a DataFrame df. 
```

## Data Frame settingsish commands. 
```Python
pd.set_option() # Set's certain options for the pandas environment. 
df.rename() # Can use to rename columns - df.rename(columns={key:val}) where key is the old name 
		    # and val is the new name. 
df.set_index('Column1') # Sets df index to 'Column1'
df.reset_index('Foo') # Moves index Foo back into data frame as column. 
```

## Basic visualization. 
```Python 
df.describe() # Lists summary stats for each variable in the data. 
df.shape # Outputs a tuple of the number of rows and columns in the DataFrame.  
df.columns # Outputs a list of the column names of the DataFrame. 
df.dtypes # Lists the data types of each of the variables in the DataFrame. 
df.head(#) # Show the first # rows of the data. 
df.tail(#) # Show the last # rows of the data. 
```

## Accessing Data. 
```Python
df['Column_Name'] # Pulls 'Column_Name' from data. Try not to put spaces in column names 
				  # if you can help it. There are number of functions where this will save you 
				  # some hassle. 
df.Column_Name # Pulls 'Column_Name' from data (serves same purpose as above). 
```

## Data Work 
```Python
df.groupby(['Column 1', 'Column 2']) # Groups the data by Column1 and Column2. From here, you can 
		   							 # chain any number of methods (sum(), count(), etc.) 
```

## Series Commands
```Python
series.nlargest(n) # Returns the n largest observations from variable series. 
series.nsmallest(n) # Returns the n smallest observations from variable series. 
```

## Your best friends. 
```Python
df.eval(string) # Evaluates the string using columns/info. from the database. The most useful time 
				# for this is when creating new columns: df['new_column'] = df.eval('Col1 / Col2')
df.query(string) # Pulls data from the database for which the conditions in 'string' are matched.
``` 
