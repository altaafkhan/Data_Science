### Question 1
The American Community Survey distributes downloadable data about United States communities. Download the 2006 microdata survey about housing for the state of Idaho using download.file() from here:  

[https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv](https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv)  

and load the data into R. The code book, describing the variable names is here:  

[https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf](https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf)  

How many properties are worth $1,000,000 or more?  
53

###### Script  
`## check if directory called data exists. if not then create directory to save data files to`  
`if (!file.exists("data"))`
`   {`
`      dir.create("data")`
`   }`  

`## sets the file url`  
`fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv"`  

`## download file to the data folder`  
`download.file(fileUrl, destfile = "./data/getdata_data_ss06hid.csv")`  

`## data download date recorded`  
`dateDownloaded <- date()`  

`## read the csv file into microData`  
`microData <- read.table("./data/getdata_data_ss06hid.csv", sep=",", header=TRUE)`  

`## count of properties worth $1,000,000 or more`  
`sum(!is.na(microData$VAL[microData$VAL==24]))`  

### Question 2
Use the data you loaded from Question 1. Consider the variable FES in the code book. Which of the "tidy data" principles does this variable violate? 

`Tidy data has one variable per column.`

### Question 3
Download the Excel spreadsheet on Natural Gas Aquisition Program here:  

[https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FDATA.gov_NGAP.xlsx](https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FDATA.gov_NGAP.xlsx)  

Read rows 18-23 and columns 7-15 into R and assign the result to a variable called:  

`dat`  

What is the value of:  

`sum(dat$Zip*dat$Ext,na.rm=T)`  

(original data source: http://catalog.data.gov/dataset/natural-gas-acquisition-program)     

36534720

###### Script  
`## install xlsx package if you haven't already`  
`install.packages("xlsx", dep = T)`  

`## sets the file url`  
`fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FDATA.gov_NGAP.xlsx"`  

`## download file to the data folder`  
`download.file(fileUrl, destfile = "./data/FDATA_gov_NGAP.xlsx")`

`## data download date recorded`  
`dateDownloaded <- date()`  

`## load read xlsx library`  
`library(xlsx)`  

`## set rows 18 - 23`  
`rowIndex <- 18:23`  

`## set columns 7 - 15`  
`colIndex <- 7:15`  

`## read the csv file into data`  
`data <- read.xlsx("./data/FDATA_gov_NGAP.xlsx", sheetIndex=1, header=TRUE, colIndex=colIndex, rowIndex=rowIndex)`

`## calculate sum`  
`sum(data$Zip*data$Ext,na.rm=T)`

### Question 4
Read the XML data on Baltimore restaurants from here:  

[https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml](https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml)  

How many restaurants have zipcode 21231?  

127

###### Script  
`## install xml package if you haven't already`  
`install.packages("XML", dep = T)`  

`## load read xlsx library`  
`library(XML)`  

`## download data`  
`## set the file url`  
`fileUrl <- "http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml"`  

`doc <- xmlTreeParse(fileUrl, useInternal=TRUE)`  
`rootNode <- xmlRoot(doc)`  

`## returns count of restaurants have zipcode 21231`  
`sum(xpathSApply(rootNode, "//zipcode", xmlValue)==21231)`  

### Question 5
The American Community Survey distributes downloadable data about United States communities. Download the 2006 microdata survey about housing for the state of Idaho using download.file() from here:  

[https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv](https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv)  

using the fread() command load the data into an R object  

`DT`  

Which of the following is the fastest way to calculate the average value of the variable  

`pwgtp15`  

broken down by sex using the data.table package? 

DT[,mean(pwgtp15),by=SEX]

###### Script  
`## install data.table package if you haven't already`  
`install.packages("data.table", dep = T)`  

`## load read xlsx library`  
`library(data.table)`  

`## download data`  
`## set the file url`  
`fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv"`  
`download.file(fileUrl, destfile="./data/getdata_data_ss06pid.csv")`  

`## read csv file into DT`  
`DT <- fread("./data/getdata_data_ss06pid.csv")`  

`DT[,mean(pwgtp15),by=SEX]
