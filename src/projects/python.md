# Python


```python
strings = ['alt', 'bam', 'alt', 'ant', 'din']
numbers = [1, 2, 1, 9, 4, 3, 3]
tuple = (1, 2, 1, 9, 4, 3, 3)
dictionary = {'a': 1, 'b': 3, 'c': 3, 'd': 9, 'e': 5}
dictionary_lists = {
    'a': [1, 0, 30],
    'b': [15, 2, 35],
    'c': [2, 3, 9],
    'd': [0, 20, 11],
    'e': [1, 5, 3]
}
```

#### main()

The
**if __name__ == '__main__':
 main()**
construct is a common pattern used in Python to ensure that a block of code is only executed when the script is run directly as the main module, and not when it is imported as a module by another script.


```python
class MyClass:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f"Hello, {self.name}!")

    def main(self):
        # Main logic of the script
        self.greet()

if __name__ == '__main__':
    my_object = MyClass("Alice")
    my_object.main()
```


```python
class MyClass:
    n = 3
    m = 5

    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f"Hello, {self.name}!")

    def calculate_sum(self, a, b):
        return a + b

    def calculate_product(self, a, b):
        return a * b

    def print_sum_and_product(self, a, b):
        sum_result = self.calculate_sum(a, b)
        product_result = self.calculate_product(a, b)
        print(f"The sum of {a} and {b} is: {sum_result}")
        print(f"The product of {a} and {b} is: {product_result}")

    def main(self):
        # Main logic of the script
        self.greet()
        self.print_sum_and_product(self.n, self.m)


if __name__ == '__main__':
    my_object = MyClass("Alice")
    my_object.main()
```

    Hello, Alice!
    The sum of 3 and 5 is: 8
    The product of 3 and 5 is: 15


#### Comprehension List


```python
l = [string for string in strings if string.startswith('a')]
l
```

#### Filtering


```python
def is_even(number):
    return number % 2 == 0

even_numbers = list(filter(is_even, numbers))
even_numbers
```




    [2, 4]




```python
strings_with_a = list(filter(lambda string: string.startswith('a'), strings))
strings_with_a
```




    ['alt', 'alt', 'ant']




```python
strings_with_a = [string for string in strings if string.startswith('a')]
strings_with_a
```




    ['alt', 'alt', 'ant']




```python
filtered_dictionary = {key: value for key, value in dictionary.items() if value > 3}
filtered_dictionary
```




    {'d': 9, 'e': 5}




```python
filtered_dictionary_lists = {
    key: [value for value in values if value > 5]
    for key, values in dictionary_lists.items()
}
filtered_dictionary_lists
```




    {'a': [30], 'b': [15, 35], 'c': [9], 'd': [20, 11], 'e': []}



#### Aggregation



```python
nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
sums = [sum(sublist) for sublist in nested_list]
total = sum(sums)
total
```




    45



#### Grouping


```python
grouped_strings = {}
for string in strings:
    key = string[0] # Group by initial letter of the strings
    if key not in grouped_strings:
        grouped_strings[key] = []
    grouped_strings[key].append(string)
dict(sorted(grouped_strings.items()))
```




    {'a': ['alt', 'alt', 'ant'], 'b': ['bam'], 'd': ['din']}




```python
grouped_numbers = {}
for num in numbers:
    key = num % 2  # Group by even/odd
    if key not in grouped_numbers:
        grouped_numbers[key] = []
    grouped_numbers[key].append(num)
dict(sorted(grouped_numbers.items()))
```




    {0: [2, 4], 1: [1, 1, 9, 3, 3]}




```python
grouped_tuple = {}
for value in tuple:
    key = value // 3  # Group by tens place
    if key not in grouped_tuple:
        grouped_tuple[key] = []
    grouped_tuple[key].append(value)
dict(sorted(grouped_tuple.items()))
```




    {0: [1, 2, 1], 1: [4, 3, 3], 3: [9]}




```python
grouped_dictionary = {}
for key, value in dictionary.items():
    if value not in grouped_dictionary:
        grouped_dictionary[value] = []
    grouped_dictionary[value].append(key)
dict(sorted(grouped_dictionary.items()))
```




    {1: ['a'], 3: ['b', 'c'], 5: ['e'], 9: ['d']}




```python
grouped_dictionary_of_lists = {}
for key, values in dictionary_lists.items():
    for value in values:
        if value not in grouped_dictionary_of_lists:
            grouped_dictionary_of_lists[value] = []
        grouped_dictionary_of_lists[value].append(key)
dict(sorted(grouped_dictionary_of_lists.items()))
```




    {0: ['a', 'd'],
     1: ['a', 'e'],
     2: ['b', 'c'],
     3: ['c', 'e'],
     5: ['e'],
     9: ['c'],
     11: ['d'],
     15: ['b'],
     20: ['d'],
     30: ['a'],
     35: ['b']}




```python
from itertools import groupby

strings.sort(key=lambda x: x[0])
strings_grouped = groupby(strings, key=lambda x: x[0])

for key, value in strings_grouped:
    print(f'Initial letter {key}: {list(value)}')
```

    Initial letter a: ['alt', 'alt', 'ant']
    Initial letter b: ['bam']
    Initial letter d: ['din']



