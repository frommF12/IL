

## String
---

### String 객체와 리터럴

자바에서 String은 java.lang 패키지에 있는 String 클래스의 객체이다.  

특이하게도 원시 타입이 될 수도 있고 참조 타입이 될 수도 있다.  

String변수를 선언할 때 리터럴 값을 넣으면 원시 타입이(primative)되고 new 연산자를 통해 객체로 만들면 참조 타입(reference)으로 만들어진다.  

둘의 차이점은 원시 타입일 경우에는 스택에 저장되고 참조 타입은 힙 영역에 저장된다.  
 
또한 같은 내용의 값을 가지고 있을 때는 리터럴로 선언할 시 변수들이 하나의 메모리를 공유하지만 객체는 따로 만들어서 메모리를 더 소비한다.  

== 연산자는 참조 타입을 비교할 때는 주소를 비교하기 때문에 문자열 내용의 값을 비교하고 싶다면 equlas() 메서드를 사용해야 한다.  

String은 불변이다. 리터럴이 같을 때 공유하기 때문에 만약 중간에 값이 바뀐다면 공통 데이터를 갖고 있던 변수들도 영향을 받게 되므로 불변이다.  

그래서 String을 조작하면 기존의 값이 바뀌는 게 아니라 새로운 String을 만든다. (ex. str1 + str2)  

---
### StringBuilder / StringBuffer

StringBuilder는 String과 String을 더할 때 새로운 객체를 만드는 것이 아니라 기존의 데이터에 더하는 방식을 사용한다.  

그래서 String 객체에 비해 속도도 빠르며 부하가 적다.  

StringBuilder.append() 메서드에 더하고 싶은 문자열을 인자로 주면 기존의 문자열에 인자값이 더해진다.  

StringBuilder와 StringBuffer의 차이점은 동기화 유무이다.  

StringBuffer는 동기화 키워드를 지원하여 멀티쓰레드 환경에서 안전하다.  

StringBuilder는 동기화를 지원하지않지만 대신에 단일쓰레드 환경에서의 성능은 StringBuffer보다 뛰어나다.  

> 쓰레드 부분은 아직 잘 몰라서 구글링을 했다. ^^ 