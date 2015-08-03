# Just Enough mongodb to poke yourself in the eye

## Getting Up and Running. 
```
mongod # Start mongo terminal. 
mongo # Open up mongo shell. 
```

Once you have a shell open... 
```
show dbs # Show all available databases. 
use clicks # Log in/use database clicks. 
```

## Basic Database/collection info. 
```
db.printCollectionStats() # Prints out stats for all collections in the current db. 
```

## Querying Basics
```
db.log.find()	# Return all documents from the log collection in the current db. 
db.log.find().limit(10) # Return the first 10 documents from the log collection in the 
						# current db. 
db.log.findOne() # Return the first document from the log collection in the current db. 
db.log.find({cy : 'San Francisco'}) # Return all documents from the log collection in the 
									# current db where field cy is equal to San Francisco. 
db.log.distinct('a') # Return all distinct values for the field 'a' from the log collection 
					 # in the current database. 
```

## Query Result 'Methods' (Things you can apply to a query result to get cool facts)
```
.length[()] # Return the length/number of documents from that query. Parens are sometimes required.
.count() # Return the length/number of documents from that query.
```