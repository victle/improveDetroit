# improveDetroit
Exploratory Data Analysis of the Improve_Detroit_Issues dataset, with some initial modeling:
Code is found in the notebooks of the repository. Summary if the insights are below. 
![image](https://user-images.githubusercontent.com/26015263/115037781-d2950380-9e9c-11eb-93e4-b6956a57e6b2.png)

[Visualizations](#visualizations)

[Modeling](#modeling) 

# Project Goals
* Characterize what data is included
* Inform some of the questions that we can and should ask // What can this data tell us? 
* Perform some basic modeling of the data

# Loading data 
## Packages 
Only the basics are needed:
* Numpy
* Pandas 
* Matplotlib
* Sci-kit learn 

## Data
The data itself can be found at [this link](https://data.detroitmi.gov/datasets/improve-detroit-issues?geometry=-87.321%2C41.470%2C-82.140%2C42.894).
Data description: 
> Issues submitted through the Improve Detroit mobile app. Improve Detroit is a 311 ticketing system used by many City departments and agencies to manage resident requests.

Columns of the data include the (lat, long), status of the issues, short descriptions of the issues, the neighboorhoods, and the timestamp data of when issues were opened, closed, and updated. For the following visualizations, we'll be primarily interested in geospatial data. 

# Visualizations 
<details>
  <summary>Location of the issues</summary>

  ## Scatter plot of all the issues with location data 
  ![image](https://user-images.githubusercontent.com/26015263/115037781-d2950380-9e9c-11eb-93e4-b6956a57e6b2.png)

  ## Open issues are more frequently found in the southwestern neighborhoods of Detroit 
  ![image](https://user-images.githubusercontent.com/26015263/115038453-8e563300-9e9d-11eb-801e-abc4053257d2.png)
</details>

<details>
  <summary>Do the issues depend on the types of requests?</summary>
  
  ## Some of the most frequent requests are reported by public city departments, so let's look at just citizens' reports
  ![image](https://user-images.githubusercontent.com/26015263/115038732-ceb5b100-9e9d-11eb-9660-09ea276b8ff8.png)

  ## The location of the most common issue, __Illegal Dump Sites__, shows similar density 
  ![image](https://user-images.githubusercontent.com/26015263/115038881-f1e06080-9e9d-11eb-95ce-f04ca8611302.png)

  ### Another frequently reported issue, __Tree Issue__, tells us a different story
  ![image](https://user-images.githubusercontent.com/26015263/115039004-0f152f00-9e9e-11eb-8a0b-e940fa3dc41c.png)

This seemingly points to the idea that the southwestern neighborhoods of Detroit being more urban and dense. Evidently, there is still a lot more to explore. One of the main insights here is that the most common issues are reported in the lower left corner of Detroit. Consequently, a majority of the issues still left Open are found in that area. More exploration needs to be done to determine whether that is on part of the department or the citizens reporting it. Something interesting to look at would be the time it takes to close issues, and the shortest times by neighboorhood.

</details>

# Modeling 
<details>
  <summary>Does the time it take to close issues vary by month?</summary>

![image](https://user-images.githubusercontent.com/26015263/115039629-a084a100-9e9e-11eb-99cd-2337d3829482.png)

Clearly it pays to look at the data before modeling! There is a seemingly obvious quadratic fit. Let's try again.

![image](https://user-images.githubusercontent.com/26015263/115039770-c14cf680-9e9e-11eb-86ec-1b8286ab1ba8.png)

Much better, and we're getting a pretty decent R-squared term as well. Evidently, there's a concave down relationship between month and time it takes to close issues. This seems counterintuitive, as I would assume that holiday months (later in the Fall and early Winter) would be when it takes issues longest due to fewer staff. However, it seems like the summer months take the absolute longest, with June take even more than a month to close.

Yet, this does not tell the full story, as the amount of time it takes to close may very well depend on the types of issues that show up during the year. The next step is to figure out what kinds of issues appear during which months.

</details>
