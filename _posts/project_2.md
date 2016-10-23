
# Project 2
## Step 1: Exploring your data.

##### Load your data in using Pandas and start to explore. Save all of your early exploration code here and include in your final submission.


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
import scipy as stats
from __future__ import division
```


```python
#reading the files into pandas dataframe to analyse the data
df_billboard = pd.read_csv('../assets/billboard.csv')
df_billboard.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>x1st.week</th>
      <th>x2nd.week</th>
      <th>x3rd.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2000</td>
      <td>Destiny's Child</td>
      <td>Independent Women Part I</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-09-23</td>
      <td>2000-11-18</td>
      <td>78</td>
      <td>63.0</td>
      <td>49.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2000</td>
      <td>Santana</td>
      <td>Maria, Maria</td>
      <td>4:18</td>
      <td>Rock</td>
      <td>2000-02-12</td>
      <td>2000-04-08</td>
      <td>15</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2000</td>
      <td>Savage Garden</td>
      <td>I Knew I Loved You</td>
      <td>4:07</td>
      <td>Rock</td>
      <td>1999-10-23</td>
      <td>2000-01-29</td>
      <td>71</td>
      <td>48.0</td>
      <td>43.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2000</td>
      <td>Madonna</td>
      <td>Music</td>
      <td>3:45</td>
      <td>Rock</td>
      <td>2000-08-12</td>
      <td>2000-09-16</td>
      <td>41</td>
      <td>23.0</td>
      <td>18.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2000</td>
      <td>Aguilera, Christina</td>
      <td>Come On Over Baby (All I Want Is You)</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-08-05</td>
      <td>2000-10-14</td>
      <td>57</td>
      <td>47.0</td>
      <td>45.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 83 columns</p>
</div>




```python
df_billboard.dtypes
```




    year                 int64
    artist.inverted     object
    track               object
    time                object
    genre               object
    date.entered        object
    date.peaked         object
    x1st.week            int64
    x2nd.week          float64
    x3rd.week          float64
    x4th.week          float64
    x5th.week          float64
    x6th.week          float64
    x7th.week          float64
    x8th.week          float64
    x9th.week          float64
    x10th.week         float64
    x11th.week         float64
    x12th.week         float64
    x13th.week         float64
    x14th.week         float64
    x15th.week         float64
    x16th.week         float64
    x17th.week         float64
    x18th.week         float64
    x19th.week         float64
    x20th.week         float64
    x21st.week         float64
    x22nd.week         float64
    x23rd.week         float64
                        ...   
    x47th.week         float64
    x48th.week         float64
    x49th.week         float64
    x50th.week         float64
    x51st.week         float64
    x52nd.week         float64
    x53rd.week         float64
    x54th.week         float64
    x55th.week         float64
    x56th.week         float64
    x57th.week         float64
    x58th.week         float64
    x59th.week         float64
    x60th.week         float64
    x61st.week         float64
    x62nd.week         float64
    x63rd.week         float64
    x64th.week         float64
    x65th.week         float64
    x66th.week         float64
    x67th.week         float64
    x68th.week         float64
    x69th.week         float64
    x70th.week         float64
    x71st.week         float64
    x72nd.week         float64
    x73rd.week         float64
    x74th.week         float64
    x75th.week         float64
    x76th.week         float64
    dtype: object




```python
#checking the column names
df_billboard.columns.values
```




    array(['year', 'artist.inverted', 'track', 'time', 'genre', 'date.entered',
           'date.peaked', 'x1st.week', 'x2nd.week', 'x3rd.week', 'x4th.week',
           'x5th.week', 'x6th.week', 'x7th.week', 'x8th.week', 'x9th.week',
           'x10th.week', 'x11th.week', 'x12th.week', 'x13th.week',
           'x14th.week', 'x15th.week', 'x16th.week', 'x17th.week',
           'x18th.week', 'x19th.week', 'x20th.week', 'x21st.week',
           'x22nd.week', 'x23rd.week', 'x24th.week', 'x25th.week',
           'x26th.week', 'x27th.week', 'x28th.week', 'x29th.week',
           'x30th.week', 'x31st.week', 'x32nd.week', 'x33rd.week',
           'x34th.week', 'x35th.week', 'x36th.week', 'x37th.week',
           'x38th.week', 'x39th.week', 'x40th.week', 'x41st.week',
           'x42nd.week', 'x43rd.week', 'x44th.week', 'x45th.week',
           'x46th.week', 'x47th.week', 'x48th.week', 'x49th.week',
           'x50th.week', 'x51st.week', 'x52nd.week', 'x53rd.week',
           'x54th.week', 'x55th.week', 'x56th.week', 'x57th.week',
           'x58th.week', 'x59th.week', 'x60th.week', 'x61st.week',
           'x62nd.week', 'x63rd.week', 'x64th.week', 'x65th.week',
           'x66th.week', 'x67th.week', 'x68th.week', 'x69th.week',
           'x70th.week', 'x71st.week', 'x72nd.week', 'x73rd.week',
           'x74th.week', 'x75th.week', 'x76th.week'], dtype=object)



