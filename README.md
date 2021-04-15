# CSE163Note

Prof: Kevin Lin

## Basics

- Print 

  ```python
  print('a', 'b', 'c') #'a b c', add space in it
  print('abc') # 'abc'
  ```

  print 自动换行

- Main pattern

  ```python
  def main():
    if __name__ = '__main__':
      main()
  ```

- variable 可以被重复定义 -- mutable 

- Expression

  - Division `a / b`
  - Integeter devision `a // b`
  - Exp `a ** b`

- T/F

  - Same as Java

- Cast

  - Float to int:  取整 不四舍五入
  - Int to float: 加 .0
  - Float to str: 不变
  - Str to float: 需要Str是数字
  - Str to int: 需要Str是整数
  - Int to str: 不变

- Python: 用Indentation区别loop内外

- Loop

  - While loop

    ```python
    while condition:
      process
    ```

  - For loop

    ```python
    for i in range(int):
      
    for item in collection:
      
    ```

    Range

    - `range(A)` 0到A不包括A
    - `range(A, B)` 从A（包括A）到B（不包括B）
    - `range(A, B, C)` 从A到B+=C

- Condition

  ```python
  if condition:
    
  elif condition:
  
  else:
  ```

- Function

  - Build-in

    - `print(), range()`, casting, math...

  - User define

    - ```python
      def a():
        
      def a(x, y):
        return x + y
      ```

- String and Lists

  - 单引号双引号都可以，只要consistent
  - String里面出现单引号外面使用双引号作为区分
  - Concatenation
    - `str1 + str2` 中间无空格
    - **因为+只会创建新的String，不会自动cast，只能将两个原本就是str的相加**
  - Index `str[i]`
  - Length `len(str)` 计算方式与Java一样
  - Loop over: 同For Each Loop
  - **String是object**
    - Find `str.find(str)` return 开始的index，没有的话就是-1
    - `lower()/upper()`
    - `strip()` 创建新的无空格的string 也有`lstrip()/rstrip()`
    - `a.join(str)` 插入：str中插入a
  - String slice
    - `[a:b]` 包括a不包括b
    - `[:b]` 从0开始不包括b
    - `[a:]` 从a开始到end
    - `[a:b:c]` step c
    - **negative index**: Python对于负index有新的计算方式，最后一位为-1向前递减
  - List
    - `s.split` return a list of str
    - list can contain many different types
    - **Mutable: 可以直接修改list里面的内容：`l[i] = a`**

- Doc

  - ```python
    """
    This is a head comment
    """
    ```

- None: 

  - Absense of a value
  - **单独的一个type，需要使用`isNone` 不要使用==**

## File Processing

In terminal: `cat poem.txt` to displat contents

- Open files in Python

  - Use `open` 

    ```python
    with open('path') as f:
      content = f.read() # return file contents as str
    ```

- Line processing

  - Line by line: `split` or `readlines`

  - **each line will have `\n` in the end so we need to strip to trail space**

    ```python
    def number_lines(file_name):
      with open(file_name) as f:
        lines = f.readlines() #read from file handle
        line_num = 1 #initialize line number
        for line in lines:
          line = line.strip()
          line_num += 1
    ```

- Token processing

  - Since each line is a string, use split
    - `words = line.split()`

- File Path

  - relative path
  - absolute path(on Ed) start with /

## Python Models 

### Scripts

`.py` files, run using `python file_name.py`

### Interactive

Read Evaluate Print Loop

- Run in terminal 
- Exit using `Ctrl D` / `exit()`
- Jupyter notebooks

## Data Structures

### List

- Have integer indices order the elements in list
- Mutable

- **List Methods**

  - `l.append(x)` adds `x` to the end of `l`
  - `l.extend(xs)` adds all elements in `xs` to end of `l`
  - `l.insert(i, x)` inserts `x` at index `i` in `l`
  - `l.remove(x)` removes the first `x` found in `l`
  - `l.pop(i)` removes the element at index `i` in `l`
  - `l.clear()` removes all values from `l`
  - `l.index(x)` returns the first index whose associated value is `x`. If `x` is not in `l` give error
  - `l.reverse()` reverses the order of all elements in `l`
  - `l.sort()` rearranges all elements of `l` into sorted order

  - `in` keyword: made for doing contains queries, or **membership queries**

  ```python
  if 'a' in words: # can also be `not in` if you want
    print('exist')
  else:
    print('no')
  ```

- **List comprehensions**

  - List can also be sliced

    ```python
    l = [1, 2, 'hello']
    print(l[1:2]) # 2
    l[1] = 3 # mutable can be changed
    print(l[1]) # 3
    ```

  - **Syntax**

    ```python
    nums = [i for i in range(1, 100)] # nums now contains 1 to 99
    
    # To be more clear
    nums = [                   # 3. Store the result in list called nums
      i                        # 2. The value you will put in list
      for i in range(1, 100)   # 1. What you are looping for
    ]
    
    # Compute value
    squares = [i ** 2 for i in range(1, 11)] # in 1-10, store every i ^ 2
    
    # Filter value
    squares = [i ** 2 for i in range(1, 11) if i % 3 == 0] # in 1-10, for every i % 3 == 0, store its i^2
    ```

### Tuples

- **Immutable** 

- Also have integer indices

- Do not have any meaningful methods since immutable

- Define

  ```python
  t = 1, 2, 3
  tt = (1, 2, 3)
  ```

- Access: same as list

- **Why Tuples instead of Lists?**

  - When you need data that cannot be changed

