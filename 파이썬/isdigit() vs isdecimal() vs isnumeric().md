## isdigit() ,isdecimal() ,isnumeric()

### 공통점 
- 셋 다 평범한 숫자 문자열의 경우 true 반환

```
A = “123123”
print(a.isdigit())
print(a.isdecimal())
print(a.isnumeric())
```
와 같이 평범한 숫자 들만 있는 경우 다음과 같이 True 만 반환 한다.

```
True
True
True
```

#### 차이점
```aidl
a = '3²'
print(a.isdigit())
print(a.isdecimal())
print(a.isnumeric())
```
```

```


의 경우
True
False
True

를 반환함.

isdigit() - 단일 글자가 ‘숫자’모양이면 무조건 true 반환 숫자처럼생기면 다 됨.

isdecimal() - 문자열이 int 형으로 변환이 가능한지 ?

isnumeric() 숫자값 포현에 해당하는 문자열 까지 인정
제곱근, 분수, 거듭제곱, 특문까지 인정.