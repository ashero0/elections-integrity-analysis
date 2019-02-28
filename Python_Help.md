# Python Basics for Statistical Analysis
```
import numpy as np
import pandas as pd
from matplotlib import pyplot as plt
from scipy import stats
```

## Histograms

### import data from csv
```python
transactions = pd.read_csv("transactions.csv")
```
### minimum
```python
min = np.amin(array)
```
### maximum
```python
max = np.amax(array)
```
### range
```python
range = max - min
```
### find bin width
```python
bins = # number of bins u wanna have
bin_width = (max-min + 1) / bins
```
### histogram function
```python
np.histogram(exercise_ages, range = (20, 70), bins = 5)
```
* `exercise_ages` is the input array
* `range = (20, 70)` is the range of values we expect in our array.
* Range includes everything from 20, up until but not including 70.
* `bins = 5` is the number of bins.
* Python will automatically calculate equally-sized bins based on the range and number of bins.
* **Output:** First array is the counts for each bin. Second array includes the min & max for each bin
### to graph histogram
```python
plt.hist(exercise_ages, range = (20, 70), bins = 5, edgecolor='black')
plt.title("Decade Frequency")
plt.xlabel("Ages")
plt.ylabel("Count")
plt.show()
```

# Mean, etc.
### average
```python
average = np.average(array)
```
### median
```python
median = np.median(array)
```
### mode
* If there are two modes, the `stats.mode()` method will always return the smallest mode in the dataset.
* The result of `stats.mode()` is an object with the smallest mode value, and its count.
```python
mode = stats.mode(array)
```
### example of plotting all three
```python
# Plot the figure
plt.hist(author_ages, range=(10, 80), bins=14,  edgecolor='black')
plt.title("Author Ages at Publication")
plt.xlabel("Publication Age")
plt.ylabel("Count")
plt.axvline(average_age, color='r', linestyle='solid', linewidth=3, label="Mean")
plt.axvline(median_age, color='y', linestyle='dotted', linewidth=3, label="Median")
plt.axvline(mode_age, color='orange', linestyle='dashed', linewidth=3, label="Mode")
plt.legend()

plt.show()
```
### variance
```python
variance = np.var(dataset)
```
### standard deviation
```python
stddev = np.var(dataset) ** 0.5 # Take the square root
```
or
```python
stddev = np.std(dataset)
```
### find num of stddevs away from the mean
```python
my_height = 80
nba_mean = np.mean(nba_data)
nba_standard_deviation = np.std(nba_data)
nba_difference = my_height - nba_mean
num_nba_deviations = nba_difference / nba_standard_deviation
```

# Seeing Raw Data
### print a few lines of data
```python
print(london_data.head()) # Print first few lines
print(london_data.iloc[100:200]) # Print lines 100-199
```
### see how many data points you have
```python
print(len(london_data))
```
### data extraction example
```python
from weather_data import london_data
temp = london_data["TemperatureC"]
average_temp = np.average(temp)
temperature_var = np.var(temp)
temperature_stddev = np.std(temp)
```
### filter data
```python
june = london_data.loc[london_data["month"] == 6]
```
