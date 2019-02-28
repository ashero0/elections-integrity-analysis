# Pandas Help

```python
import pandas as pd
```

### read from csv
```python
df = pd.read_csv('shoefly_orders.csv')
```

### look at first 10 rows
```python
df.head(10)
```

### select everyone who ordered black sandals
```python
df[(df.shoe_type == 'sandals') & (df.shoe_color == 'black')]
```

### select orders from susan dennis
```python
df[(df.first_name == 'Susan') & (df.last_name == 'Dennis')]
```

### data printing example
```python
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out country column as Pandas Series
print(cars['cars_per_cap'])

# Print out country column as Pandas DataFrame
print(cars[['cars_per_cap']])

# Print out DataFrame with country and drives_right columns
print(cars[['cars_per_cap', 'country']])
```
