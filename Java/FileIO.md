

## 파일 입출력

### 입출력이란 

컴퓨터 내부 또는 외부의 장치와 프로그램간 데이터를 주고 받는 것
ex) 키보드로부터 데이터를 입력받음, 콘솔창에 데이터 출력 등

## 스트림

### 스트림이란 

자바에서 입출력을 수행할려면 두 대상을 연결하고 데이터를 전송할 수 있는 연결통로가 필요하다.  

그것을 스트림이라고 한다. 스트림은 데이터를 운반하는데 사용되는 통로이다.  

스트림은 단방향통신만 가능하기 때문에 입출력을 수행하려면 입력 스트림, 출력 스트림이 각각 필요하다.  

스트림은 먼저 보낸 데이터를 먼저 받는 큐(queue)와 같은 FIFO구조이다.  

스트림은 3가지로 나뉜다.  

바이트기반 스트림, 문자기반 스트림, 보조스트림  

---
### 바이트 기반 스트림

바이트 기반 스트림은 데이터를 1 byte 단위로 전송한다.  

입력 스트림은 InputStream, 출력 스트림은 OutputStream인 추상클래스가 있다.  

입/출력대상의 종류에 따라 추상클래스를 상속받아 각각 구현되어있다.  
ex) FileInputStream, FileOutputStream, ByteArrayInputStream 등  

---
### 보조 스트림

스트림의 기능을 보완하기 위해 보조스트림이 제공된다.  

실제 데이터를 주고받는 스트림이 아니기 때문에 데이터를 입출력할 수 있는 기능은 없지만,  

스트림의 기능을 향상시키거나 새로운 기능을 추가할 수 있다.  

그래서 스트림을 생성한 다음에 보조스트림을 생성해야한다.  

``` 
FileInputStream fis = new FileInputStream("text.txt");
BufferedInputStream bis = new BufferedInputStream(fis);
bis.read();
```
text파일을 읽기위해 파일 입력 스트림을 사용할 때 버퍼를 사용하는 보조 입력 스트림을 사용해서  
입력 성능을 향상시킬 수 있다.  

실제 입력기능은 파일 입력 스트림이 하는 것이고 보조 입력 스트림은 버퍼만 제공한다.  

버퍼를 사용한 입출력의 성능이 좋기 때문에 대부분의 경우에 버퍼를 이용한다.  

보조 입/출력 스트림은 FilterInput/OutputStream의 자손들이고  

FilterI/OStream은 Input/OutputStream의 자손이라서 모든 보조스트림은 Input/OutputStream의 자손들이다.  

---
### 문자기반 스트림

바이트기반의 스트림은 입출력 단위가 1 byte이다.  

자바에서는 char형이 2 byte이기 때문에 바이트 기반의 스트림으로 2 byte 문자를 처리하는에 어려움이 있다.  

그래서 문자 데이터를 입출력할 때는 문자기반 스트림을 사용한다.  

문자기반 스트림에서 InputStream은 Reader, OutputStream은 Writer이다.  

사용목적과 방식은 바이트 기반 스트림, 바이트 기반 보조스트림과 다르지 않기 때문에 똑같이 사용하면 된다.  
(바이트 기반은 byte[]를 썼다면 문자 기반은 char[]을 사용한다. / 추상메서드도 다르다.)

---
### System.out.println()

흔히 사용하는 System.out.println()은 무엇일까  

매일 사용하는 메서드인데 어떤 건지는 대략 아는게 좋지 않을까?  

일단 System은 java.lang 패키지에 있는 상속불가능한 final 클래스이다.  

System의 static final 멤버 중 out이 있다.   

out은 PrintStream형 참조변수이다.  

PrintStream은 무엇일까   

PrintStream은 데이터를 기반스트림에 다양한 형태로 출력할 수 있는 print, println, printf와 같은 메서드를 오버로딩하여 제공한다.  

PrintWriter도 있지만 System.out이 PrintStream이라 둘 다 사용된다고 한다.  

PrintWriter가 더 다양한 언어의 문자를 처리하는데 적합하기 때문에 가능하면 PrintWriter를 사용하는 것이 좋다.  

결국 System의 static 변수는 PrintStream의 참조변수이기 때문에 PrintStream의 메서드를 사용할 수 있다.  

PrintStream은 바이트 기반 보조 스트림으로 FilterOuputStream을 상속받고 print같은 메서드를 제공한다.  

PrintStream은 FilterOutputStream을 통해 OutputStream에 접근할 수 있고  
(생성자 단계에서 FilterOutputStream 생성자를 통해 OutputStream 참조변수를 만든다)    

OutputStream의 write를 오버라이딩해서 println같은 메서드를 구현한 것 같다.  





