
## Static 

자바의 클래스는 메모리의 static 영역에 적재되고  
new 연산자를 통해 만들어진 객체는 Heap 영역에 적재된다.

static 영역은 모든 객체가 메모리를 공유하고 Garbage collector 관여가 없는 반면  
heap 영역은 메모리를 공유하지 않고 GC 관여가 있다.  

static 변수와 메서드는 객체에 소속된 멤버가 아니라 클래스에 고정된 멤버이다.
-> 클래스가 메모리에 적재되면 객체를 생성하지 않고 즉시 바로 사용이 가능하다.  

static 키워드를 쓰지 않은 인스턴스 필드값과 메서드는 메모리를 따로 사용하기 때문에 서로 다른 것들이다.

```
class Number {
	static int stNum = 1;
	int inNum = 1;
}

public class Test {
	public static void main(String[] args) {
		Number test1 = new Number();
		Number test2 = new Number();
		
		test1.stNum++;
		test1.inNum++;
		System.out.println(test2.stNum); >> 2
		System.out.println(test2.inNum); >> 1
	}
}
```
---

## innerClass
