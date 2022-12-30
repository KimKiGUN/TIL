# 내장 함수
> 2022년 12월 30일

## 내장함수
- `__builtins__` 안에 
들어가있는 함수
- import 없이 사용되는 함수 : 내장함수
- dir() 로 목록 확인

***
### abs(x)
- x의 절대값 반환
```python
print(abs(-10))
```
`10`

***

### all(iterable)
- 모든 요소가 참이면 True, 아니면 False
- 0이 하나라도 있으면 False
- iterable : 반복 가능한 자료형, 각각의 요소를 하나씩 리턴하는 형태
- for문을 사용할 수 있는 자료형 -> 리스트, 튜플, 집합, 딕셔너리

```python
print(all([1,2,3]))
print(all([0,1,2,3]))
print(all([True, True, 1, 3, 0]))
print(all([True, True, 1, 3, 0, None])) 
```
`True
False
False
False
`
***

### any(iterable)
- 하나라도 참이면 True, 모두 거짓이면 False
- all, any, in(data or data or..), not in(data or data or...) 한 세트
```python
print(any([0,0,0]))
print(any([0,1,2,3]))
print(any([0,"",[]])) #1
print(any([None,None])) 

#1 빈문자열, 빈리스트, None 은  False
```
`False
True
False
False
`
***
### chr(), ord()
- 아스키 코드 값에 해당하는 문자 <----> 코드값

```python
print(chr(97)) 
print(chr(65)) 
print(chr(13)) # enter
```
`a A`

```python
print(ord('a')) 
print(ord('0')) 
print(ord('\n')) # new line
print(ord(' ')) 
print(ord('\r')) #  enter
print(ord('\t'))
print(ord(','))
```

`97
48
10
32
13
9
44`

***

### divmod(a, b)
- a를 b로 나눈 몫과 나머지를 튜플형태로 리턴

```python
print(divmod(7, 3))
```
`(2, 1)`

***

### enumerate(iterable, start = 0)  
- 반복의 객체와 인덱스 값을 포함해서 리턴
- start 인덱스 수치 지정 가능
```python
print(enumerate(['kim', 'lee', 'park']))
for name in enumerate(['kim', 'lee', 'park']) :
    print(name)
```

`<enumerate object at 0x000001E49DB51280>`

`(0, 'kim')`

`(1, 'lee')`

`(2, 'park')`

***

```python
for i, name in enumerate(['kim','lee','park'],start=1) :
    print(i, name)
    
for i, name in enumerate(['kim','lee','park'],start=101) :
    print(i, name)
```

`1 kim`

`2 lee`

`3 park`

`101 kim`

`102 lee`

`103 park`

***

### filter(function or None, iterable)
- 반복의 객체를 function 임의로 필터링해서 리턴 
- `_filter object`

```python
def positive(x):
    return x > 0

print(filter(positive, [0, -1, 5, -7, 10]))
print(list(filter(positive, [0, -1, 5, -7, 10])))
```
`<filter object at 0x000001E49DB0D1F0>`

`[5, 10]`

```python
def even_n(x):
    if x % 2 ==0 :
        return x
print(list(filter(even_n, [0, 1, 2, 3, 4, 5, 6, 7, 8])))
```
`[2, 4, 6, 8]`

***

```python
#Q1) 리스트 데이터 중 25 이상인 데이터를 필터링하자.

my_list = [1, 65, 23, 4, 6, 7, 25, 77]
res = []

for num in my_list:
    if num >=25 :
        res.append(num)
print(res)
```
`[65, 25, 77]`

```python
#Q2) Q1을 filter 함수를 이용해 해결하자.

my_list = [1, 65, 23, 4, 6, 7, 25, 77]

def fil(num):
    return num >= 25

print(list(filter(fil, my_list)))
```
`[65, 25, 77]`

```python
# Q3) Q2를 람다식으로 변환해보자.

my_list = [1, 65, 23, 4, 6, 7, 25, 77]

res = list(filter(lambda x: x >=25, my_list))
print(res)
```
`[65, 25, 77]`

```python
# Q4) 이중 리스트를 필터링 해보자. 가격이 1500원 이상인 과일만 추출해보자.

fruits = [['apple', 1000], 
          ['banana', 3000],
          ['pineapple', 5000],
          ['kiwi', 1100],
          ['blueberry', 7500]]

res = list(filter(lambda x : x[1] >= 1500  , fruits))
print(res)
```
`[['banana', 3000], ['pineapple', 5000], ['blueberry', 7500]]`

