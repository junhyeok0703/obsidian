웹소켓을 연결할 예정이다.
1. pub/sub을 검색하고
2. Front로 설정하고 나머지는 똑같이 한다음 배포한다.
3. 배포완료시 pub/sub리소스 -> 설정 -> 키 -> 클라이언트 엑세스 URL로 테스트를 진행할수있다.
4. 허브와 그룹으로 보내기가 있는데 채팅방 웹소켓 채널이라고 생각하면 된다. 웹소켓에 메세지를 보낼때 특정 허브의 특정 그룹으로 보내기 하면되는데 채팅방이라고 생각하면 된다. 웹소켓의 특정그룹이나 모든그룹등의 엑세스 허용범위를 설정할수있다. 특정한 그룹에만 참가를 할수있도록하거나 아니면 특정한 그룹에만 보낼수있게 되게 된다.
5. 테스트는 개요로 가서 빠른 시작이 있다.
6. 설정을 허브는 test_hub이고 권한부분에 Group 1의 참가와 탈퇴 허용하기
7. ![[Pasted image 20250130223801.png]]
8. 이런식으로 웹소켓 url를 붙여주고 연결하면 client websocket opened라고 써져있다. 
9. Group1만 참가 탈퇴만 되고 메세지 보내는건 안된다.
10. 메세지 권한을 주면 ![[Pasted image 20250130224015.png]]
11. 위처럼 메세지 보내는것까지 되는것이다. 수신도 되는지 확인하려면 사이트를 하나 더 뛰어서 확인해야한다.
12. 이제 사용자id까지 주고 모든 허용으로 하나 url파서 하게 되면 서로 통신이 되는걸 확인할수있다.
13. 프론트와 웹소켓을 붙여보자

```javascirpt
const WEB_SOCKET_URL = 'wss://parkgptlecturepubsub.webpubsub.azure.com/client/hubs/test_hub?access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJ3c3M6Ly9wYXJrZ3B0bGVjdHVyZXB1YnN1Yi53ZWJwdWJzdWIuYXp1cmUuY29tL2NsaWVudC9odWJzL3Rlc3RfaHViIiwiaWF0IjoxNzM4MjQ0NjY4LCJleHAiOjE3MzgyNDgyNjgsInJvbGUiOlsid2VicHVic3ViLnNlbmRUb0dyb3VwIiwid2VicHVic3ViLmpvaW5MZWF2ZUdyb3VwIl0sInN1YiI6Imd1ZXN0In0.Bxq9d2R5z1uieybI9LGEeAfg0lc7QReIFnhrg5bpk74'

const pubsubClient = new WebSocket(WEB_SOCKET_URL,'json.webpubsub.azure.v1')

pubsubClient.onopen = function(event){

console.log('연결성공')

}

pubsubClient.onmessage = function(event){

  

}

```
이런식으로 원래는 토큰을 API에서 발행해서 줘야하지만 지금은 연결을 해보는것이기때문에 모든 권한을 허용한 url을 가져와서 위처럼 설정하여 연결을 성공하였다.

웹소켓에 연결을 한다음에 그룹으로 조인을 하도록 해야한다.
특정한 그룹이랑 Join을 해야한다.

그다음에 onopen함수에 group을 조인하는 코드를 작성해주고

그다음은 onmessage함수는 메세지를 받았을때 event에 data의 data에 우리가 받은 메세지를 jquery로 뿌리기만 하면 된다.