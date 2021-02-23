---
title: "Covid-19 Vaccinations Status Dashboard"
excerpt: "A Tableau dashboard to visualize data "
header:
  teaser: /assets/images/vaccine.jpg

 
tags: 
  - Data Clean
  - Data Visualization
  - Tableau
  - Dashboard
  - Covid-19
---

[Show on gallery](https://public.tableau.com/views/covid2_16138717906360/Dashboard1?:language=zh-Hant&:display_count=y&publish=yes&:origin=viz_share_link)

## How to use

Most of the information are in the tool tip of map chart, the control bars are explained below

- __Select Metric:__ 
Chose one from the 4 metics ( People fully vaccinated / People vaccinated / Total Vaccinated / Last N days Avg.) and result will be present on left 2 charts.

- __Unit:__ 
By raw number / By per hundred (only applies to first 3 metrics)

- __Vaccination Threshold__: 
When observing metrics with By per hundred, the rank chart may include some region that with small population, can be avoid by increading vaccinations threshold.

- __N days:__ 
How days are used to calculate average of daily vaccinations (only applies to Last N days Avg.)


## Data Clean 

I did some data clean for the purpose of plotting cumulative chart and calculating last n days average, both of them need data that has value at current data, however some countries are not updating daily. So I just assume that the date they are not updated is 0 or remain the same.

For example on 2021-02-21 one of the countries data looks like this, there has no data of 2/20 and 2/21

> | Country       | Date       | Daily Vaccinations | People Fully Vaccinated |
|---------------|------------|--------------------|-------------------------|
| United States | 2021-02-17 | 100                | NaN                     |
| United States | 2021-02-18 | 200                | NaN                     |
| United States | 2021-02-19 | 300                | 200                     |

Then after imputation it should look like this, 0 was imputed to daily associated columns and latest data was cloned to status features like _People Fully Vaccinated_.

> | Country       | Date       | Daily Vaccinations | People Fully Vaccinated |
|---------------|------------|--------------------|-------------------------|
| United States | 2021-02-17 | 100                | NaN                     |
| United States | 2021-02-18 | 200                | NaN                     |
| United States | 2021-02-19 | 300                | 200                     |
| United States | 2021-02-20 | 0                  | 200                     |
| United States | 2021-02-21 | 0                  | 200                     |

Code 
```python
df = pd.read_csv("/kaggle/input/covid-world-vaccination-progress/country_vaccinations.csv")

# latest report date
max_date = df['date'].max()

# create country/region list
country_lst = df.country.tolist()
country_lst = set(country_lst)

# create dict to access index of each column 
col_inx = {col_name:i for i,col_name in enumerate(df.columns.values)}

# Started to impute country by country
temp_df_lst = []
for country in country_lst:
    
    temp_df = pd.DataFrame(df.groupby(['country']).get_group(country))
    # lastest date of this country
    last_update = temp_df['date'].max()
    
    if last_update < max_date:
        # create date list 
        time_delta = pd.to_datetime(max_date) - pd.to_datetime(last_update)
        # length of lack data
        append_len = time_delta.days
        # create date string list
        time_lst = [pd.to_datetime(temp_df['date'].max())+pd.Timedelta(x, unit="day") for x in range(1,time_delta.days+1)]
        time_lst = [x.strftime("%Y-%m-%d") for x in time_lst]
        
        # create append data for other features, basically remain the same like the last day's information
        last_data = temp_df[temp_df['date'] == last_update].values
        # cloning to append length
        append_data = np.tile(last_data,(append_len,1))
        # specify 0 to "daily" related columns since there is no updates at these dates, and other features remain the same
        append_data[:,col_inx['date']] = time_lst
        append_data[:,col_inx['daily_vaccinations_raw']] = 0
        append_data[:,col_inx['daily_vaccinations']]=0
        append_data[:,col_inx['daily_vaccinations_per_million']]=0
        # create df 
        append_df = pd.DataFrame(append_data,columns=df.columns)
        # append to origin df and add to list 
        temp_df_lst.append(temp_df.append(append_df,ignore_index=True))
    else:
        temp_df_lst.append(temp_df)

# concate into new df

new_df = pd.concat(temp_df_lst,axis=0,ignore_index=True)


# sorting 
new_df = new_df.sort_values(by=['country','date'])

new_df.reset_index(inplace=True,drop=True)
```