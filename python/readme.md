# Python

## 파이썬 반복문에서 index에 접근하는 방법

### len() 함수 이용

```python
arr = [1,2,3]
for idx in range(len(arr)):
	print(idx, arr[idx])
```

in 이후를 리스트를 바로 접근하는 것이 아닌 길이로 접근해 인덱스로 다시 리스트에 접근하는 방법이 있다.

### enumerate() 함수 이용

```python
arr = [1,2,3]
for idx, val in enumerate(arr):
	print(idx, val)
```

enumerate 함수는 내장함수로써 매개변수로 들어오는 자료형의 index와 value를 enumerate 객체로 리턴한다.

## pycharm 모듈 import 에러

> This inspection detects names that should resolve but don't. Due to dynamic dispatch and duck typing, this is possible in a limited but useful number of cases. Top-level and class-level items are supported better than instance items.

위와 같은 에러가 난다면 File > Setting > Project > Project Structure > 모듈이 포함된 폴더 클릭 후 Source 버튼 체크

## 실행 시간 체크

python 코드를 작성하다보면 실행 시간을 측정해야 할 일이 생긴다.

다음과 같이 측정하면 쉽게 코드의 실행 시간을 알 수 있다.

```python
import time

start = time.time()
# 코드 시작
# ==========
# 코드 끝
print("time : ", time.time() - start)
```

단위는 초단위 이다.

## lambda 표현식

```python
def func(x):
    if x > 0:
        return x
    else:
        return None
```

위의 함수를 아래와 같이 표기해 익명 함수로 사용할 수 있다.

```python
lambda x : x > 0
```

주로 함수의 매개변수 전달용으로 사용한다.

## filter

filter는 파이썬의 built-in 함수로써 첫번째 매개변수로 함수를 두번째 매개변수로 iterable 한 변수를 입력받아 특정 조건에 일치하는 값만을 추출하는 용도로 사용된다.

```python
def func(x):
    if x > 0:
        return x
    else:
        return None

# origin
origin_list = list(filter(func, range(-5, 10)))
print(origin_list)
# lambda expression
lambda_list = list(filter(lambda x : x > 0, range(-5,10)))
print(lambda_list)
# generator expression
gen_list = [i for i in range(-5,10) if i > 0]
print(gen_list)
```

위와 같이 간단한 조건은 lambda 또는 generator 표현방식으로 간단하게 구현이 가능하다.

## collections.Counter

collections 모듈의 Counter 클래스는 중복값을 카운팅해주는 로직을 직접 구현하지 않고 쉽게 사용할 수 있도록 도와준다.

```python
from collections import Counter

def countLetters(word):
    counter = {}
    for letter in word:
        if letter not in counter:
            counter[letter] = 0
        counter[letter] += 1
    return counter

print(countLetters('hello world'))
# out = {'h': 1, 'e': 1, 'l': 3, 'o': 2, ' ': 1, 'w': 1, 'r': 1, 'd': 1}
print(Counter('hello world'))
# out = {'h': 1, 'e': 1, 'l': 3, 'o': 2, ' ': 1, 'w': 1, 'r': 1, 'd': 1}
print(Counter('hello world').most_common())
# out = [('l', 3), ('o', 2), ('h', 1), ('e', 1), (' ', 1), ('w', 1), ('r', 1), ('d', 1)]
print(Counter('hello world').most_common(2))
# out = [('l', 3), ('o', 2)]
```

collections 모듈은 별도의 설치없이 설치가 가능하며 위의 countLetters 함수의 기능을 Counter 클래스만으로 동일하게 수행할 수 있다.

또한 dict type으로 카운팅이 완료 된 후 most_common() 함수를 사용하면 높은 순으로 정렬되며 매개변수로 숫자를 주게 되면 원하는 만큼의 순위를 자를수 있게 된다.

## list()

파이썬 객체인 리스트를 만듭니다.

매개변수로 iterable(반복가능한) 변수를 넣으면 해당 변수를 list형태로 변환해서 리턴해줍니다.

```python
# empty list
print(list())

# vowel string
vowel_string = 'aeiou'
print(list(vowel_string))

# vowel tuple
vowel_tuple = ('a', 'e', 'i', 'o', 'u')
print(list(vowel_tuple))

# vowel list
vowel_list = ['a', 'e', 'i', 'o', 'u']
print(list(vowel_list))
```

###### result

```
[]
['a', 'e', 'i', 'o', 'u']
['a', 'e', 'i', 'o', 'u']
['a', 'e', 'i', 'o', 'u']
```

