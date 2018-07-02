

```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
```


```python
# Read World Happiness Report into pandas
arrivals= "Data/GDP.csv"
arrivals_df = pd.read_csv(arrivals)

arrivals_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country_Name</th>
      <th>Country Code</th>
      <th>Indicator Name</th>
      <th>Indicator Code</th>
      <th>1960</th>
      <th>1961</th>
      <th>1962</th>
      <th>1963</th>
      <th>1964</th>
      <th>1965</th>
      <th>...</th>
      <th>2008</th>
      <th>2009</th>
      <th>2010</th>
      <th>2011</th>
      <th>2012</th>
      <th>2013</th>
      <th>2014</th>
      <th>2015</th>
      <th>2016</th>
      <th>2017</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Brazil</td>
      <td>BRA</td>
      <td>GDP (current US$)</td>
      <td>NY.GDP.MKTP.CD</td>
      <td>1.516557e+10</td>
      <td>1.523685e+10</td>
      <td>1.992629e+10</td>
      <td>2.302148e+10</td>
      <td>2.121189e+10</td>
      <td>2.179004e+10</td>
      <td>...</td>
      <td>1.695820e+12</td>
      <td>1.667020e+12</td>
      <td>2.208870e+12</td>
      <td>2.616200e+12</td>
      <td>2.465190e+12</td>
      <td>2.472810e+12</td>
      <td>2.455990e+12</td>
      <td>1.803650e+12</td>
      <td>1.796190e+12</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Canada</td>
      <td>CAN</td>
      <td>GDP (current US$)</td>
      <td>NY.GDP.MKTP.CD</td>
      <td>4.109345e+10</td>
      <td>4.076797e+10</td>
      <td>4.197885e+10</td>
      <td>4.465717e+10</td>
      <td>4.888294e+10</td>
      <td>5.390957e+10</td>
      <td>...</td>
      <td>1.549130e+12</td>
      <td>1.371150e+12</td>
      <td>1.613460e+12</td>
      <td>1.788650e+12</td>
      <td>1.824290e+12</td>
      <td>1.842630e+12</td>
      <td>1.799270e+12</td>
      <td>1.559620e+12</td>
      <td>1.535770e+12</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>China</td>
      <td>CHN</td>
      <td>GDP (current US$)</td>
      <td>NY.GDP.MKTP.CD</td>
      <td>5.971647e+10</td>
      <td>5.005687e+10</td>
      <td>4.720936e+10</td>
      <td>5.070680e+10</td>
      <td>5.970834e+10</td>
      <td>7.043627e+10</td>
      <td>...</td>
      <td>4.598210e+12</td>
      <td>5.109950e+12</td>
      <td>6.100620e+12</td>
      <td>7.572550e+12</td>
      <td>8.560550e+12</td>
      <td>9.607220e+12</td>
      <td>1.048240e+13</td>
      <td>1.106470e+13</td>
      <td>1.119910e+13</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>France</td>
      <td>FRA</td>
      <td>GDP (current US$)</td>
      <td>NY.GDP.MKTP.CD</td>
      <td>6.265147e+10</td>
      <td>6.834674e+10</td>
      <td>7.631378e+10</td>
      <td>8.555111e+10</td>
      <td>9.490659e+10</td>
      <td>1.021610e+11</td>
      <td>...</td>
      <td>2.923470e+12</td>
      <td>2.693830e+12</td>
      <td>2.646840e+12</td>
      <td>2.862680e+12</td>
      <td>2.681420e+12</td>
      <td>2.808510e+12</td>
      <td>2.849310e+12</td>
      <td>2.433560e+12</td>
      <td>2.465450e+12</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Germany</td>
      <td>DEU</td>
      <td>GDP (current US$)</td>
      <td>NY.GDP.MKTP.CD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>3.752370e+12</td>
      <td>3.418010e+12</td>
      <td>3.417090e+12</td>
      <td>3.757700e+12</td>
      <td>3.543980e+12</td>
      <td>3.752510e+12</td>
      <td>3.890610e+12</td>
      <td>3.375610e+12</td>
      <td>3.477800e+12</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 62 columns</p>
</div>




```python
# Create dataframe for winning countries
GDP_winners_df = arrivals_df.loc[(arrivals_df["Country_Name"] == "Spain")|(arrivals_df["Country_Name"] == "Italy") | (arrivals_df["Country_Name"] == "Germany")| (arrivals_df["Country_Name"] == "Brazil")]

