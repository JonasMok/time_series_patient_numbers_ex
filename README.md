# Explatory exercise using time series methods to predict the number of patients in a local walk-in health centre. 
This repositoy register the main results obtained during a explatory exercise of forecasting using R. I applied time series methods to identify any pattern in the data of a local walk-in health centre. Then, I selected the best models to predict the number of patients. The original exercise was part of an assingment that I have done during my MSc course. 

## Getting Started
It is necessary to download the dataset avaliable in this repository: [TimeSeries_example](TimeSeries_example.xlsx). This file is a fictional dataset built to practise time series methods. The period cover by dataset is from 01/04/15 to 31-03-19. 

### Prerequisites

What things packages and libraries you need to install

```
#To import excel file
install.packages("readxl")
library(readxl)

#Work with Date and times
install.packages('lubridate')
library('lubridate')

#Basics stats
install.packages('pastecs')
library('pastecs')
install.packages('DescTools')
library('DescTools')

#Graphics
install.packages('fpp2')
library('fpp2')

```

## Data analysis

Is there any pattern in the daily number of patients at a local walk-in centre?  

We can start plotting a graph and making some basic statistics to figure out which kind of dataset we are working.
```
#Import the file to R including the correct path where you save the file
TimeSeries_example <- read_excel("TimeSeries_example.xlsx")

#saving as time series object
dt_1 <- ts(TimeSeries_example[,2],start = decimal_date(as.Date("2015-04-01")), frequency = 365)

#plot the first graph to visualise which kind of data we are working
plot(dt_1, main="Number of patients per day", sub="01 April 2015 - 31 March 2019", col = 'Blue', xlab="Year", ylab="number of Patients")

```
![Basic graph](basic_graph_v2.png)

... and the basics statistics 

```
stat.desc(dt_1)
mean(dt_1)
median(dt_1)
mean(abs(dt_1-mean(dt_1)))
mean((dt_1-mean(dt_1))^2)
var(dt_1)
sd(dt_1)
min(dt_1)
max(dt_1)
```

- Data Period: 01/04/15 – 31-03-19;
- Number of Obervations (days): 1,461;
- Mean: 46.72 / Mean abs. Dev.: 9.94 / Mean Sqd dev: 166.57 / Variance: 166.69 / St.dev: 12.91 / Mininum: 16 and Maximum: 97

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system


## Authors

* **Jonas Okawara** 

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## References

Hyndman, R.J., & Athanasopoulos, G. (2018) Forecasting: principles and practice, 2nd edition, OTexts: Melbourne, Australia. OTexts.com/fpp2. Accessed on <26/05/2020>. link: https://otexts.com/fpp2/index.html