```python
# Q5) dict 타입을 필터링 해보자.  key 값이 0이상인 값만 출력하자.
m_dict = {-2 : 'a', -1 : 'bc', 0 : 'd', 1 : 'e' }
print(m_dict.items())

res = list(filter(lambda x : x[0] >= 0, m_dict.items()))
new_dict = dict(res)
print(new_dict)
```
`dict_items([(-2, 'a'), (-1, 'bc'), (0, 'd'), (1, 'e')])`

`{0: 'd', 1: 'e'}`

```python
# Q6) Q5에서 value가 a인 값만 출력하자.
m_dict = {-2 : 'a', -1 : 'bc', 0 : 'd', 1 : 'e' }

res = list(filter(lambda x : x[1] == 'a', m_dict.items()))
print(res)

new_dict = dict(res)
print(new_dict)
```

`[(-2, 'a')]`

`{-2: 'a'}`

```python
# Q7) Q5를 내포된 for 문으로 해결하자.
m_dict = {-2 : 'a', -1 : 'bc', 0 : 'd', 1 : 'e' }

res = {k : v for k, v in m_dict.items() if k >= 0}
new_dict = dict(res)
print(new_dict)
```

`{0: 'd', 1: 'e'}`

```python
# Q8) Q6을 내포된 for 문으로 해결하자.
m_dict = {-2 : 'a', -1 : 'bc', 0 : 'd', 1 : 'e' }

res = {k : v for k, v in m_dict.items() if v == 'a'}
new_dict = dict(res)
print(new_dict)
```
`{-2: 'a'}`

```python
# Q9) dict타입을 a 만 필터링 해보자. 내포된 for 문으로
m_dict = {-2 : 'a', -1 : 'bc', 0 : 'd', 1 : 'e' , 2 : 'a'}
res = {}
for k, v in m_dict.items():
    if v == 'a':
        res[k] = v
        
print(res)
```
`{-2: 'a', 2: 'a'}`

***

### 파이썬에서 10진수를 16진수 문자열로 변환하는 방법
1) hex()
2) format()
3) f-string f'{}'

```python
# 1) hex()  정수를 0x 접두사가 붙는 소문자 16진수 문자열로 변환
x = 0x569F
print(hex(7)) 
print(type(hex(7))) 
print(hex(10))
print(hex(1234)) 
```
`0x7
<class 'str'>
0xa
0x4d2`

```python
# 2) format()
#    #x : 0xff / #X : 0Xff / x : ff / X : FF
su = 255
hex = format(su, '#x')
print(hex)

hex = format(su, '#X')
print(hex)

hex = format(su, 'x')
print(hex)

hex = format(su, 'X')
print(hex)
```
`0xff
0XFF
ff
FF`

```python
# 3) f-string
#    #x : 0xff / #X : 0Xff / x : ff / X : FF
su = 255
hex = f'{su : #x}'
print(hex)

hex = f'{su : #X}'
print(hex)

hex = f'{su : x}'
print(hex)

hex = f'{su : X}'
print(hex)
```
` 0xff
 0XFF
 ff
 FF`

 ***
 ### map(func, iterables)
- iterables 각 요소를 함수에 전달해서 수행된 결과를 리턴한다.

```python
def increase(x):
    return x + 1

print(map(increase, [1, 2, 3, 4, 5]))
print(list(map(increase, [1, 2, 3, 4, 5])))
```

`<map object at 0x000001E49DBFEA00>`

`[2, 3, 4, 5, 6]`

***

### pow(), round()
- pow(x, n) : x를 n제곱한 결과값
- round(number, ndigits) : 반올림 하여 반환 (ndigits : 표현할 소수 이하 자리수)

```python
print(pow(10,3))
print(pow(10, -1))
```
`1000
0.1`

```python
print(round(3.141592,3))
print(round(3.141592,0))
print(round(126.41592,-1))
print(round(123.141592,-2))
print(round(1243.141592,-3))
```
`3.142
3.0
130.0
100.0
1000.0`

***

### zip(iterable)
- 각 iterable에서 동일한 인덱스의 요소를 추출하여 묶어서 튜플 형태로 반환
- zip 객체로 반환하고 내부에 iterable 자료형으로 구성되어 있으므로 형변환해서 사용 

```python
print(zip([1,2,3],[4,5,6]))
print(list(zip([1,2,3],[4,5,6])))
```

`<zip object at 0x000001E49DC200C0>`

`[(1, 4), (2, 5), (3, 6)]`

```python
keys = ('apple', 'banana', 'grape')
values = (1500, 3000, 4500)
print(tuple(zip(keys, values)))
result = dict(zip(keys, values))
print(result)
```

`(('apple', 1500), ('banana', 3000), ('grape', 4500))`

`{'apple': 1500, 'banana': 3000, 'grape': 4500}`
