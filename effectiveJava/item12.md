# 12. toString을 항상 재정의하라

Object의 기본 toString 메서드가 우리가 작성한 클래스에 적합한 문자열을 반환하지 않는다.
PhoneNunber@adbbd 처럼 단순히 클래스이름@16진수해시코드를 반환한다.
따라서 PhoneNumber를 전화번호의 형태로 반환받으려면 모든 하위 클래스에서 재정의해야한다.

### toString 의 재정의
toString 을 잘 재정의 했다면 다음과같은 코드만으로 충분한 메세지를 담을 수있다.
```
System.out.println(phoneNumber + "에 연결할 수 없습니다.");
```

 - toString을 구현할 때는 반환값의 포맷을 문서화할지 정해야함.
 - 포맷을 명시하든 아니든 의도를 명확히 밝혀야 한다.
 - 포맷 명시 여부와 상관없이 toString이 반환한 값에 포함된 정보를 얻어올수 있는 API를 제공하자.
    * ex)phoneNumber 클래스는 지역코드, 프리픽스, 가입자 번호용 접근자임을 제공
 - 정적 유틸리티 클래스 및 대부분의 열거 타입은 toString을 제공할 필요가 없다.
 - 
##### 포맷 명시
```
/*
* 전화번호의 문자열 표현을 반환하다.
* 문자열은 "XXX-YYY-ZZZZ" 형태의 12글자로 구성된다.
* XXX는 지역 코드, YYY는 프리픽스, ZZZZ는 가입자 번호다.
* 각각의 대문자는 10진수 숫자 하나를 나타낸다.
*/
@Override public String toString() {
  return String.format("%03d-%03d-%04d", areaCode, prefix, lineNum);
```

##### 포맷 명시하지 않음.

```
/**
* 약물에 관한 대략적인 설명을 반환한다.
* 다음은 이 설명의 일반적인 형태이나,
* 상세 형색은 정해지지 않았으며 향후 변경될 수 있다.
* "[약물 #9: 유형=사람, 냄새=테레빈유, 겉모습=먹물]"
*/
@Override public String toString() { ...}
```