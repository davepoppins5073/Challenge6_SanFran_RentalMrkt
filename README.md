# Challenge6_SanFran_RentalMrkt

## Requirements/ Installations
The requirement.txt file in this repository contain all the packages you'll need in your conding env. Please make sure to install if you do not have them already. While you could use the package manager [pip](https://pip.pypa.io/en/stable/) to install these individually please make use of the requirement text in the repo.

### pip install for Requirements
```bash
python -m pip install -r requirements.txt
```
### Imports
```python
# Import the required libraries and dependencies
import pandas as pd
import os 
import glob
import hvplot.pandas
from pathlib import Path
```
## FUNCTIONS
1. csv_path_builder()
2. csv_to_dataframe()


```python
def csv_path_builder():
    
    """
    The goal of is the print out the csv data files that we will turn into
    dataframes for the subsequent analyses
    
    """
    
    # It all starts with the working directory
    dir_fl = os.getcwd()
    p = Path(dir_fl)
    all_files = []
    
    for i in p.glob('**/Resources/*.csv'):    #'**/*.csv'
        all_files.append((i.name))
    
    return(all_files)

```
```python
def csv_to_dataframe(file_path=str):
    
    """
    This function will take the file path to a csv file and turn it
    into a dataframe
    """
    
    #Initializing Variables & Such
    df_data = pd.DataFrame()
    path = file_path
    
    # Creating the Dataframe
    df_data = pd.read_csv(path)

    return(df_data)
 ```

# CODE 
The code is well documented and as it's a commented notebook you can follow the code. However there are few things I wanted to showcase.

### for-loop
For the sake of iterating and improving my code I created and did the following. basically this is close to being a function that will determine if there are any csv in the directory (it will check not jsut the folder where the script is at it will check subdirectories as well and it will take the names of the files there and and using the file path created dataframes beaing their names. It might format the columns to a way I prefer. Either way this is very close to what I want and a few more iterations it will be my very own desktop datascrapper.


<img width="1093" alt="Screen Shot 2022-05-01 at 10 56 29 PM" src="https://user-images.githubusercontent.com/101449950/166180307-acfb4fce-2983-4bf9-8152-6d20d3b5950d.png">

### GRAPHS:

#### Bar Graph
```python
housing_units_by_year.hvplot.bar(
    x='Year',
    y='Housing_Units',
    ylim = (365000, 385000),
    hover_color='pink',
    title="Housing Units in San Fran 2010 - 2016"
).opts(
    width=700,
    yformatter='%.0f',
    color="yellow",
    bgcolor="gray",
    fontsize={
        'title': 15, 
        'labels': 12, 
    'xticks': 10, 
    'yticks': 10,},
    padding=0.1
)

```

<img width="745" alt="Screen Shot 2022-05-01 at 11 04 52 PM" src="https://user-images.githubusercontent.com/101449950/166179578-952744bd-3d81-44c6-9617-a1c1a967afee.png">



#### Graph with Widet
```python
# Use hvplot to create an interactive line plot of the average price per square foot
# The plot should have a dropdown selector for the neighborhood
prices_by_year_by_neighborhood.hvplot.line(groupby='Neighborhood').opts(
    width=620,
    bgcolor="lightgrey",
    yformatter='%.0f',
    legend_position='right',
    legend_offset=(0, 50)
).opts(
    width=725,
    yformatter='%.0f',
    legend_position='right',
    legend_offset=(0, 50)
)
```
<img width="1093" alt="Screen Shot 2022-05-01 at 10 56 29 PM" src="https://user-images.githubusercontent.com/101449950/166179140-eb92a922-400b-4325-84ac-3a43253626ca.png">

#### Interactive Plots
```python
all_neighborhoods_df.hvplot.points(
    'Lon', 
    'Lat', 
    geo=True, 
    size = 'Sale_Price_SQR_Foot',
    color='Gross_Rent',
    tiles='OSM',
    frame_width = 700,
    frame_height = 500,
    hover_cols = 'Neighborhood',
    tools=[HoverTool(tooltips=
        [('Gross Rent','@Gross_Rent{1.11}'),
         ('Sale Price sq/ft','@Sale_Price_SQR_Foot{1.11}'),
         ('Neightborhood','@Neighborhood')])],
    title='San Franscisco Neighborhood Interactive Map: Gross Rent, Sale Price sq/ft '
).opts(
    xlabel="Longitude",
    ylabel="Latitude",
)
```
    

<img width="928" alt="Screen Shot 2022-05-01 at 10 53 59 PM" src="https://user-images.githubusercontent.com/101449950/166178928-f731ff75-d9cf-4eb1-8882-ba2983c259bb.png">








## Answers/Data Story

### Question 1

In the six years from 2010 to 2016, the total housing units increased from 372560 to 384242. That's a net change of 11,682 units in 6 years, about an increase of 1947 units per year. In that same time frame, the gross rent increased from $1239/per month to $4390. The average sales_price per square foot changed by about $51/year or $4.25 per month. The San Francisco rental market from 2010 to 2016 presented real estate investors with a legitimate financial opportunity. The price of acquisition (389.34 - 697.64) per sq foot) didn't increase as drastically (1.7 times roughly as the monthly rents did compare to 3.5 times).

### Question 2

The lowest gross_rent was $1239 and that was reported in 2010.

### Question 3

In 2011 sales price/ sq ft decreased from $369.34 the year before to $341.90. The rent still increaes that year to $1530 up from the prior years $1239

### Question 4

From Anza Vista the Avg sales price /sq ft was $88.40, down from $344.49 in 2012.

### Question 5

Westwood Park => Gross Rent: 3959 (max value) Union Sq District Sales Price: 903.99 (max value)

### Question 6

Looking at all the neighborhoods that comprise, the San Francisco rental market from 2010 to 2016 as a whole, real estate investors had a legitimate financial opportunity. The price of acquisition (389.34 - 697.64) per sq foot) didn't increase as drastically (1.7 times roughly as the monthly rents did compare to 3.5 times).

While all neighborhoods saw increases in gross rent not all of the sales_price per sq ft increased the same. there are sstill neightborhood where I would encourage investment like Forest Knolls. The gross rent there is in the 1700 nd the sales price per sq ft $321. I dont think in a city as large as San francisco, all gross_Rent will increase at the same rate.In other words overall trends dont apply to every consituent place the same. I dont have 2016 Present day data so I wouldnt recommend anything until I see this data
