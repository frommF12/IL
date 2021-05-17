
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

내부클래스는 변수처럼 인스턴스, static, 지역클래스로 나뉘며 유효범위(scope)와 접근성(accessibility)를 갖는다.(익명클래스도 있다.)  

인스턴스 클래스는 외부 클래스의 멤버들을 전부 접근할 수 있다.  
static 클래스는 static 멤버와 static 메서드에만 접근할 수 있다.  
지역클래스는 외부에서 접근할 수 없다.  
익명클래스는 클래스나 인터페이스를 선언과 객체의 생성을 동시에 한다. 그래서 단 한번만 사용될 수 있고 하나의 클래스만 만들 수 있는 일회용 클래스이다.  

하나의 클래스를 상속받거나 하나의 인터페이스만 구현할 수 있다.(둘 이상은 안된다!)  
내부클래스가 컴파일되면 외부클래스.class , 외부클래스명$내부클래스.class 형식으로 된다.  
만약 같은 이름을 가진 지역클래스가 있다면 외부클래스$1내부클래스.class, 외부클래스$2내부클래스.class와 같이 숫자를 통해 구별한다.  

### 인스턴스, static, 지역클래스별로 외부클래스의 멤버들중 접근 가능한 멤버들을 알아보는 코드이다.
```
public class Test {
	int instanceValue = 1;
	static int staticValue = 2;
	final int finalValue = 3;
	static final int staticFinalValue = 4;
	
	void testPrint() {
		System.out.println("외부클래스의 인스턴스 메서드");
	}
	class InstanceClass {
		int a = instanceValue;
		int b = staticValue;
		int c = finalValue;
		int d = staticFinalValue; // static 과 final이 동시에 붙으면 가능하다. (지역클래스도 동일)
//		// 인스턴스 클래스의 멤버로 static을 갖지 못한다.
//		static int e = staticValue;
//		static void print2() {}
		void print() {
			System.out.println(a + " "+ b + " " + c + " " + d);
			testPrint();
		}
	}
	
	static class StaticClass {
//		static class에서 instance 접근불가
//		int a = instanceValue;
		int b = staticValue;
//		finalValue도 인스턴스 변수이기 때문에 접근불가
//		int c = finalValue;
		int d = staticFinalValue;
		void print() {
			System.out.println(b +" "+ d);
//			testPrint(); 오류 발생, static 메서드에만 접근이 가능하다.
		}
	}
	
	void method() {
		int localValue = 5;
		final int flocalValue = 6;
		class LocalClass {
			int a = instanceValue;
			int b = staticValue;
			int c = finalValue;
			int d = staticFinalValue;
			int e = localValue;
			int f = flocalValue;
//			// 지역클래스도 static 멤버를 갖지 못한다.
//			static int g = staticValue;
//			static void print2() {}
			void print() {
				System.out.println(a + " "+ b + " "+ c + " " + d +" "+ e + " " + f);
				testPrint();
			}
		}
		LocalClass methodLocal = new LocalClass();
		methodLocal.print();
		
	}
	public static void main(String[] args) {
		Test test = new Test();
		InstanceClass testInstance = test.new InstanceClass();
		StaticClass testStatic = new StaticClass();
		testInstance.print();
		testStatic.print();
		test.method();
	}
}
```
