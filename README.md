# Bikesharing Analysis (Tableau)

## Project Overview
The purpose of this project is to create a visual business proposal using Tableau. Data on Citi bike ridership in New York City is analyzed to determine the business prospects of creating a similar business in Des Moines, Iowa. Pandas DataFrames and Tableau Calculated Fields are used to transform the datatypes and format of some columns.

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
The column "Gender" was originally formatted as 0, 1, and 2 to identify genders. To have this column correctly print with letters instead of numbers, the datatype of the column is changed to string and the following code was used to create a calculated field: 
```tableau
if [Gender] = '0' then 'UNKNOWN'
ELSEIF [Gender] = '1' then 'MALE'
ELSEIF [Gender] = '2' then 'FEMALE' END
```

## Results 

[Click here to view the completed Tableau business proposal.](https://public.tableau.com/profile/michael.mishkanian#!/vizhome/BikesharingAnalysis_16191255906100/BikesharingAnalysis)




## Summary  
In this analysis, it is found that the majority of citi bike riders in New York City (NYC) identify as Male. Additionally, these rides typically begin in Ubran and densely populated areas. Bike riding may be an attractive alternative to cars in NYC due to the congested streets and the ease of transportation.


**Author: Michael Mishkanian**   
For all questions and inquiries, please contact me on [LinkedIn](https://www.linkedin.com/in/michaelmishkanian/).
