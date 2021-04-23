# Tableau Bikesharing Analysis

## Project Overview
The purpose of this project is to create a visual business proposal using [Tableau Public](https://public.tableau.com/en-us/s/). Data on Citi bike ridership in New York City is analyzed to determine the business prospects of creating a similar business in Des Moines, Iowa. Pandas DataFrames and Tableau Calculated Fields are used to transform the datatypes and format of some columns.

### Changing the Datatype of "tripduration"
While creating the visualizations necessary for this project, it was found necessary to transform the datatype of the "tripduration" column from an integer to a string. This was accomplished through the following steps:
1. The original CSV data file was read and transformed into a dataframe:
```python
citi_bike_data = "201908-citibike-tripdata.csv"
citi_bike_data_df = pd.read_csv(citi_bike_data)
```
2. The data was converted into the datetime datatype with the following code:
```python
citi_bike_data_df["tripduration(datetime)"] = pd.to_datetime(citi_bike_data_df["tripduration"], unit="s")
```
3. The updated dataframe is exported as a new CSV file without the index:
```python
citi_bike_data_df.to_csv("aug_2019_citibike_data_datetime.csv", index=False)
```

### Correcting the Gender Column 
The column "Gender" was originally formatted as 0, 1, and 2 to identify genders (Unknown, Male, and Female). To have this column correctly print with letters instead of numbers, the datatype of the column is changed to string and the following code was used to create a calculated field: 
```tableau
if [Gender] = '0' then 'UNKNOWN'
ELSEIF [Gender] = '1' then 'MALE'
ELSEIF [Gender] = '2' then 'FEMALE' END
```

## Results 

[Click here to view the completed Tableau business proposal.](https://public.tableau.com/profile/michael.mishkanian#!/vizhome/BikesharingAnalysis_16191255906100/BikesharingAnalysis)

The analysis begins with [general information](https://public.tableau.com/profile/michael.mishkanian#!/vizhome/BikesharingAnalysis_16191255906100/BikesharingAnalysis), which contains a map of the top starting locations for rides in NYC and a pie chart showing the gender distribution of riders. This dashboard is intended to provide a basic overview of the data.

Total user checkout times are then shown, which is then followed by the same graph filtered by gender. This line graph showcased the large disparity in Male and Female ridership.

Total trips by weekday are visualized as a heatmap. The majority of Monday-Friday trips are 7 AM - 9 AM and 5 PM - 7 PM. When filtering this heatmap by Gender, it is again found that Male ridership far outpaces Female ridership. However, the peak riding hours across all genders are similar.

Finally, user trips by gender is visualized. This chart illustrates that users are much more likely to be subscribers, rather than ordinary customers.


## Summary  
In this analysis, it is found that the majority of Citi bike riders in New York City (NYC) identify as **Male**. Additionally, these rides typically begin in **Ubran and densely populated areas**. Bike riding may be an attractive alternative to cars in NYC due to the congested streets and the ease of transportation.

Although this business is popular in NYC due to the heavy traffic, it is not certain that Des Moines will develop the same success. Further research must be done on Des Moines to determine whether car traffic and locational convenience would motivate potential customers to use this service. While NYC has a population density of approximately 27,000 people per square mile, Des Moines only has 2,436 people per square mile. In fact, NYC has nearly 39 times the population of Des Moines.

### Additional Suggestions
In addition to the analysis presented in this Tableau Story, two more visualizations are suggested for future investigation:
1. The top starting and stopping location by gender. This visualization will determine whether there is a gender disparity between the locations were rides begin and end.
2. Usertype percentage by gender should be investigated. If there is a difference between gender and usertype (subscriber vs customer), there could be a more targeted advertisement campagin if this new business is established.

**Author: Michael Mishkanian**   
For all questions and inquiries, please contact me on [LinkedIn](https://www.linkedin.com/in/michaelmishkanian/).
