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