### *Billboard csv file dictionary*

| Columns | Data Type as of now/Data Type to be changed | Description of Columns | 
|---|---|---|
| year |Integer/Integer  |Calendar year the songs were part of billbard. Dataset is 2000 | 
| artist.inverted | Object/String | Name of the artist | 
| track | Object/String | Name of the track |
| time | Object/time | Length of the music track |
| genre | Object/String | Genre of the music track |
| date.entered | Object/Date time | The date of the music entered into billboard |
| date.peaked | Object/Date time | The date when the music track marked highest in billboard |
| x1st.week-x76th.week | Integer/Integer | Rank of the track on the billboard and the weeks after its entered |


```python
#checking the number of unique items in each item
print "Unique value in year: \t\t" , df_billboard['year'].nunique()
print "No of unique artists: \t\t" , df_billboard['artist.inverted'].nunique()
print "No. of unique tracks: \t\t" , df_billboard['track'].nunique()
print "No. of unique time:  \t\t", df_billboard['time'].nunique()
print "No. of unique genres:  \t\t", df_billboard['genre'].nunique()
print "No. of unique date.entered: \t", df_billboard['date.entered'].nunique()
print "No. of unique date.peaked: \t", df_billboard['date.peaked'].nunique()
```

    Unique value in year: 		1
    No of unique artists: 		228
    No. of unique tracks: 		316
    No. of unique time:  		126
    No. of unique genres:  		10
    No. of unique date.entered: 	68
    No. of unique date.peaked: 	53



```python
df_billboard.shape
```




    (317, 83)




```python
#Listing the top 10 most listed artists in billboard for analysis
df_billboard['artist.inverted'].value_counts().head(10)
```




    Jay-Z                   5
    Houston, Whitney        4
    Dixie Chicks, The       4
    DMX                     3
    Aguilera, Christina     3
    McGraw, Tim             3
    Backstreet Boys, The    3
    Thomas, Carl            3
    N'Sync                  3
    Destiny's Child         3
    Name: artist.inverted, dtype: int64




```python
#Jay-Z songs were listed 5 times and checking if any of his songs were peaked. But none of his songs peaked in billboard
df_billboard[df_billboard['artist.inverted'] == 'Jay-Z']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>x1st.week</th>
      <th>x2nd.week</th>
      <th>x3rd.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>57</th>
      <td>2000</td>
      <td>Jay-Z</td>
      <td>I Just Wanna Love U (Give It 2 Me)</td>
      <td>3:50</td>
      <td>Rap</td>
      <td>2000-10-28</td>
      <td>2000-12-30</td>
      <td>58</td>
      <td>45.0</td>
      <td>35.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>71</th>
      <td>2000</td>
      <td>Jay-Z</td>
      <td>Big Pimpin'</td>
      <td>3:55</td>
      <td>Rap</td>
      <td>2000-04-22</td>
      <td>2000-07-08</td>
      <td>69</td>
      <td>52.0</td>
      <td>39.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>192</th>
      <td>2000</td>
      <td>Jay-Z</td>
      <td>Anything</td>
      <td>3:41</td>
      <td>Rap</td>
      <td>2000-02-26</td>
      <td>2000-03-11</td>
      <td>72</td>
      <td>58.0</td>
      <td>55.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>226</th>
      <td>2000</td>
      <td>Jay-Z</td>
      <td>Do It Again (Put Ya Hands Up)</td>
      <td>3:47</td>
      <td>Rap</td>
      <td>2000-01-15</td>
      <td>2000-01-29</td>
      <td>95</td>
      <td>68.0</td>
      <td>65.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>264</th>
      <td>2000</td>
      <td>Jay-Z</td>
      <td>Hey Papi</td>
      <td>3:40</td>
      <td>Rap</td>
      <td>2000-08-12</td>
      <td>2000-10-07</td>
      <td>98</td>
      <td>100.0</td>
      <td>98.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 83 columns</p>
</div>




```python
#checking the top 10 listed tracks in billboard to check
df_billboard['track'].value_counts().head(10)
```




    Where I Wanna Be                     2
    If You Don't Wanna Love Me           1
    Just Be A Man About It               1
    With Arms Wide Open                  1
    Girls Dem Sugar                      1
    More                                 1
    Rhythm Divine                        1
    Case Of The Ex (Whatcha Gonna Do)    1
    Pull Over                            1
    Without You                          1
    Name: track, dtype: int64



## There are 317 rows or tracks on the list. However, there are 316 unique track values. I initially thought this was a duplicate record or maybe a cover song. There are two “Where I Wanna Be” tracks


```python
df_billboard[df_billboard['track'] == 'Where I Wanna Be']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>x1st.week</th>
      <th>x2nd.week</th>
      <th>x3rd.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>118</th>
      <td>2000</td>
      <td>Jones, Donell</td>
      <td>Where I Wanna Be</td>
      <td>6:22</td>
      <td>Rock</td>
      <td>2000-04-22</td>
      <td>2000-07-08</td>
      <td>81</td>
      <td>71.0</td>
      <td>65.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>305</th>
      <td>2000</td>
      <td>Sheist, Shade</td>
      <td>Where I Wanna Be</td>
      <td>4:16</td>
      <td>Rap</td>
      <td>2000-11-11</td>
      <td>2000-11-18</td>
      <td>96</td>
      <td>95.0</td>
      <td>99.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>2 rows × 83 columns</p>
