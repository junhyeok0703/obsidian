
만들어 놓은 코드를 재사용하고 싶다.
어떻게 구조화해야지만 사람들이 가져가서 쓸때 얼마나 잘 쓸수있을지
그런것들이 객체라고 함

![[Pasted image 20240629233557.png]]
수강신청을 만들떄 어떻게 만들까? 2가지방법
2번째 방법이 객체지향
![[Pasted image 20240629233700.png]]


### 클래스와 인스턴스
설계도 - 클래스(붕어빵틀) 
실제 구현체 - 인스턴스(붕어빵) - 객체라고도 함

### objects in python

축구 선수 정보를 class로 구현하기

class 선언 (함수선언이랑 비슷) , object는 pyton3에서 자동상속 
![[Pasted image 20240630160149.png]]
여기서 특이한점 변수나 함수명을 지을때 띄어쓸때 \_를 추가했는데
class명은 위처럼 카멜case로 하게된다.

클래스안에 있는것들은 속성 , 행동을 크게 나눌수있는데 
init을 통해 여러가지 속성정보를 적게 된다.
self.으로 그 객체의 초기정보를 선언할수있다.
![[Pasted image 20240630160444.png]]
위 코드는 한 class(객체)를 선언한것이다. 
흡사 named tuple이랑 비슷하다
#### 여기서 \_\_는 뭘까?
여기서 언더바 두개를 쓴 init경우는 특수한 예약함수나 변수 그리고 함수명변경(맨글링)으로 사용한다.  **중요**
예) \_\_main\_\_ , \_\_add\_\_ ,\_\_str\_\_

str이라 함수는 프린트문을 쓰게 되면 return 값을 프린터 해준다.
![[Pasted image 20240630161013.png]]



### 클래스선언
자그럼 찬찬히 class를 생성하는 것부터 보자
![[Pasted image 20240630161748.png]]
클래스를 선언한뒤에 init을 통해서 클래스안에 초기화함수를 만들수있다.
똑같은 클래스를 써서 다른 객체를 만들수있다.
틀만 같고 서로 다른 객체가 생성이 된다.

### \_\_str\_\_ 이 뭘까?
![[Pasted image 20240630162130.png]]
저 함수에 self를 매개변수로 주고 문장을 return 해주게 되면 
print함수로 찍었을때 저게 찍힌다.
별다른 함수호출을 하지않아도 print를 하게 되면 함수호출이 되는것이다.
만약 str함수를 쓰지않았을때는 그냥 메모리주소만 나오게 된다.

### \_\_add\_\_는 뭘까?
말그대로 더해준다.
![[Pasted image 20240630162420.png]]
이런식으로 서로 다른 객체를 더해주면 name을 더 해주게 된다!

https://corikachu.github.io/articles/python/python-magic-method
이러한 아티클(매직메서드)을 정리한것이다.


### 클래스안에 메서드 구현하기
메서드(액션)추가는 기존 함수와 같으나 self를 추가해야만 class함수로 인정된다!!

![[Pasted image 20240630163003.png]]

### objects(instance) 사용하기
object 이름 선언과 함께 초기값 입력하기
![[Pasted image 20240630163041.png]]
![[Pasted image 20240630163055.png]]


### self가 뭐냐
생성된 인스턴스자신을 이야기한다.
위에 코드를 보게 되면 jinhyun이라는 객체(인스턴스)가 생성되었을때
클래스밖에서는 jinhyun.change_back_number(1)이렇게 접근하지만
클래스코드안에서는 self가 곧 jinhyun이라는 뜻이다. 
![[Pasted image 20240630163401.png]]
여기서 보면 self를 넣어줘서 자기자신의 back_number를 넣어줄수있었다. 



### OOP 예시

구현 가능한 OOP 만들기 - 노트북

![[Pasted image 20240630163648.png]]

```
class Note(object):
    def __init__(self,content=None):
        self.content=content
    def write_content(self,content):
        self.content = content
    def remove_all(self):
        self.content=""
    def __add__(self,other):
        return self.content + other.content
    def __str__(self):
        return self.content
        
class NoteBook(object):
    def __init__(self,title):
        self.title = title
        self.page_number = 1
        self.notes = {}

    def add_note(self,note,page=0):
        if self.page_number< 300:
            if page == 0:
                self.notes[self.page_number] = note
                self.page_number +=1
            else:
                self.notes = {page:note}
                self.page_number +=1
        else:
            print("page가 모두 채워짐")
            
    def remove_note(self,page_number):
        if page_number in self.notes.keys():
            return self.notes.pop(page_number)
        else:
            print("해당페이지 존재 X")
    
    def get_number_of_pages(self):
        return len(self.notes.kets())    
```
### OOP characteristices

객체지향언어의 특징 - 실제 세상을 모델링

상속 , 다형성 , 


### 상속
부모클래스로부터 속성과 메서드를 물려받은 자식 클래스를 생성하는것

![[Pasted image 20240630170043.png]]![[Pasted image 20240630170048.png]]

korean에 person을 상속받았음
korean에 아무것도 없지만 person에있는 속성과 메서드를 사용할수있음
