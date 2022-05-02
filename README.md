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
