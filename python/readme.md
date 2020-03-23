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
