
Model -> 데이터 (DB나 변수) 이거를 씀으로써 템플릿화할수있었음
View  -> html이나 머스케치이런걸로 그냥 보일 화면 뿌리기
Controller -> 로직 model을 가져와서 view를 리턴해주는 역할


### controller로 이용한 templates반환

![[Pasted image 20241030005240.png]]

먼저 템플릿에 우리가 보여줄 화면을 만듬(안에 변수가 있어서 컨트롤러로 쏴줘야함) ->  컨트롤러(클래스파일로)를 하나만들어서 메서드를 하나만든다. 메서드는 @Controller라는 어노테이션을 붙여주고 안에 뷰템플릿을 model이라는 걸 통해 addAttribute를 가지고 변수를 변경해 그 뷰템플릿을 리턴해준다. 근데 getmapping을 통해서 url도 지정해줄수있다. 위에 그림과 같다.

결국 클라이언트는 localhost:8080/hi라는 주소로 접속하게 되면 저 컨트롤러가 메서드를 실행해서 model로 변수를 바꾼 greetings를 반환하게된다.



### 다시 정리 5강

hi라는 클라이언트가 요청이 오면 컨트롤러가 요청을 (getmapping)받는다. 
겟매핑으로 해당메서드가 실행되는데 보여줄페이지는 greetings고  사용할변수를 model로 등록하더라




