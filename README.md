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

## CODE 
The code is well documented and as it's a commented notebook you can follow the code. However there are few things I want to point out




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