</div>



## Most popular genre is Rock and it then Country then followed by Rap


```python
df_billboard['genre'].value_counts()
```




    Rock           137
    Country         74
    Rap             58
    R&B             23
    Pop              9
    Latin            9
    Electronica      4
    Gospel           1
    Jazz             1
    Reggae           1
    Name: genre, dtype: int64




```python
df_billboard['genre'].describe()
```




    count      317
    unique      10
    top       Rock
    freq       137
    Name: genre, dtype: object



##### Write a brief description of your data, and any interesting observations you've made thus far. 

* This dataset has the list of songs entered for the year 2000.
* There are 317 songs in this data set but only 228 unique artist lists which means there are some artist multiple times entered
* Date peaked, Date entered fields needs to be converted into date time
* time columns also needs to be converted into hour, time and minutes

## Step 2: Clean your data.

##### Do some rudimentary cleaning. Rename any columns that are poorly named, shorten any strings that may be too long, check for missing values (and replace them if it makes sense to do so). Explain your rationale for the way you choose to "impute" the missing data.


```python
#renaming the column names to analyse appropriately
df_billboard.rename(columns={'artist.inverted': 'artist',
                             'track': 'track_name',
                             'time': 'track_length',
                             'date.entered': 'date_entered', 
                             'date.peaked': 'date_peaked'},
                    inplace=True)
#removing x and . from column headers to make it cleaner and easy to analysis further
for item in df_billboard.columns:
    if any([char in item for char in ['x','.']]):
        newitem=''.join([char for char in item if char not in ['x','.']])
        df_billboard.rename(columns={item:newitem}, inplace=True)
```


```python
#changing the date entered and peaked columns into datetime format
df_billboard['date_entered'] = pd.to_datetime(df_billboard['date_entered'])
df_billboard['date_peaked'] = pd.to_datetime(df_billboard['date_peaked'])
```


