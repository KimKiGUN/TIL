### 모듈 활용

***

#### 1. re 모듈

```python
# Q1) 문자열의 단어수를 리턴받아 보자. str.split()
#str.split() : 문자열의 공백으로 구분하고 결과를 목록으로 리턴

str = 'fotmat_spec defaults to the empty string.'

res = str.split()               # 1
word_count = len(res)           # 2
print(res)
print(word_count)

#1 공백으로 단어 구분 (split)
#2 단어 대수 확인
```
['fotmat_spec', 'defaults', 'to', 'the', 'empty', 'string.']

6
***

```python
# Q2) 문자열의 단어수를 리턴받아 보자. 정규표현식
#import re -> 정규식 패턴을 컴파일 할 수 있는 모듈
#findall()
#'findall', 'finditer', 'fullmatch', 'functools', 'match', 'purge', 'search', 'split'

import re
str = 'Return a list of all non-overlapping matches in the string.'
res = re.findall('\w+', str)        #1
word_count = len(res)
print(res)
print(word_count)

#1 정규표현식 '\w+'' : any word character + one more
# regexr.com  or https://regex101.com/  ?, ^ , +  , * 
# \w  ->알파벳, 숫자, _ 중 하나를 의미한다.  
# \w+  ->알파벳, 숫자, _  문자가  하나이상 반복되는 것 
```
['Return', 'a', 'list', 'of', 'all', 'non', 'overlapping', 'matches', 'in', 'the', 'string']

11

***

```python
# Q3) str에서 공백의 개수를 출력해 보자.
str = 'Return a list of all non-overlapping matches in the string.'
res = re.findall('\s', str)        #1
space_count = len(res)
print(res)
print(space_count)

#1 정규표현식 '\s' : any white space character
```
[' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']

9

***
```python
# Q4) 리스트 객체에서 슬라이싱을 이용해서 삭제해보자.

m = ['kim','lee','park']*3
del m[1:3]                #1
print(m)

#1 m list에서 index = 1, 2 항 삭제
```
['kim', 'kim', 'lee', 'park', 'kim', 'lee', 'park']

***

### 2. pathlib 모듈 
1) 실행중인 Python 파일 경로확인  
2) 작업 디렉토리 경로 확인  
3) 작업 디렉토리 변경  

파일을 만드는 방법

- 1) pathlib.Path.touch() 방법
- 2) open() 방법 
- 3) os.system()

```python
from pathlib import Path      #1
path = Path()
path

#1 pathlib에서 Path만 참조하겠다.
```
WindowsPath('.')

***

```python
print(f'{Path.cwd()}')

# Path.cwd = 작업 경로를 확인
```
c:\ds_work\source_code

***

```python
from os import chdir
#print(dir(os))
path = Path('c:\Test')
print(f'{Path.cwd()}')

# 탐색기에서 사용되는 명령어를 가진 모듈
```
c:\Test

***

```python
from pathlib import Path
import os

Path('a.txt').touch()         #1

with open('b.txt', 'w') :
    pass

r = os.system(' abc >> e.txt')
print(r)

os.system('notepad.exe')      #2
os.system('mspaint.exe')

#1 파일 만들기
#2 파이썬 빅데이터 파이프라인을 구현할 때 몽고 또는 하둡 스토리지에 전송 구문
```
1

0

### 3. OS모듈
- 시스템 환경에  관한 함수  
- 디렉토리 , 파일 
os.walk() 
os.system() 
os.listdir()
os.path() 
os.environ() 
os.mkdir()
os.rename() 
os.remove() 

```python
import os
if os.name == 'nt':
    print('on Windows')
elif os.name == 'posix':
    print('on Mac or Linux')
print(os.name)
```
on Windows

nt

```python
import platform
pf = platform.system()
if pf == 'Windows':
    print('on Windows')
elif pf == 'Darwin':
    print('on Mac')
elif pf == 'Linux' :
    print('on Linux')
    
platform.system()

```

on Windows

'Windows'

```python
# Q1) makedirs', 'mkdir'를 이용해서 디렉토리를 생성해보자.  

import os
path = '.\dir\sub'  #1
os.mkdir(path)

#1 dir 밑에 sub 디렉토리 생성
```
***

```python
path_list = ['.\\dir\\sub1','.\\dir\\sub2', '.\\dir\\sub3']  #1
path = '.\dir\sub'
for path in path_list:
    os.mkdir(path) 
    
#1 dir 밑에 sub1, sub2, sub3 디렉토리 생성
```

***

```python
path = '.\\dir\\sub_dir1\\sub_dir2'
os.makedirs(path, exist_ok = True)

# dir > sub_dir1 > sub_dir2 생성
```

***

```python
for root, dirs, files in os.walk('.'):
    print(root)
    print(dirs)
    print(files)
```
.
['dir']
['a.txt', 'b.txt', 'e.txt']
.\dir
['sub', 'sub1', 'sub2', 'sub3', 'sub_dir1']
[]
.\dir\sub
[]
[]
.\dir\sub1
[]
[]
.\dir\sub2
[]
[]
.\dir\sub3
[]
[]
.\dir\sub_dir1
['sub_dir2']
[]
.\dir\sub_dir1\sub_dir2
[]
[]

***

```python
for root, dirs, files in os.walk('c:\\Python\\Python310'):
    for f in files:
        if 'abc.py' in f:
            print(os.path.join(root, f))
```

c:\Python\Python310\Lib\abc.py
c:\Python\Python310\Lib\_collections_abc.py
c:\Python\Python310\Lib\_py_abc.py
c:\Python\Python310\Lib\collections\abc.py
c:\Python\Python310\Lib\importlib\abc.py
c:\Python\Python310\Lib\importlib\_abc.py
c:\Python\Python310\Lib\site-packages\pip\_vendor\resolvelib\compat\collections_abc.py
c:\Python\Python310\Lib\site-packages\pip\_vendor\rich\abc.py
c:\Python\Python310\Lib\site-packages\pkg_resources\_vendor\importlib_resources\abc.py
c:\Python\Python310\Lib\site-packages\setuptools\_vendor\importlib_resources\abc.py
c:\Python\Python310\Lib\test\test_abc.py
c:\Python\Python310\Lib\test\test_importlib\abc.py
c:\Python\Python310\Lib\test\test_importlib\test_abc.py