- Unpack tuples

  - Tuples normally appear as a way to return more than one values from a function 

    ```python
    def ftletters(word):
      return word[0], word[1]
    
    #Unpack
    a, b = ftletters("cat") #c a
    ```

  - Give a variable name to each component than index
  
    ```python
    t = 4, 5, 6
    a, b, c = t # unpack
    a b c # 4, 5, 6
    
    # Note the number of targets must match the length of tuple
    
    a, b, c, d = t # Error
    a, b = t # Only unpack the first two
    
    # Or, if you want only few values, you can do
    a, b, _ = t
    ```
  
    - List can do the same, but not recommanded since list is mutable

### Set

- **FAST** when finding unique values

  - Set wont allow duplicates 
  - Does not have notion of indices

- Define

  ```python
  nums = set()
  ```

- Set Methods

  - `s.add(num)` adds `num` to `s`, ignore duplicates
  - `s.remove(num)` removes `num` from s, error if not exist
  - `s.clear()` removes all values
  - `len(s)`, `in` keyword
  - if you try index will be error

### Dictionaries 

- Store data type as index, mutable

- key-value pair

- Define

  ```python
  d = {'a': 1, 'b': 17, 47: 'sc'}
  d = {}
  d = dict()
  ```

- Usage

  ```python
  d['dogs'] = 'cute' # Add new element
  d['a'] = 'cute' # Change element
  # if a key already exist => overwitten if you set
  ```

- **If a key is not in dictionary and you call it by `d['a']` it will return error** 

  - Check first use `in`

- **Dictionary Methods**

  - `d.pop(key)` removes `key` from `d`
  - `d.keys()` returns a collection of all keys in `d`
  - `d.values()` returns a collection of all the values in `d`
  - `d.items()` returns a collection of all `(key, value)` tuples in `d`

- Iteration

  ```python
  for k in d.keys():
      print(k, d[k])
      
  for pair in d.items():
      # (key, value) tuples
      print(pair[0], pair[1])
  # unpack tuple
  for k, v in d.items():
      print(k, v)
  ```

### Enumerate and Zip

- Python built-in functions

- Enumerate

  - Helps you loop over both indices and elements of a sequence at the same time

    ```python
    squares = [i ** 2 for i in range(1, 11)]
    
    for i, n in enumerate(squares):
        print(i, n) # Gives both indices and element as tuple
    ```

- Zip

  - Helps you loop over multiple sequences at the same time. 

    ```python
    numbers = [i for i in range(1, 11)]
    squares = [i ** 2 for i in range(1, 11)]
    cubes = [i ** 3 for i in range(1, 11)]
    
    for i in range(len(numbers)):
        print(numbers[i], squares[i], cubes[i])
    
    for n, s, c in zip(numbers, squares, cubes):
        print(n, s, c) # Give all at the same time as tuples
    ```

## CSVs

- List of Dictionaries

  ```python
  data = [
      {'Name': 'Madrona', 'Salary': 3},
      {'Name': 'Rit',     'Salary': 1},
      {'Name': 'Ryan',    'Salary': 3}
  ]
  print('Data:', data)
  print('Number of rows:', len(data))  # Since data is just a list
  print('Row 2:', data[1])
  
  ta = data[1]  # This is a dictionary: {'Name': 'Rit', 'Salary': 1}
  print('Name of TA in Row 2:', ta['Name'])
  
  # It helps to print out the types of things
  print()
  print('Types')
  print('type(data)', type(data))
  print('type(data[1])', type(data[1]))
  print("type(ta['Name'])", type(ta['Name']))
  ```

- Reading in a CSV file

  ```python
  import pandas as pd
  
  def parse(file_name):
      """
      Reads the CSV with the given file_name and returns it as a list of
      dictionaries. The list will have a dictionary for each row, and each
      dictionary will have a key for each column.
      """
      df = pd.read_csv(file_name)
      return df.to_dict('records')
  
  print(parse('/course/lessons/tas.csv'))
  #[{'Name': 'Flora', 'Salary': 3}, {'Name': 'Ken', 'Salary': 1}, {'Name': 'Ryan', 'Salary': 3}]
  ```


## Panda

### Imports

- Python module can be executed and imported

  ```python
  import module_a
  import module_a as m
  from module_a import fun2
  
  df = pd.read_csv('/home/tas.csv')
  ```

### Access Columns

```python
df['Name']
```

- Series
  - `Series` is 1-dimensional (it only has "one direction" like a single row or a single column).
- DataFrame
  - A `DataFrame` is a 2-dimensional structure (it has rows and columns like a grid)

### Element Operation

```python
df2['emissions'] + df2['population'] # returns a new Series that represents the sum of those two columns. The first value in the Series is the sum of the first values in the two that were added, the second is the sum of the second two, etc. It does not modify any of the columns of the dataset
```

### Filter Data

- If you pass it a `str` (e.g., `df2['emissions']`), it returns that column as a `Series`.
- If you pass it a `Series` with `dtype=bool` (e.g., `df2[df2['emissions'] >= 200]`), it will return a `DataFrame` of all the rows that `Series` had a `True` value for!
- Mask
  - We commonly call a `Series` with `dtype=bool` used for this context a **mask**. It usually makes your program more readable to save those masks in a variable. The following cell shows the exact same example, but adding a variable for readability for the mask.
- Multiple Conditions
  - `&` does an element-wise `and` to combine two masks
  - `|` does an element-wise `or` to combine two masks
  - `~` does an element-wise `not` of a single mask

### Location

- Can have 2 indexer

### Return Values

- If both the row and column indexers are a single value, returns a single value. This will be whatever the value is at the location so its type will be the same as the `dtype` of the column it comes from.
- If only one of the row and colum indexers is a single value (meaning the other is multiple values), returns a `Series`.
- If neither of the row and column indexers are single values (meaning both are multiple values), returns a `DataFrame`.

