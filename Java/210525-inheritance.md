

### 상속
---

기존의 클래스를 재사용하여 클래스를 작성하는 것  

작성할 클래스 이름 뒤에 extends 키워드와 상속받을 클래스를 적어주면 된다.  

``` class Child extends Parent ```

상속하는 클래스를 조상, 부모, 상위, 기반 클래스라고 하며  

상속받는 클래스는 자식, 하위, 파생 클래스라고 한다.  

**자손 클래스는 부모 클래스의 모든 멤버를 상속받는다.**  

즉, 부모 클래스의 멤버변수나 메서드가 자동으로 자식 클래스에 추가된다.  

자식클래스에 멤버를 추가한다고 부모 클래스에도 추가되진 않는다.  

**부모의 생성자와 초기화 블럭은 상속되지 않는다. 멤버만 상속된다.**  

클래스간의 관계에서 형제관계같은 것은 없고 오로지 부모와 자식관계만 있다.  

자식 클래스가 부모 클래스의 모든 멤버를 상속받으니까   

자식 클래스를 (이 때는 부모클래스가 되는) 상속받는 자식 클래스가 있다면 부모 클래스와 부모의 부모 클래스의 모든 멤버를 상속받는거다.  

부모 클래스에서 멤버를 추가하거나 삭제하면 자식 클래스들도 똑같이 추가되고 삭제된다.  

클래스간의 상속관계를 맺어주면 자식 클래스의 공통적인 부분은 부모 클래스에서 관리할 수 있다.  

-> 약간 양날의 검인것 같다. 부모 클래스만 변경해도 상속받는 자식 클래스들에게 영향을 미치기 때문에   
관리가 편리할 수 있겠으나 어떤 문제를 일으킬지 모르는(?)  

**자식 클래스의 인스턴스를 생성하면 부모 클래스의 멤버와 자식 클래스의 멤버가 합쳐진 하나의 인스턴스로 생성된다.**  

---

### is a, has a 

클래스를 재사용하는 방법에는 상속이외에도 다른 방법이 있다.  

한 클래스의 멤버변수로 다른 클래스 타입의 참조 변수를 선언하는 것이다.   

즉 다른 클래스를 참조하는 것이다.  

예를 들어서 

```
class Circle {
  Point c = new Point();
  int r;
}

class Point {
  int x;
  int y;
}
```

Point 클래스를 재사용하는 방법이 있다. (포함한다고 한다.)  


클래스를 재사용할 때 상속관계와 포함관계 중 어떤 관계를 맺어줄건지 헷갈릴 때가 있다.  

그럴 땐 is a ( ~ 은 ~ 이다)  
       has a ( ~ 은 ~ 을 가지고 있다)를 이용하면 클래스 간의 관계를 설정할 때 도움이 될 수 있다.  
       
상속관계는 is a  
포함관계는 has a로 설명된다.  

1. 원은 점이다.  
2. 원은 점을 가지고 있다.   

-> 원과 점은 상속이 아닌 포함관계 

1. SportsCar는 Car이다.   
2. SportsCar는 Car을 가지고 있다.  

-> 스포츠카는 차; 상속관계   

자바의 정석 3rd 참고