```python
df_billboard.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 317 entries, 0 to 316
    Data columns (total 72 columns):
    year            317 non-null int64
    artist          317 non-null object
    track_name      317 non-null object
    track_length    317 non-null object
    genre           317 non-null object
    date_entered    317 non-null datetime64[ns]
    date_peaked     317 non-null datetime64[ns]
    1stweek         317 non-null int64
    2ndweek         312 non-null float64
    3rdweek         307 non-null float64
    4thweek         300 non-null float64
    5thweek         292 non-null float64
    6thweek         280 non-null float64
    7thweek         269 non-null float64
    8thweek         260 non-null float64
    9thweek         253 non-null float64
    10thweek        244 non-null float64
    11thweek        236 non-null float64
    12thweek        222 non-null float64
    13thweek        210 non-null float64
    14thweek        204 non-null float64
    15thweek        197 non-null float64
    16thweek        182 non-null float64
    17thweek        177 non-null float64
    18thweek        166 non-null float64
    19thweek        156 non-null float64
    20thweek        146 non-null float64
    21stweek        65 non-null float64
    22ndweek        55 non-null float64
    23rdweek        48 non-null float64
    24thweek        46 non-null float64
    25thweek        38 non-null float64
    26thweek        36 non-null float64
    27thweek        29 non-null float64
    28thweek        24 non-null float64
    29thweek        20 non-null float64
    30thweek        20 non-null float64
    31stweek        19 non-null float64
    32ndweek        18 non-null float64
    33rdweek        12 non-null float64
    34thweek        10 non-null float64
    35thweek        9 non-null float64
    36thweek        9 non-null float64
    37thweek        9 non-null float64
    38thweek        8 non-null float64
    39thweek        8 non-null float64
    40thweek        7 non-null float64
    41stweek        7 non-null float64
    42ndweek        6 non-null float64
    43rdweek        6 non-null float64
    44thweek        6 non-null float64
    45thweek        5 non-null float64
    46thweek        5 non-null float64
    47thweek        5 non-null float64
    48thweek        4 non-null float64
    49thweek        4 non-null float64
    50thweek        4 non-null float64
    51stweek        4 non-null float64
    52ndweek        4 non-null float64
    53rdweek        4 non-null float64
    54thweek        2 non-null float64
    55thweek        2 non-null float64
    56thweek        2 non-null float64
    57thweek        2 non-null float64
    58thweek        2 non-null float64
    59thweek        2 non-null float64
    60thweek        2 non-null float64
    61stweek        2 non-null float64
    62ndweek        2 non-null float64
    63rdweek        2 non-null float64
    64thweek        2 non-null float64
    65thweek        1 non-null float64
    dtypes: datetime64[ns](2), float64(64), int64(2), object(4)
    memory usage: 178.4+ KB



```python
# from 66+ weeks all have nan values. so dropping columns from 66
df_billboard = df_billboard.dropna(axis=1, how='all')
df_billboard.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>artist</th>
      <th>track_name</th>
      <th>track_length</th>
      <th>genre</th>
      <th>date_entered</th>
      <th>date_peaked</th>
      <th>1stweek</th>
      <th>2ndweek</th>
      <th>3rdweek</th>
      <th>...</th>
      <th>56thweek</th>
      <th>57thweek</th>
      <th>58thweek</th>
      <th>59thweek</th>
      <th>60thweek</th>
      <th>61stweek</th>
      <th>62ndweek</th>
      <th>63rdweek</th>
      <th>64thweek</th>
      <th>65thweek</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2000</td>
      <td>Destiny's Child</td>
      <td>Independent Women Part I</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-09-23</td>
      <td>2000-11-18</td>
      <td>78</td>
      <td>63.0</td>
      <td>49.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2000</td>
      <td>Santana</td>
      <td>Maria, Maria</td>
      <td>4:18</td>
      <td>Rock</td>
      <td>2000-02-12</td>
      <td>2000-04-08</td>
      <td>15</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2000</td>
      <td>Savage Garden</td>
      <td>I Knew I Loved You</td>
      <td>4:07</td>
      <td>Rock</td>
      <td>1999-10-23</td>
      <td>2000-01-29</td>
      <td>71</td>
      <td>48.0</td>
      <td>43.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2000</td>
      <td>Madonna</td>
      <td>Music</td>
      <td>3:45</td>
      <td>Rock</td>
      <td>2000-08-12</td>
      <td>2000-09-16</td>
      <td>41</td>
      <td>23.0</td>
      <td>18.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2000</td>
      <td>Aguilera, Christina</td>
      <td>Come On Over Baby (All I Want Is You)</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-08-05</td>
      <td>2000-10-14</td>
      <td>57</td>
      <td>47.0</td>
      <td>45.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 72 columns</p>
</div>



##### Using Pandas' built in `melt` function, pivot the weekly ranking data to be long rather than wide. As a result, you will have removed the 72 'week' columns and replace it with two: Week and Ranking. There will now be multiple entries for each song, one for each week on the Billboard rankings.