# Set the 'Country name' to be our index for easy referencing of rows and drop colmns we dont need
GDP_winners_df = GDP_winners_df.set_index("Country_Name")
GDP_winners_df.drop([ 'Country Code', 'Indicator Name', 'Indicator Code'], axis=1, inplace=True)

GDP_control_df = arrivals_df.loc[arrivals_df["Country_Name"].isin(['Australia','Canada','China','France','India','Indonesia','Japan','Korea, Rep.','Mexico','Netherlands','Russian Federation','Saudi Arabia','Switzerland','Turkey','United Kingdom','United States'])]
#arrivals_Control_df = arrivals_df.loc[(arrivals_df["Country Name"] == "UK") | (arrivals_df["Country Name"] == "France") | (arrivals_df["Country Name"] == "Brazil") ]
GDP_control_df = GDP_control_df.set_index("Country_Name")

GDP_control_df.drop([ 'Country Code', 'Indicator Name', 'Indicator Code'], axis=1, inplace=True)
GDP_control_df.head()

# find the average of arrivals between control countries
mean=GDP_control_df.mean(axis=0)


```


```python
# Collect the years where data was collected
keys = GDP_control_df.mean()
years = GDP_control_df.keys()
years
```




    Index(['1960', '1961', '1962', '1963', '1964', '1965', '1966', '1967', '1968',
           '1969', '1970', '1971', '1972', '1973', '1974', '1975', '1976', '1977',
           '1978', '1979', '1980', '1981', '1982', '1983', '1984', '1985', '1986',
           '1987', '1988', '1989', '1990', '1991', '1992', '1993', '1994', '1995',
           '1996', '1997', '1998', '1999', '2000', '2001', '2002', '2003', '2004',
           '2005', '2006', '2007', '2008', '2009', '2010', '2011', '2012', '2013',
           '2014', '2015', '2016', '2017'],
          dtype='object')




```python
# Plot the number of arrivals for each country and add marker X for the winning year
plt.plot(years, GDP_winners_df.loc['Germany', years], 
         color="red", label="Germany")
plt.scatter( (GDP_winners_df.loc['Germany'].keys()[52]),GDP_winners_df.loc['Germany', '2012'],  color="red",marker='x',label='_nolegend_')


plt.plot(years, GDP_winners_df.loc['Italy', years], 
         color="black", label="Italy")
plt.scatter( (GDP_winners_df.loc['Italy'].keys()[46]),GDP_winners_df.loc['Italy', '2006'],  color="black",marker='x',label='_nolegend_')


plt.plot(years, GDP_winners_df.loc['Spain', years], 
         color="green", label="Spain")
plt.scatter( (GDP_winners_df.loc['Italy'].keys()[50]),GDP_winners_df.loc['Spain', '2010'],  color="green",marker='x',label='_nolegend_')

plt.plot(years, GDP_winners_df.loc['Brazil', years], 
         color="blue", label="Brazil")
plt.scatter( (GDP_winners_df.loc['Brazil'].keys()[42]),GDP_winners_df.loc['Brazil', '2002'],  color="blue",marker='x',label='_nolegend_')

## plot graph for average of control countries
plt.plot(years, mean, color='grey',alpha=0.65, label="Control countries ")


plt.xlim(2000, 2016)

## create Legend and place outside of graph
plt.legend(bbox_to_anchor=(1.05, 1), loc=2, borderaxespad=0.)

plt.title("GDP 2000-2016")
plt.xlabel("Years")
plt.ylabel("GDP")

# Customize the grid
plt.style.use('seaborn')


# Add arrow
plt.annotate('Great Spanish Depression', xy=('2010-10-25', 40), xytext=('2011-08-25', 60),
            arrowprops=dict(arrowstyle="->",facecolor='black'))

# Show the chart
plt.show()

```


![png](output_4_0.png)

