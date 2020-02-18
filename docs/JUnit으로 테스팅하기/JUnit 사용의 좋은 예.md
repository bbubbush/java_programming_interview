# JUnit 사용의 좋은 예



### Q. 테스트가 성공인지 어떻게 증명할 수 있는가?

테스트의 결과를 확인하기 위해 JUnit은 몇가지 정적 메서드를 지원한다.

- assertEqueals : 두 객체의 equals 메서드 값이 같은지 비교한다.
- assertTrue & assertFalse : 주어진 상태를 각 Boolean 값과 비교한다. 
- assertNotNull : 객체가 Not null인지 확인한다.
- assertArrayEquals : 두 배열에 같은 값이 있는지 확인한다. 

위 메서드를 활용해서 개발자는 테스트의 예상되는 결과를 실제 결과와 비교하면 된다. 예를 들어 null이 아닌 어떤 결과가 예상되는 메서드는 assertNotNull(member) 처럼 결과를 예측한다.

위에 기록한 테스트 정적 메서드들은 기본적으로 입력받는 파라미터들 앞에 String 파라미터를 추가할 경우, 실패시 메세지를 설정할 수 있다. assertNotNull("This is null.", member)  처럼 말이다. 이렇게 메세지를 활용하면 테스트가 실패해도 상대방에게 어떤 문제가 있었는지 나타낼 수 있다. 물론 시간이 촉박한 상황에서는 생략해도 괜찮다.



### Q. 어떻게 특정 예외를 예상할 수 있는가?



