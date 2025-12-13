# 🌱 Spring 핵심 원리 - 기본편 학습 기록


<img width="1325" height="844" alt="certificate" src="https://github.com/user-attachments/assets/b89a0b41-f387-4867-ad85-5adbd010ee70" />

<br><br>



## 📌 회고

스프링이 객체 지향 설계를 돕기 위해 탄생한 배경과 철학이 인상 깊었으며, 직접 설계를 해보며 다형성과 DIP 등 객체 지향의 장점을 체감할 수 있었다.  
또한 스프링의 핵심 기능인 Bean 생성·의존관계 주입 과정을 깊이 이해하게 되었고, 앞으로 유연하고 확장성 높은 코드를 작성하고자 하는 동기부여가 되었다.


<br>

## 📚 학습 정리  


### 1. Spring · Spring Boot · 자바 애플리케이션의 이해
- 자바 애플리케이션은 **HTTP 요청을 받아 로직을 처리하고 응답을 반환하는 서버 프로그램**이다.  
- Spring은 IoC/DI/AOP/MVC 를 중심으로 다양한 기술(Spring Data, Security, Cloud 등)을 포함한 **거대한 생태계**다.  
- Spring Boot는 스프링을 더 쉽게 사용하도록 **의존성 관리(Starter), 자동 설정(Auto Configuration), 톰캣 내장 등**을 제공한다.


### 2. 스프링이 탄생한 이유 & 객체 지향 설계
- 과거 EJB의 복잡성·컨테이너 종속성을 해결하기 위해 스프링은 **순수 자바 객체(POJO)** 기반 개발을 목표로 등장했다.  
- 객체 지향의 핵심(추상화, 캡슐화, 상속, 다형성)을 통해 “**역할과 구현을 분리**”함으로써 유연한 설계를 가능하게 한다.  
- 특히 다형성은 확장에 열려 있고 변경에는 닫힌(OCP) 형태를 지원하지만, **역할 설계가 잘못되면 오히려 큰 변경이 필요**하다는 단점도 있다.


### 3. SOLID 핵심 원칙 정리
- **SRP:** 한 클래스는 하나의 책임만 가진다.  
- **OCP:** 확장에는 열려 있고 변경에는 닫혀 있어야 한다.  
- **LSP:** 역할에 맞게 올바르게 구현해야 한다.  
- **ISP:** 작은 인터페이스 여러 개가 큰 인터페이스 하나보다 낫다.  
- **DIP:** 구현체가 아니라 **추상화(인터페이스)**에 의존해야 한다.


### 4. Spring Container와 Bean 관리
- Spring Container는 **Bean 생성 → 의존관계 주입 → 초기화 → 소멸**까지 생명주기를 관리한다.  
- Bean 저장소는 “**빈 이름 : 빈 객체**” 형태의 매핑 테이블 구조를 가진다.  
- ApplicationContext는 BeanFactory의 기능 + 환경설정, 국제화, 이벤트 등 부가기능을 포함한 상위 컨테이너다.  
- 설정 정보는  
  - **Java 기반**: `AnnotationConfigApplicationContext`  
  - **XML 기반**: `GenericXmlApplicationContext`  
  로 적용할 수 있다.


### 5. DI(의존관계 주입) 방식과 @Configuration / @ComponentScan
- **@Configuration + @Bean**: 개발자가 의존성 생성 및 주입을 직접 구성하는 수동 DI.  
- **@ComponentScan + @Autowired**: 클래스를 자동 스캔하고 필요한 의존성을 자동 주입하는 자동 DI.  
- 자동 주입 시 구현체가 여러 개면 **@Primary 또는 @Qualifier**로 특정 Bean을 지정한다.  
- 생성자 주입을 권장하는 이유:  
  1) `final`로 불변 의존성을 보장할 수 있고  
  2) 테스트하기 수월하며 누락 위험이 없다.


### 6. 빈 스코프 & 생명주기 관리
- 빈 스코프는 객체의 **생명주기 범위**를 정의한다.  
  - `singleton` (애플리케이션 전역에서 하나만 생성)  
  - `prototype` (주입할 때마다 새로운 객체 생성)  
  - `request` (HTTP 요청 단위로 생성)  
- 초기화 / 소멸 콜백은  
  - `@PostConstruct`  
  - `@PreDestroy`  
  로 지정한다.

