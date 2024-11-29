
JPA는 자바와 DB를 쉽게 연결할수있도록 한다.
JPA는 엔티티라는것으로 DTO를 쉽게 받아서 레파지토리를 통해 DB에 저장하게 된다.
![[Pasted image 20241128233314.png]]
![[Pasted image 20241128233328.png]]


1. 클라이언트에서 받은 form데이터를 DTO를 만들어서 받고 컨트롤러에서 Article form이라는 DTO를 매개변수로 받기
2. DTO를 엔티티로 바꾸고 레포지토리로 DB에 서빙해야함


### DTO를 엔티티로 바꾸기
1. Article이라는 엔티티를 만들기  -> DTO랑 비슷하지만 DB에 저장할거라 조금 다름

![[Pasted image 20241129000155.png]]
뭐 생성자는 똑같은 어노테이션이 좀 다름 Column이라는 걸붙여주고 id라는것은
DB에서 고유값을 넣어야해서 사용함
2. DTO에 toEntity라는 메서드를 만들어야함 
![[Pasted image 20241129000404.png]]
이런식으로 public Article toEntity라는 메서드를 통해서 new Article(엔티티)를 만드는데 DTO의 변수들을 매개변수로 넣어서 위와같이 엔티티의 생성자를 채워서 DTO -> 엔티티로 변환시킴



### 레포지토리로 엔티티를 저장

![[Pasted image 20241129000545.png]]
여기서 보면 articleRepository라는 인터페이스를 만들어서 레포지토리의 기능을 상속받아 써야함

![[Pasted image 20241129000631.png]]
이렇게 Crud레포지토리를 상속받아서 처음에는 엔티티와 엔티티처음의 타입을 기입하면레포지토리가 완성됨 
결국 레포지토리의 .save라는 기능을 쓸수있음

현재까지 게시물 Create기능을 만들었고 H2 DB에 저장할수있음