
### HTML Tags

html태그를 semantic한 태그라고 표현을 한다.  
각 태그마다 의미가 있기 때문에 용도에 맞게 쓰라는 것이다.  
ul/li, img, p, div 태그 등이 자주 사용되며 굳이 모두 외울 필요가 없고 필요한 태그는 찾아서 사용하는 것이 좋다.  
구글링을 통해서 알아보는게 가장 효율적일듯하다. 
> html tags list 


### HTML Layout Tag

레이아웃 태그 
상단의 header, 네비게이션 영역의 nav, 본문의 section, 사이드영역의 aside, 하단의 footer  
header 같은 태그는 HTML5의 새로운 태그라서 PC웹페이지에서는 사용하지 않고 div에 클래스로 header를 주는 식으로 하고  
최신 브라우저를 갖고 잇는 모바일에서 레이아웃 태그를 많이 사용한다.(브라우저 호환성 이슈)

### HTML 구조설계

HTML을 개발할 때 큰 부분부터 영역을 나누고 각 영역 안의 구조를 잡는 방식으로 한다.  
CSS코드를 같이 구현하지 않고 HTML로 먼저 구조를 잡아나간다.  

### class와 id 속성

id는 고유한 속성으로 한 HTML문서에 하나만 사용 가능하다. (실제로 중복해서 써도 오류를 일으키지 않지만 규칙을 지켜야 한다.)  
고유한 값이므로 검색에 용이하다.  

class는 중복해서 사용이 가능하다.  
하나의 태그에 여러 개의 다른 class 이름을 공백을 기준으로 나열할 수가 있다.
여러 개의 class 스타일을 받을 수도 있고 하나의 class가 여러 개의 element 스타일을 지정할 수 있다.
