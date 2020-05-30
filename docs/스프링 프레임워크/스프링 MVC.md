# 스프링 핵심 기능과 애플리케이션 컨텍스트

이번 챕터의 설명을 들어가기 전에 애플리케이션 컨텍스트가 무엇인지 설명하는 것이 중요할 것 같다. 개념적으로는 Bean을 관리하는 BeanFactory의 확장된 의미이다. 아래 코드를 보면 실제로 BeanFactory(ListableBeanFactory)를 상속한다. 

```java
package org.springframework.context;

import org.springframework.beans.factory.HierarchicalBeanFactory;
// ...생략

public interface ApplicationContext extends EnvironmentCapable, ListableBeanFactory, HierarchicalBeanFactory, MessageSource, ApplicationEventPublisher, ResourcePatternResolver {	
// ...
}
```

즉, 애플리케이션 컨택스트는 빈을 관리하면서 동시에 다른 추가적인 컨테이너 기능을 확장하여 사용하는 것이다. BeanFactory는 너무 저수준이기 떄문에 애플리케이션 컨텍스트를 선호한다

### Q. 스프링은 어떻게 웹 애플리케이션을 제공하는가?

스프링은 이게 문제다. 어떤 개념 하나를 설명하려면 다른 개념을 가져와 설명해야 한다. 이 질문도 일단 Dependency Injection(의존성 주입)에 대한 선이해가 필요하다. 

먼저 아래 코드를 통해 의존성부터 살펴보자.

```java
// 직원
@Data
class Emp {
    private long empId;  // 사원번호
    private String name; // 사원명
    private long deptId; // 부서객체
}
// 부서
@Data
class Department {
    private long deptId;  // 부서번호
    private String name; // 부서명
}
```

위 코드는 간단히 직원과 부서관계를 나타내며, 각 getter/setter는 생성 Lombok으로 생성되었다고 가정한다. 순조롭게 개발이 진행되던 중에 Department.setName()이 Emp.setName()과 혼란스러울 것 같아 na



### Q. 어떻게 스프링 MVC에서 쉽게 테스트할 수 있는 웹 컨트롤러를 만들 수 있는가?



### Q. 서버측 로직을 요청 결과 표시와 어떻게 분리해서 유지하는가?



### Q. 스프링은 다른 뷰 템플릿 엔진들과 함께 동작하도록 어떻게 설정할 수 있는가?