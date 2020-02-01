
### join two dataframes on a date field and return the closest (next or previous) value from the right table


```python
left = pd.DataFrame({'a': ['2010-01-01', '2015-01-01', '2100-01-01'], 'left_val': ['a', 'b', 'c']})
right = pd.DataFrame({'a': ['2010-01-01', '2012-01-01', '2013-01-01', '2016', '2017-01-01'], 'right_val': [1, 2, 3, 6, 7]})

left['a'] = pd.to_datetime(left['a'])
right['a'] = pd.to_datetime(right['a'])

left.set_index('a', inplace=True)
right.set_index('a', inplace=True)

print(left)
print(right)

print(pd.merge_asof(left, right, left_index=True, right_index=True)) #defualt direction in backward
print(pd.merge_asof(left, right, left_index=True, right_index=True, direction='forward'))
```

- references:
- https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.merge_asof.html
- https://stackoverflow.com/questions/37610983/how-set-column-as-date-index
- 
