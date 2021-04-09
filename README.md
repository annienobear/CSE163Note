# CSE163Note

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

## List Methods

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

## Python Models 

### Scripts

`.py` files, run using `python file_name.py`

### Interactive

Read Evaluate Print Loop

- Run in terminal 
- Exit using `Ctrl D` / `exit()`
- Jupyter notebooks