```python
df_billboard_big = pd.melt(df_billboard,
                          id_vars =['artist', 'track_name',
                                   'genre','date_entered',
                                   'date_peaked'],
                          value_vars =list(df_billboard.columns[7:]),
                          var_name ='week',
                          value_name='billboard_rank')
df_billboard_big.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>artist</th>
      <th>track_name</th>
      <th>genre</th>
      <th>date_entered</th>
      <th>date_peaked</th>
      <th>week</th>
      <th>billboard_rank</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Destiny's Child</td>
      <td>Independent Women Part I</td>
      <td>Rock</td>
      <td>2000-09-23</td>
      <td>2000-11-18</td>
      <td>1stweek</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Santana</td>
      <td>Maria, Maria</td>
      <td>Rock</td>
      <td>2000-02-12</td>
      <td>2000-04-08</td>
      <td>1stweek</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Savage Garden</td>
      <td>I Knew I Loved You</td>
      <td>Rock</td>
      <td>1999-10-23</td>
      <td>2000-01-29</td>
      <td>1stweek</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>Music</td>
      <td>Rock</td>
      <td>2000-08-12</td>
      <td>2000-09-16</td>
      <td>1stweek</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Aguilera, Christina</td>
      <td>Come On Over Baby (All I Want Is You)</td>
      <td>Rock</td>
      <td>2000-08-05</td>
      <td>2000-10-14</td>
      <td>1stweek</td>
      <td>57.0</td>
    </tr>
  </tbody>
</table>
</div>



## Step 3: Visualize your data.

##### Using a plotting utility of your choice (Tableau or python modules or both), create visualizations that will provide context to your data. There is no minimum or maximum number of graphs you should generate, but there should be a clear and consistent story being told. Give insights to the distribution, statistics, and relationships of the data. 

## Visualize to see which genre is popular??


```python
fig = plt.figure(figsize=(15,8))
plt.title("Total number of songs by Genre")
plt.ylabel("Total number of tracks")
pd.value_counts(df_billboard['genre']).plot.bar()
plt.show()

```


![png](output_29_0.png)


## Checking average ranking per week for all the songs in billboard??


```python
fig=plt.figure(figsize=(15,8))
plt.title("Average Ranking per week")
plt.ylabel("Ranking")

(df_billboard.loc[:,'1stweek':'65thweek'].describe().mean()).plot()

plt.show()
```


![png](output_31_0.png)


## As we can see from the above chart that average ranking per week was high in the initial weeks and the its fropped from 11th week and kept on dropping and few spike after 41st week till 65th week


```python
g1=df_billboard.groupby('genre').mean()
```


```python
g1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>1stweek</th>
      <th>2ndweek</th>
      <th>3rdweek</th>
      <th>4thweek</th>
      <th>5thweek</th>
      <th>6thweek</th>
      <th>7thweek</th>
      <th>8thweek</th>
      <th>9thweek</th>
      <th>...</th>
      <th>56thweek</th>
      <th>57thweek</th>
      <th>58thweek</th>
      <th>59thweek</th>
      <th>60thweek</th>
      <th>61stweek</th>
      <th>62ndweek</th>
      <th>63rdweek</th>
      <th>64thweek</th>
      <th>65thweek</th>
    </tr>
    <tr>
      <th>genre</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Country</th>
      <td>2000.0</td>
      <td>82.405405</td>
      <td>75.256757</td>
      <td>71.808219</td>
      <td>68.309859</td>
      <td>65.271429</td>
      <td>62.357143</td>
      <td>57.692308</td>
      <td>54.859375</td>
      <td>52.983871</td>
      <td>...</td>
      <td>25.0</td>
      <td>26.0</td>
      <td>31.0</td>
      <td>32.0</td>
      <td>37.0</td>
      <td>42.0</td>
      <td>42.0</td>
      <td>45.0</td>
      <td>50.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Electronica</th>
      <td>2000.0</td>
      <td>84.500000</td>
      <td>71.000000</td>
      <td>64.000000</td>
      <td>61.000000</td>
      <td>57.000000</td>
      <td>54.000000</td>
      <td>54.500000</td>
      <td>52.250000</td>
      <td>51.500000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Gospel</th>
      <td>2000.0</td>
      <td>76.000000</td>
      <td>76.000000</td>
      <td>74.000000</td>
      <td>69.000000</td>
      <td>68.000000</td>
      <td>67.000000</td>
      <td>61.000000</td>
      <td>58.000000</td>
      <td>57.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Jazz</th>
      <td>2000.0</td>
      <td>89.000000</td>
      <td>89.000000</td>
      <td>7.000000</td>
      <td>8.000000</td>
      <td>66.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Latin</th>
      <td>2000.0</td>
      <td>73.222222</td>
      <td>64.333333</td>
      <td>58.777778</td>
      <td>52.666667</td>
      <td>52.000000</td>
      <td>42.625000</td>
      <td>38.500000</td>
      <td>39.000000</td>
      <td>39.625000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Pop</th>
      <td>2000.0</td>
      <td>79.222222</td>
      <td>68.000000</td>
      <td>65.500000</td>
      <td>60.333333</td>
      <td>52.125000</td>
      <td>40.285714</td>
      <td>36.142857</td>
      <td>33.857143</td>
      <td>36.285714</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>R&amp;B</th>
      <td>2000.0</td>
      <td>84.086957</td>
      <td>74.095238</td>
      <td>67.190476</td>
      <td>60.894737</td>
      <td>61.473684</td>
      <td>56.000000</td>
      <td>58.294118</td>
      <td>63.294118</td>
      <td>62.062500</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Rap</th>
      <td>2000.0</td>
      <td>85.172414</td>
      <td>76.228070</td>
      <td>68.781818</td>
      <td>63.925926</td>
      <td>60.384615</td>
      <td>55.714286</td>
      <td>53.723404</td>
      <td>50.255814</td>
      <td>51.976744</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Reggae</th>
      <td>2000.0</td>
      <td>72.000000</td>
      <td>72.000000</td>
      <td>63.000000</td>
      <td>56.000000</td>
      <td>62.000000</td>
      <td>63.000000</td>
      <td>54.000000</td>
      <td>60.000000</td>
      <td>69.000000</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Rock</th>
      <td>2000.0</td>
      <td>76.116788</td>
      <td>66.852941</td>
      <td>60.298507</td>
      <td>54.015267</td>
      <td>49.330709</td>
      <td>45.894309</td>
      <td>42.689076</td>
      <td>40.234783</td>
      <td>38.819820</td>
      <td>...</td>
      <td>26.0</td>
      <td>29.0</td>
      <td>32.0</td>
      <td>39.0</td>
      <td>39.0</td>
      <td>43.0</td>
      <td>47.0</td>
      <td>50.0</td>
      <td>50.0</td>
      <td>49.0</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 66 columns</p>
