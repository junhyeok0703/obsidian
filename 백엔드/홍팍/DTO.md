## 역할
- 뷰에서 DTO로 받아서 컨트롤러에 넘김
- 뷰에서 DTO로 데이터 받기 그다음에 DTO로 이제 DB에 넘겨주는거임

## 순서
1. form데이터에서 input박스에 name설정해서 어떤변수이름으로 보낼지
![[Pasted image 20241128232502.png]]
먼저 action으로 컨트롤러한테 post로 던질거야 
DTO에겐 ![[Pasted image 20241128232534.png]] 이런 title이라는 이름으로
2. DTO라는 폴더하나만들기
3. ArticleForm.java파일 하나만들기
->form에서 받을 변수명써주기
![[Pasted image 20241128232558.png]]
construtor?로 만들면됨 
toString으로 콘솔찍어볼수있음
DTO는 form 데이터가 어떤 형식으로 받을건지 또 변수공간이라서 받아서 
컨트롤러는 찍어보면됨

컨트롤러
![[Pasted image 20241128232711.png]]
여기서는 getmapping부분에는 from화면 띄워주는역할
postmapping은 저 주소로 보낼거야! 아까 action부분임 
ArticleForm form은 아까전에 만들었던 DTO에 뭐가 들었는지 확인할수있음


결론 DTO는 변수와 같이 클라이언트가 보낸 데이터를 저장함 
DTO는 컨트롤러에서 꺼내서볼수있음
컨트롤러는 DTO라는 변수를 DB에게 전해줄때 어떻게 넣을지 결정함