# String 이용하기

### Q. String은 메모리에 어떻게 저장되는가?

A. String은 char의 배열이다. 객체지만 마치 기본자료형처럼 사용되는 독특한 객체라고 할 수 있다. 그래서 스트링 객체는 기본자료형처럼 리터럴로 생성할 수도, new 키워드로 객체로 생성할 수도 있다. 물론 리터럴로 생성해도 내부적으로는 객체를 생성하게 된다.

### Q. String 객체의 값을 변경할 수 있는가?

A. 없다. 스트링은 Immutable Object(변하지 않는 객체)이다. 우리가 리터럴값을 변경하는 것은 내부적으로 새로운 스트링 객체를 생성하여 주소값을 변경하는 것이다. 이는 Thread-safe(스레드 안전성)을 확보하는 코딩에 적합하다. 이 밖에도 Integer, Double, Character, BigInteger 와 같은 모든 숫자형 클래스들도 불변클래스이다.

### Q. 인터닝이란 무엇인가?

A. 모든 스트링 리터럴은 Constant pool(상수 풀)에 존재하는데, 스트링객체의 리터럴 값이 여기에 있으면 이를 참조하여 사용한다. 이를 String Interning(스트링 인터닝) 이라고 한다. 아래 예제 코드를 보자

```{.java}
@Test
public void stringIntern() {
  final String literal = "Hello";  // 리터럴
  final String object = new String("Hello");  // 객체
  final String intern = literal.intern();  // 리터럴의 인턴
  
  Assert.assertTrue(literal.equals(object)); // true
  Assert.assertFalse(literal == object);  // false
  Assert.assertTrue(literal.equals(intern));  // true
  Assert.assertTrue(literal == intern);  // true
}
```

테스트 결과를 보자. 1번과 2번은 크게 놀랍진 않다. 그러나 4번의 결과가 true인 것은 조금 놀랍다. 이것이 인터닝이다. literal의 리터럴이 존재하는 상수 풀에서 가리키는 데이터를 intern 객체가 그대로 가져가 사용하는 것이다. 조금 더 상세히 설명하자면 literal 객체가 생성 될 때, 값인 "Hello"를 Permanent Generation(줄여서 PermGen) 영역 내 상수 풀에 데이터를 넣는다. intern 객체가 literal.intern()을 통해 생성이 되는데 이때 인터닝이 발생하게 되어 동일한 값을 바라보는 객체가 된다. 

![](./JVM%20구조.png)

Constant Pool은 Method Area 내에 존재한다.
