### Data

The zip file containing the data for questions 11–20 in this Quiz can be downloaded here:

[Week 1 Quiz Data](https://d396qusza40orc.cloudfront.net/rprog%2Fdata%2Fquiz1_data.zip)

### Question 1
R was developed by statisticians working at  

`The University of Auckland`  

`The R language was developed by Ross Ihaka and Robert Gentleman who were statisticians at the University of Auckland in New Zealand.`  

### Question 2
The definition of free software consists of four freedoms (freedoms 0 through 3). Which of the following is NOT one of the freedoms that are part of the definition?  

`The freedom to prevent users from using the software for undesirable purposes.`  

`This is not part of the free software definition. Freedom 0 requires that the users of free software be free to use the software for any purpose.`  

### Question 3
In R the following are all atomic data types EXCEPT  

`list`  

`'list' is not an atomic data type in R.`  

### Question 4
If I execute the expression x <- 4L in R, what is the class of the object x as determined by the class() function?  

`integer`  

`The 'L' suffix creates an integer vector as opposed to a numeric vector.`  

### Question 5
What is the class of the object defined by the expression x <- c(4, "a", TRUE)?  

`character`  

`The character class is the "lowest common denominator" here and so all elements will be coerced into that class. R does automatic coercion of vectors so that all elements of the vector are the same data class.`

### Question 6
If I have two vectors x <- c(1,3, 5) and y <- c(3, 2, 10), what is produced by the expression rbind(x, y)?  

`a matrix with three columns and two rows`  

`The 'rbind' function treats vectors as if they were rows of a matrix. It then takes those vectors and binds them together row-wise to create a matrix.`  

### Question 7
A key property of vectors in R is that  

`elements of a vector all must be of the same class`  

### Question 8
Suppose I have a list defined as x <- list(2, "a", "b", TRUE). What does x[[2]] give me?  

`a character vector containing the letter "a".`

`x <- list(2, "a", "b", TRUE)`  
`x[[2]]`  
`[1] "a"`  

### Question 9
Suppose I have a vector x <- 1:4 and y <- 2:3. What is produced by the expression x + y?

`an integer vector with the values 3, 5, 5, 7.`  

`x <- 1:4`  
`y <- 2:3`  
`> x + y`  
`[1] 3 5 5 7`

### Question 10
Suppose I have a vector x <- c(3, 5, 1, 10, 12, 6) and I want to set all elements of this vector that are less than 6 to be equal to zero. What R code achieves this?

`x[x %in% 1:5] <- 0`  

` 	You can create a logical vector with the expression x %in% 1:5 and then use the [ operator to subset the original vector x.`  

`x <- c(3, 5, 1, 10, 12, 6)`  
`x[x < 6] <- 0`  
`x`  
`[1]  0  0  0 10 12  6`  

### Question 11
In the dataset provided for this Quiz, what are the column names of the dataset?

`Ozone, Solar.R, Wind, Temp, Month, Day`  

`You can get the column names of a data frame with the names() function.`  

`hw1 = read.csv('hw1_data.csv')`  
`names(hw1)`  
`[1] "Ozone"   "Solar.R" "Wind"    "Temp"    "Month"   "Day"`  

### Question 12
Extract the first 2 rows of the data frame and print them to the console. What does the output look like?


	  Ozone Solar.R Wind Temp Month Day
	1    41     190  7.4   67     5   1
	2    36     118  8.0   72     5   2
	
`You can extract the first two rows using the [ operator and an integer sequence to index the rows.`  

	hw1 = read.csv('hw1_data.csv')
	hw1[c(1,2),]
	
	  Ozone Solar.R Wind Temp Month Day
	1    41     190  7.4   67     5   1
	2    36     118  8.0   72     5   2

### Question 13
How many observations (i.e. rows) are in this data frame?

`153`

`You can use the nrow() function to compute the number of rows in a data frame.`  

	hw1 = read.csv('hw1_data.csv')
	nrow(hw1)
	[1] 153
	
### Question 14
Extract the last 2 rows of the data frame and print them to the console. What does the output look like?

	   Ozone Solar.R Wind Temp Month Day
	152    18     131  8.0   76     9  29
	153    20     223 11.5   68     9  30
	
`The tail() function is an easy way to extract the last few elements of an R object.`

	hw1 = read.csv('hw1_data.csv')
	tail(hw1,2)
	
	    Ozone Solar.R Wind Temp Month Day
	152    18     131  8.0   76     9  29
	153    20     223 11.5   68     9  30

### Question 15
What is the value of Ozone in the 47th row?

`21`  

`The single bracket [ operator can be used to extract individual rows of a data frame.`  

	hw1 = read.csv('hw1_data.csv')
	hw1[15,]
	
	   Ozone Solar.R Wind Temp Month Day
	15    18      65 13.2   58     5  15
	
### Question 16
How many missing values are in the Ozone column of this data frame?

`37`  

`The is.na function can be used to test for missing values.`  

	hw1 = read.csv('hw1_data.csv')
	sub = subset(hw1, is.na(Ozone))
	nrow(sub)
	[1] 37
	
### Question 17
What is the mean of the Ozone column in this dataset? Exclude missing values (coded as NA) from this calculation.

`42.1`  

`The mean function can be used to calculate the mean.`

	hw1 = read.csv('hw1_data.csv')
	sub = subset(hw1, !is.na(Ozone), select = Ozone)
	apply(sub, 2, mean)
	
	   Ozone 
	42.12931 
	
### Question 18
Extract the subset of rows of the data frame where Ozone values are above 31 and Temp values are above 90. What is the mean of Solar.R in this subset?

`212.8`  

`You need to construct a logical vector in R to match the questions requirements. Then use that logical vector to subset the data frame.`  

	hw1 = read.csv('hw1_data.csv')
	sub = subset(hw1, Ozone > 31 & Temp > 90, select = Solar.R)
	apply(sub, 2, mean)
	
	Solar.R 
	  212.8 
	  
### Question 19
What is the mean of "Temp" when "Month" is equal to 6? 

`79.1`

	hw1 = read.csv('hw1_data.csv')
	sub = subset(hw1, Month == 6, select = Temp)
	apply(sub, 2, mean)
	
	Temp 
	79.1
	
### Question 20
What was the maximum ozone value in the month of May (i.e. Month = 5)?

`115`

	hw1 = read.csv('hw1_data.csv')
	sub = subset(hw1, Month == 5 & !is.na(Ozone), select = Ozone)
	apply(sub, 2, max)
	
	Ozone 
	  115