</div>




```python
plt.figure(figsize=(15,8))
(g1.loc['Rock','1stweek':'65thweek']).plot()
(g1.loc['Country','1stweek':'65thweek']).plot()
(g1.loc['Rap','1stweek':'65thweek']).plot()
(g1.loc['Electronica','1stweek':'65thweek']).plot()
plt.title("Average ranking by week per Genre")
plt.legend()
plt.show()
```


![png](output_35_0.png)


## Step 4: Create a Problem Statement.

##### Having explored the data, come up with a problem statement for this data set. You can feel free to introduce data from any other source to support your problem statement, just be sure to provide a link to the origin of the data. Once again- be creative!


* Having exploring the data and looking at its rankings by week, its interesting to know why there is cut in the rankings for few weeks in the average rankings.
* It will be interesting to know with true data set why there is break in the ranking after entering?

After exploring and visualizing the data, it would be interesting to dive into the rankings of the songs that were cut after so many weeks of declining airtime. That would be the only true dataset to find the actual average song.
In addition, I would like to tie this dataset to a calendar year, not just “Weeks after entering.” Do certain songs have staying power when released during a certain time of year.
Also, what are the lyrics of the top songs? Do they have an effect?

## Step 5: Brainstorm your Approach.
##### In bullet-list form, provide a proposed approach for evaluating your problem statement. This can be somewhat high-level, but start to think about ways you can massage the data for maximum efficacy. 

Is there any relation with the lyrics for its success and being the ranking for so long. May be certain lyrics associated with joy, sad, pain, humor play towards the success of it. Why the ranking dropped after 20, 35, 52 weeks after enterining and it is interesting to investigate further with other music track rankings not only with billboard.

## Step 6: Create a blog post with your code snippets and visualizations.
##### Data Science is a growing field, and the Tech industry thrives off of collaboration and sharing of knowledge. Blogging is a powerful means for pushing the needle forward in our field. Using your blogging platform of choice, create a post describing each of the 5 steps above. Rather than writing a procedural text, imagine you're describing the data, visualizations, and conclusions you've arrived at to your peers. Aim for a minimum of 500 words. 



## BONUS: The Content Managers working for the Podcast Publishing Company have recognized you as a thought leader in your field. They've asked you to pen a white paper (minimum 500 words) on the subject of 'What It Means To Have Clean Data'. This will be an opinion piece read by a wide audience, so be sure to back up your statements with real world examples or scenarios.

##### Hint: To get started, look around on the internet for articles, blog posts, papers, youtube videos, podcasts, reddit discussions, anything that will help you understand the challenges and implications of dealing with big data. This should be a personal reflection on everything you've learned this week, and the learning goals that have been set out for you going forward. 


```python

```
