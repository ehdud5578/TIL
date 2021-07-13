# Item 10 equals는 일반 규약을 지켜 재정의하라.

 equals 는 재정의가 쉬워보이지만, 함정이 있기 때문에 신중히 재정의해야한다.
 다음에 열거한 상황에서는 재정의하지 않는 것이 최선이다.
 - 각 인스턴스가 본질적으로 고유하다.
 - 인스턴스의 '논리적 동치성'을 검사할 일이 없다.
 - 상위 클래승서 재정의한 equals가 하위 클래스에도 딱 들어맞는다.
 - 클래스가 private 이거나 package-private이고 equals 매서드를 호출할 일이 없다.

## equals 를 재정의해야할 때

#### 객체 식별성이 아니라 논리적 동치성을 확인해야 할때

주로 값 클래스들이 여기에 해당한다. equals가 논리적 동치성을 확인하도록 재정의해두면
Map의 키와 Set의 원소로 사용할 수 있게됨.

## Object 명세에 적힌 규약
equals 메서드는 동치관계(equivalence relation)를 구현하며, 다음을 만족한다.
 - 반사성(reflexivity) : null이 아닌 모든 참조 값 x에 대해, x.equals(x) 는 true 이다.
 - 대칭성(symmetry) : null이 아닌 모든 참조 값에 x,y에 대해, x.equals(y) 가 true 이면, y.equals(x)도 true 이다.
 - 추이성(transitivity) : null이 아닌 모든 참조 값 x,y,z에 대해, x.equals(y)가 true 이고, y.equals(z)도 true 이면, x.equals(z)도 true 이다.
 - 일관성(consistency) : null이 아닌 모든 참조 값 x,y에 대해, x. equals(y) 를 반복해서 호출하면 항상 true 를 반환하거나 항상 false를 반환한다.
 - null-아님 : null 이 아닌 모든 참조 값 x에 대해, x.equals(null)은 false다.

**일반적으로 대칭성을 만족시키지 못하는 문제가 발생한다.** 자식.equals(부모) = true 이지만 부모.equals(자식) = false 가 나올 가능성이 크다.

