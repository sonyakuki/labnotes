#Foundations
##Dogs of NYC Homework 
### Lab Notes 

#### 1. How many dogs are registered in NYC?

*First, I need to retrieve the csv data file using the **urllib** function and **urlretrive** method:*

+ import urllib

then use  --> urllib.urlretrieve("[URL of the CSV data file]" , "[whatever I want to then name the file]") so: 

+ urllib.urlretrieve("http://jonathansoma.com/lede/dogs.csv", "dogsnyc.csv")

I retrieved the data and named this CSV file "dogsnyc.csv".  Now I need to import the CSV:

+ import csv

Now I need to open it using csv.reader: 

+ with open('dogsnyc.csv', 'rb') as csvfile:
+ (*indent*) dogsnyccsv = csv.reader(csvfile, delimiter = ',')

Then I need to convert this information from the CSV into a list that I will call dogs_list:

+ (*indent*) dogs_list = list(dogsnyccsv) 

Keeping in mind that the first row of data is the header row (and not an actual data entry or in this case, a dog) I need to subtract 1 from the total number of rows of data(dogs in the list) to get the total amount of dogs that are registered in NYC:

+ (*indent*) print len(dogs_list) - 1 

**The total number that is returned is 81542. This is how many dogs are registered in NYC**

####2. How many dogs are registered in Brooklyn? Staten Island? Queens? Manhattan? Bronx? 

Focus first on finding how many dogs registered in Brooklyn, use variable brooklyn. Set brooklyn to 0 initially: 

+ brooklyn = 0 

Now need a for loop to run through every row of data in (row of data is a dog in this case so instead of row, write dog) in the list dogs_list:

+ for dog in dogs_list: 

Narrowing our search down more, we want to know specifically about the the 9th column of data in each row which we know to be what borough the dog lives in, use: if dog[9]; and use "==' because we are testing something; and since we are looking specifically for Brooklyn, that is what we set it equal to: 

+ (*indent*) if dog[9] == "Brooklyn": 

Remember that we are creating a variable "brooklyn" to count how many dogs are registered in Brooklyn (it's the count!). (*We do "brooklyn + 1" because we know the way the computer counts, it starts with a 0 so we need to add 1 to get an accurate count*): 

+ (*indent+indent*) brooklyn = brooklyn + 1

To see how many dogs there are in Brookyln: 

+ print brooklyn 

Or if you want to be fancy, you can do this (remember to convert brooklyn to a string in the process):

+ print "Number of Registered Dogs in Brooklyn: " + str(brooklyn)

And it will return a full sentence: 

+ Number of Registered Dogs in Brooklyn: 19333

**Do exactly the same process for all the other boroughs!**

The answers are: 

+ Staten Island: 9381
+ Manhattan: 26029
+ Queens: 17506
+ Bronx: 9293


####3. How many dogs are named Max in the Lower East Side? 

First, we determine that we will use zip codes to define the LES. The LES includes the following zip codes: 10002, 10003, 10009. 

So we know that we will need to use these zip codes for our search parameters. 

Since we are looking for dogs named Max, let's use the variable "max". The first step: 

+ max = 0

Now we use a for loop to search through each row of data (dog) in the list dogs_list:

+ for dog in dogs_list:

We are looking through each row of data for the info in the very first, or 0th, column. So we use dog[0] and == because we are testing

+ (*indent*) if dog[0] == "Max" 

BUT THAT'S NOT ALL!!! 

We are not just looking for dogs named Max, but dogs named Max that live in the LES so we need to use "and" to connect the name and zip code (the dog[10] column)

+ (*indent*) if dog[0] == "Max" and (dog[10] == "10002") 

STILL NOT DONE…

But since we are looking at more than just one zip code we need to *also* use "or" in the second part for each zip code: 

+ (*indent*) if dog[0] == "Max" and (dog[10] == 
""10002" or dog[10] = "10003" or dog[10] = "10009"):

Then of course, remembering that the count starts with 0, we need to do this: 

+ (*indent+indent*) max = max + 1

+ print max

**The answer is 33.**

Alternatively you could have first made a list of the LES zip codoes: 

+ les = ["10002", "10003", "10009"]

Run it and then enter it in this row of the for loop: 

+ if dog[0] = "Max" and (dog[10] in les):

####4. How many dogs are named Max in Bed Stuy?

Let's first make a list called "bedstuy" of all the zip codes that Bed Stuy encompasses: 

+ bedstuy = ["11205", "11206", "11216", "11221", "112333"]

Let's make a new variable called "max_bedstuy" to find what we are looking for in particular, and set it to 0 first: 

+ max_bedstuy = 0 

Now a for loop like number 3:

+ for dog in dogs_list:
+ (*indent*) if dog[0] == "Max" and (dog[10] in bedstuy):
+ (*indent+indent*) max_bedstuy = max_bedstuy + 1
+ print max_bedstuy 

**The answer is 22.**

####5. How many dogs have the color brindle as their first or second color?

The variable name for what we are looking for will be "brindle_dogs":

+ brindle_dogs = 0 

Now a for loop (brindle has to be in all caps for this to work, not sure why):

+ for dog in dogs_list: 

We want to know if brindle shows up in the data column of first or second column which are the (starting from 0) 4th and 5th column. Since we are looking at more than one, we use [4:6] because this counts 4 and 5, but not 6 (only up until 6 but not including 6):

+ (*indent*) if "BRINDLE" in dog[4:6]:

+ (*indent+indent*) brindle_dogs = brindle_dogs + 1
+  print brindle_dogs

**The answer is 3606.**

####6. How many dogs are named Sonya? 

Variable will be "sonya_dogs": 

+ sonya_dogs = 0 

For loop: 

+ for dog in dogs_list: 
+ (*indent*) if dog[0] == "Sonya":
+ (*indent+indent*) sonya_dogs = sonya_dogs + 1
+ print sonya_dogs 

**The answer is 7.**







