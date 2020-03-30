# Java

## 숫자로 된 char를 int로 변경하는 방법

```java
char c = '1';
int result1 = (int)c;
//49
int result2 = Character.getNumericValue(c);
//1
```

보통 첫번째 방법으로 int로 캐스팅을 많이한다.

특히 알고리즘 문제를 풀 때 많이 사용하는데 명시적 타입 캐스팅을 하게 되었을 때 char값은 아스키코드값으로 변경되기 때문에 1이 아닌 49로 변경되게 된다.

그래서 숫자를 변경할때는 번거롭게 '0' 또는 48을 빼주는 형태로 숫자로 변환을 해왔었는데 Character wrapper class에 좋은 메소드가 있었다.

getNumericValue() 메소드를 사용하면 숫자로 된 char형을 숫자형태 그대로 반환해준다.