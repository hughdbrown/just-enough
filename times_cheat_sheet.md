# Times Cheat Sheet 

This sheet is meant to provide you with some tips/tricks/notes for working with time objects in Python. At the end of the day, working with time objects is just tricky - you can get them in loads of different formats, they don't often place nice across languages, etc. In that regard, this sheet probably won't provide one-size-fits all solutions, but aims to help guide you along your time object journey. 

## Time Formats 

Often times, we'll get time data in one of several formats: 

1. *epoch time* - this is defined as the number of seconds that have elapsed since midnight on January 1st, 1970 in Universal Coordinated Time. It's also sometimes referred to as *POSIX* or *Unix* time. Time data coming in this format comes as extraodinarily large numbers. 
2. *string format* - these are just strings that correspond to an actual date, and can take on pretty much any format you could think of: 
    - '1970-01-01' (Year-Month-Day)
    - '01-01-1970' (Day-Month-Year)
    - '1970-01-01 00:00:00' (Year-Month-Day Hours:Minutes:Seconds)
    - '01/01/1970 00:00:00' (Day/Month/Year Hours:Minutes:Seconds)  
3. *date object* - these can take on a number of different formats, and will depend on where exactly you're pulling the data from (a SQL database, Mongo database, serialized object, etc.) 

When working with `1`, we don't have to think of the particular time-zone that the date is in, whereas with `2` or `3` we might. With `2`, we have a much higher likelihood that we have to figure out what timezone the data corresponds to, and then make sure to tell our program that as well. Date objects (`3`) often have a time-zone already associated with them, but be careful to double check this! Often times, the time-zone will just default to UCT. 

## Workflow 

When I work with time objects, the general workflow I follow is: 

1. Figure out how the time data is stored - is it `1`, `2`, or `3` from above? If it's neither, then can I figure out what it is?  
2. Figure out what format I need to get that data in. Often times, I want to get it to match the date type of some other time data that I have. If that's not the case, but I will want to be comparing it some pre-specified date (e.g. take all rows that are less than May 29th, 2015), then I'll convert it to my go-to format.   
3. Convert the time data to the format determined in `2`.  
4. Perform any calculations that I need to do, iterating over `2` and `3` if I need to convert formats or figure out that the format I originally chose in `2` isn't quite working like I expect. 

## Workflow Examples 

### Time data stored as `epoch` times

1. **Figure out how the time data is stored**: 
 
 Typically, I assume that my time data is stored as `epoch` times if I obtain data that I'm told is time data, and the values are all in the millions (or greater). If I have an idea of roughly what dates these `epoch` times should correspond to, then I'll go find some [epoch time calculator](http://www.epochconverter.com/) and paste one of the values in. This calculator will take your `epoch` time and convert it to a human readable format. 

 For example, putting in the `epoch` time of `1464014493` gives back the human readable format of `Mon, 23 May 2016 14:41:33 GMT`. If I put in an `epoch` time and it corresponds to a rough date that I was expecting, I move forward as if my data is `epoch` times. 

2. **Figure out what format I need to get the data in**: 
 
 Let's assume that I want to get this to a Python `datetime.datetime` object. This happens to be one of the Python date classes that I find most intuitive, easiest to work with, and the one I'm most familiar with (this is stricly my opinion, though - there might very well be better date classes to work with). 

3. **Convert the time data to the format determined in `2`**: 

 * `datetime.datetime.fromtimestap` takes an `epoch` time, and returns the **local** time corresponding to that `epoch` time (e.g. it reads that `epoch` time as if it corresponded to the **local** time that your computer is set to) 
    * If we have an epoch time of `1464014493` (the one from above), we can convert it by typing: 
    
     ```
     from datetime import datetime
     datetime.fromtimestamp(1464014493) 
     ```

     This will return `datetime.datetime(2016, 5, 23, 9, 41, 33)`, which corresponds to `2015-05-23 9:41:33`. Notice that this is 5 hours behind what we got back from the [epoch time calculator](http://www.epochconverter.com/), which corresponds to the fact that Austin (where I am current at) is 5 hours behind the `GMT` timezone. 

4. **Perform any calculations that I need to do**

I'm going to punt on this until we walk through the three ways we might obtain time data. Once we get it in the format we want, then working with it any performing calculations will all use roughly the same code. 
