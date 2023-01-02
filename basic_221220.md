### 변수 생성 규칙

1. 변수명은 다음 문자로 섞어서 사용할 수 있다.
- 소문자(a ~ z)
- 대문자(A ~ Z)
- 숫자(0 ~ 9)
- 언더스코어(_)

2. 반드시 문자로 시작되어야 한다.
3. 예악어를 제외하고 선언한다.

```python
import sys
sys.path

# 현재 파이썬의 라이브러리를 참조하는 기본 값을 확인하는 모듈
# sys.path - 참조 모듈 경로
```
['c:\\ds_work\\source_code',
 'C:\\Anaconda3\\python39.zip',
 'C:\\Anaconda3\\DLLs',
 'C:\\Anaconda3\\lib',
 'C:\\Anaconda3',
 '',
 'C:\\Anaconda3\\lib\\site-packages',
 'C:\\Anaconda3\\lib\\site-packages\\win32',
 'C:\\Anaconda3\\lib\\site-packages\\win32\\lib',
 'C:\\Anaconda3\\lib\\site-packages\\Pythonwin',
 'C:\\Anaconda3\\lib\\site-packages\\IPython\\extensions',
 'C:\\Users\\PC\\.ipython']

 ```python
 import keyword
keyword 

# 키워드를 관리하는 모듈 파일의 경로 확인
```
<module 'keyword' from 'C:\\Anaconda3\\lib\\keyword.py'>


```python
dir(keyword)

# keyword 모듈의 내용을 확인
```
['__all__',
 '__builtins__',
 '__cached__',
 '__doc__',
 '__file__',
 '__loader__',
 '__name__',
 '__package__',
 '__spec__',
 'iskeyword',
 'issoftkeyword',
 'kwlist',
 'softkwlist']

 ```python
 print(keyword.kwlist)

# 모듈에서 관리하는 객체를 참조
```

print(keyword.kwlist)

# 모듈에서 관리하는 객체를 참조
print(keyword.kwlist)
​
# 모듈에서 관리하는 객체를 참조
['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']

### 파이썬에서 사용되는 자료형 5가지
- 숫자, 문자, 리스트, 튜플, 사전 자료형

```python
# List : [] 안에 임의의 객체를 순서있게 나열하는 자료형
# 하이썬은 나열된 데이터의 인덱스를 0부터 시작한다.
# len(list[]) : 리스트 객체의 길이를 리턴해보자.

my_list = []
type(my_list)
len(my_list)
```
0

```python
my_list = [1, 2, 3, 4, 5]
type(my_list)
my_list[0] = 100     #1
len(my_list)         #2
print(my_list)
my_list[3] = 3000    #3
print(my_list)

#1 my_list의 0번째 값을 100으로 변경
#2 list 객체의 길이
#3 my_list의 3번째 값을 3000으로 변경
```

[100, 2, 3, 4, 5]

[100, 2, 3, 3000, 5]

```python
my_list = [1, 2, 3, 4, [41, 42, 43], 5, 6]   #1
type(my_list)
print(my_list)
print(my_list[0])
print(my_list[1])
print(my_list[2])
print(my_list[3])
print(my_list[4])
print(my_list[4][0])                        #2
print(my_list[4][1])
print(my_list[4][2])

#1 중첩 객체
#2 my_list의 3번째 객체 중([41, 42, 43] 중) 0번째 = 41
```

[1, 2, 3, 4, [41, 42, 43], 5, 6]

1

2

3

4

[41, 42, 43]

41

42

43

```python
# Tuple : () 안에 임의의 객체를 순서있게 나열하는 자료형
# 리스트와 다르게 값을 수정할 수 없다.

my_list = (1, 2, 3, 4, (41, 42, 43), 5, 6)
print(type(my_list))
print(my_list)
print(my_list[0])
print(my_list[1])
print(my_list[2])
print(my_list[3])
print(my_list[4])
print(my_list[4][0])
print(my_list[4][1])
print(my_list[4][2])
```

<class 'tuple'>

(1, 2, 3, 4, (41, 42, 43), 5, 6)

1

2

3

4

(41, 42, 43)

41

42

43

```python
# 사전형 자료 : {key : value} 로 선언된 요소로 순서 없는 자료형

my_dict = {'a' : 'apple', 'i' : '나는', 'am' : '입니다', 'pyhton' : '파이썬'}
print(type(my_dict))
print(my_dict)
```

<class 'dict'>

{'a': 'apple', 'i': '나는', 'am': '입니다', 'pyhton': '파이썬'}

```python
print(dir(dict))
```
['__class__', '__class_getitem__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__ior__', '__iter__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__or__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__ror__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'clear', 'copy', 'fromkeys', 'get', 'items', 'keys', 'pop', 'popitem', 'setdefault', 'update', 'values']

```python
print("values = ", my_dict.values())
print("keys = ", my_dict.keys())
```
values =  dict_values(['apple', '나는', '입니다', '파이썬'])

keys =  dict_keys(['a', 'i', 'am', 'pyhton'])