```python
import pandas as pd

df = pd.DataFrame({
    'id': [1, 2, 3, 4, 5],
    'animal': ['dog', 'cat', 'cat', 'donkey', 'cat'],
    'weight': [12, 3, 2, 9, 15]
})
df_grouped = df.groupby('animal')
df_grouped['weight'].sum()
```




    animal
    cat       20
    dog       12
    donkey     9
    Name: weight, dtype: int64



#### Sorting


```python
sorted_strings = sorted(strings)
sorted_strings
```




    ['alt', 'alt', 'ant', 'bam', 'din']




```python
sorted_numbers = sorted(numbers)
sorted_numbers
```




    [1, 1, 2, 3, 3, 4, 9]




```python
tuple_list = [(2,3), (4,9), (8,2,1), (9,0,3), (5,7)]
sorted_tuple = sorted(tuple_list, key=lambda x:min(x))
sorted_tuple
```




    [(9, 0, 3), (8, 2, 1), (2, 3), (4, 9), (5, 7)]




```python
sorted_dictionary_by_key = dict(sorted(dictionary.items()))
sorted_dictionary_by_key
```




    {'a': 1, 'b': 3, 'c': 3, 'd': 9, 'e': 5}




```python
sorted_dictionary_by_value = dict(sorted(dictionary.items(), key=lambda x: x[1]))
sorted_dictionary_by_value
```




    {'a': 1, 'b': 3, 'c': 3, 'e': 5, 'd': 9}




```python
sorted_dictionary_of_lists = {key: sorted(values) for key, values in dictionary_lists.items()}
sorted_dictionary_of_lists
```




    {'a': [0, 1, 30],
     'b': [2, 15, 35],
     'c': [2, 3, 9],
     'd': [0, 11, 20],
     'e': [1, 3, 5]}



#### List Methods


```python
l = [2, 3, 1, 3]
l.append(5)
l
```




    [2, 3, 1, 5]




```python
l = [2, 3, 1, 3]
l.extend([3, 4, 5])
l
```




    [2, 3, 1, 3, 4, 5]




```python
l = [2, 3, 1, 3]
l.insert(1, 10)
l
```




    [2, 10, 3, 1]




```python
l = [2, 3, 1, 3]
l.remove(3)
l
```




    [2, 1, 3]




```python
l = [2, 3, 1, 3]
l.pop(1)
l
```




    [2, 1]




```python
l = [2, 3, 1, 3]
print(l.count(3))
```

    2



```python
l = [2, 3, 1, 3]
l.sort()
l
```




    [1, 2, 3, 3]




```python
l = [2, 3, 1, 3]
l.reverse()
l
```




    [3, 1, 3, 2]



#### Datetime


```python
from datetime import datetime

current_datetime = datetime.now()
formatted_datetime = current_datetime.strftime("%Y-%m-%d %H:%M:%S")
formatted_datetime
```




    '2023-07-17 17:43:32'




```python
date_string = "2023-07-17 15:30:00"
parsed_datetime = datetime.strptime(date_string, "%Y-%m-%d %H:%M:%S")
parsed_datetime
```




    datetime.datetime(2023, 7, 17, 15, 30)




```python
from datetime import timedelta

future_datetime = current_datetime + timedelta(days=7)
future_datetime.strftime("%Y-%m-%d %H:%M:%S")
```




    '2023-07-24 17:43:32'




```python
year = current_datetime.year
month = current_datetime.month
day = current_datetime.day
hour = current_datetime.hour
minute = current_datetime.minute
second = current_datetime.second
print(f"Year: {year}, Month: {month}, Day: {day}, Hour: {hour}, Minute: {minute}, Second: {second}")
```

    Year: 2023, Month: 7, Day: 17, Hour: 17, Minute: 43, Second: 32



```python
datetime1 = datetime(2023, 7, 17, 12, 0, 0)
datetime2 = datetime(2023, 7, 18, 9, 0, 0)
if datetime1 < datetime2:
    print("datetime1 is earlier than datetime2")
else:
    print("datetime2 is earlier than datetime1")
```

    datetime1 is earlier than datetime2



```python
date = '2023-04-01'
date = datetime.strptime(date, "%Y-%m-%d").date()
time = '15:30:01'
time = datetime.strptime(time, "%H:%M:%S").time()
date_time = datetime.combine(date, time).strftime("%Y-%m-%d %H:%M:%S")
date_time
```




    '2023-04-01 15:30:01'




```python
datetime.strptime(date_time, "%Y-%m-%d %H:%M:%S").time().strftime("%H:%M:%S")
```




    '15:30:01'




```python
dt = datetime(2022, 5, 10, 15, 30, 45)
dt = dt.replace(year=2023)
dt
```




    datetime.datetime(2023, 5, 10, 15, 30, 45)




```python
dt.weekday()
```




    2




```python
dt.isoweekday()
```




    3



#### String Manipulation


```python
string = '  Hello '
string.strip()
```




    'Hello'




```python
string = 'oooHello'
string.strip('o')
```




    'Hell'




```python
string = 'Hello'
string.startswith('H')
```




    True




```python
string = 'Hello'
string.endswith('H')
```




    False




```python
string = 'Hello'
string.index('e')
```




    1




```python
string = 'Hello'
string.count('l')
```




    2




```python
string = 'Hello'
list(string)
```




    ['H', 'e', 'l', 'l', 'o']




```python

```
