
## eqauls 와 hashcode

https://jisooo.tistory.com/entry/java-hashcode%EC%99%80-equals-%EB%A9%94%EC%84%9C%EB%93%9C%EB%8A%94-%EC%96%B8%EC%A0%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B3%A0-%EC%99%9C-%EC%82%AC%EC%9A%A9%ED%95%A0%EA%B9%8C 블로그를 참고하고 쓰는 내용이다.  

equals와 hashcode는 Object class에 정의되어 있어 모든 객체는 이 둘을 상속받는다.  
**equals**는 ==와 비슷해보이나 내부적으로는 전혀 다르다.  
== 는 원시타입을 비교할 땐 값을 비교하고 참조타입을 비교할 땐 주소값을 비교하므로 값을 비교하고 싶다면 equals를 사용해야한다.  
참고로 primitive 타입이 == 비교를 통해 값 비교가 가능한 이유는 아래와 같다.

블로그 글들을 보다가 왜 원시타입은 값을 비교하는지 알려주는 글이 있어서 가져왔다.
> 변수 선언부는 Java Runtime Data Area의 Stack 영역에 저장이 되고, 해당 변수에 저장된 상수는 Runtime Constant Pool에 저장되어있다.  
Stack의 변수 선언부는 해당 Runtime Contant Pool의 주소값을 가지게 되고, 만약 다른 변수도 같은 상수를 저장하고 있다면,   
이 다른 변수도 같은 Runtime Contant Pool의 주소값을 가지게 때문에 엄밀히 말하면 primitive type 역시 주소값 비교가 되는 것이다.  


equals가 어떻게 구현돼있는지 궁금해서 String class에서 오버라이딩한 equals를 찾아봤다. 
```
public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String aString = (String)anObject;
            if (!COMPACT_STRINGS || this.coder == aString.coder) {
                return StringLatin1.equals(value, aString.value);
            }
        }
        return false;
    }
```
StringLatin1.equals 메서드는 다음과 같다.
```
public static boolean equals(byte[] value, byte[] other) {
        if (value.length == other.length) {
            for (int i = 0; i < value.length; i++) {
                if (value[i] != other[i]) {
                    return false;
                }
            }
            return true;
        }
        return false;
    }
```
내부적으로 byte값으로 하나씩 비교하는 것 같다.

---
**hashcode**는 객체의 주소번지를 이용해서 해시값을 만들어 리턴한다.  
equals와 hashcode는 HashTable, HashMap, HashSet에서 키값이 중복되는 걸 방지하기 위해서 사용된다.  

 
HashTable에서는 hash값을 버킷에 저장하는데 **해시충돌**(hash값이 같은 경우) 일어나면 버킷에 해당 객체를 LinkedList형태로 추가한다.   

버킷에 있는 객체끼리 equals를 통해 비교한다. 만약 같다면 기존 객체를 덮어쓰고 없다면 객체를 LinkedList에 추가한다.  

블로그 마지막 내용중 이해가 안되는 내용이다. 나중에는 이해하겠지..?  

> 만약 equals()와 hashcode() 중 하나만 재정의 하면 어떻게 될까? 위 예에서도 봤듯이 hashcode()를 재정의 하지 않으면 같은 값 객체라도 해시값이 다를 수 있다.   
따라서 HashTable에서 해당 객체가 저장된 버킷을 찾을 수 없다.  
반대로 equals()를 재정의하지 않으면 hashcode()가 만든 해시값을 이용해 객체가 저장된 버킷을 찾을 수는 있지만 해당 객체가 자신과 같은 객체인지 값을 비교할 수 없기 때문에 null을 리턴하게 된다.   
따라서 역시 원하는 객체를 찾을 수 없다.  
이러한 이유로 객체의 정확한 동등 비교를 위해서는 (특히 Hash 관련 컬렉션 프레임워크를 사용할때!) Object의 equals() 메소드만 재정의하지 말고 
hashCode()메소드도 재정의해서 논리적 동등 객체일경우 동일한 해시코드가 리턴되도록 해야한다.




