

데이터의 종류
	LLM 파인튜닝 데이터
1. 각 컴퓨터 부품의 공식홈페이지의 제품들의 설명 및 스펙
 +a
  - 코알파카사용시 기본적인 컴퓨터부품에 대한 설명등을 수집해야함

	  RAG데이터
1.  여러 견적사이트의 견적 데이터

최재우, 신동훈 -> LLM 파인튜닝 데이터 정제및 학습 진행중
	박준혁 -> RAG를 써서 상품 추천되게 하기

--------------
## RAG 1차 피드백
### 위 데이터 하나만 RAG적용시에 문제점 
현재는  가격 데이터 빼고 RAG를 사용해서 추출 해보았을때 코딩용 뭐 딥러닝용 이런것들을 곧 잘 찾지만
가격 데이터나 고성능이런 단어에 대한 식별이 부족함

### 위 RAG적용시 부족한점
단어에 대한 해석이 부족함 , 용도에 대한 해석은 어느정도 가능하다![[스크린샷 2024-04-25 17.34.10.png]]
- 이렇게 나온 이유는 가격이 낮지만 고사양 게임을 할수는 있는 견적을 추천을 해준것이다. 
- 그리고 가격으로 170만원대인 컴퓨터 견적을뽑아달라고 하면 가격인식을 못함
- 고성능에 대한 완벽한 숙지를 못함 (가격데이터로 판별할거임)

--------------
## RAG 2차 피드백
### 추가 가설 
1. 가격 데이터에 대한 정확한 카테고리가 필요, 가격으로 고성능 저성능을 판별할 생각 
2. 컴퓨터 용도에 대한 식별은 잘하지만 용도, 사용자들이 물어볼법한 질문을 뽑아서 그러한 카테고리를 추가하여 인식률을 더 높여야함
3. 실시간 가격을 보여주기 위한 부품에 대한 가격데이터(다나와)를 가져와 견적데이터랑 매칭하는 로직을 구현해야함 - 최근 1년에 대한 견적을 가져왔기에 가격 변동이 심할거라고 예상

### 보완점
- 견적가격매칭
- 현재 데이터에서 카테고리를 추가
- 추가한 카테고리에 대한 RAG 필터링기능을 사용한 1차적인 필터


--------------
## RAG 3차 피드백

1. 다나와 사이트에서 가격 데이터를 크롤링하여 각 견적에 대한 컴퓨터부품과 가격 데이터 매칭했다. 
- 문제점 : 가격 데이터 부족 - 모든부품의 가격이 있지않음(다나와는 수요량이 있어야만 가격 데이터를 줄수있음) , 컴퓨터 부품이름에 대한 매칭이기에 똑같지않다면 매칭대상에서 제외됨(그래서 있던 데이터도 매칭을 안해줄때도 있음)
- 해결방법 : 




--------------
## 4차 피드백
### 주제에 대한 셀프디스 - 캡스톤 발표때 질문에 대한 응답과 프로젝트의 구체화를 위함
1. 다나와라는 사이트는 추천 견적들과 컴퓨터부품이 있는데 뭐하러 이거를 쓰냐?
 - 다나와는 견적에 대한 자세한 설명이 있지않음. 또한 우리 프로젝트는 여러 견적사이트에서 데이터를 가져와서 주관적인 전문가 견적 데이터를 LLM파인튜닝을 통한 보다 부품의 스펙과 설명을 통한 수치화된 데이터를 가지고 해당 견적에 대한 객관적인 설명을 붙여줌.  ( 실시간 견적 상담 )
 2. LLM파인튜닝과 RAG를 적용해서 나아진점이 있나 
 - 이거를 시각적으로 기록해놔야함 (근거가 없으면 사실 RAG하나만 적용했을때랑 딱히 바뀐점이 없다고 판단할수도있음)
 3. 프로젝트 동기가 그래서 뭐냐 그냥 평소에 컴퓨터견적짜기가 어려웠냐 (이유작성해보기)
 - 평소에 소프트웨어학과라고 친구들이 자기 컴퓨터 견적을 짜달라는 이야기를 많이 들었다.
 - 그래서 부품같은 이런 부분에 대해 잘몰랐던 내가 짜주기에는 되게 어려웠다.
 - 그래서 컴퓨터부품에 대해 공부하고 어렵게 견적을 짜서 줬던 경험이 있다. 
 - 사실 이러한 하드웨어 대해 딥하게 알기에는 평소에 하드웨어에 관심이 있지않은이상 
 - 혼자서 컴퓨터견적을 짜기에는 무리가 있다. 그래서 다들 다나와나 컴퓨터 판매 사이트에서 가격대와 용도에 맞춰서 그대로 사게 된다.
 - 이러한 판매하는 견적들 같은경우 문제점은자세한 견적에 대한 설명과 비교와 실시간 Q&A가 쉽지않다는걸 발견하였다. ** (이거 다나와나 여러사이트에서 문제점을 찾아야함)
 - 근데 합리적인 소비자들은 뭐가 더 좋은지 같은 가격대라도 자기 상황에 맞는 더 좋은 컴퓨터를 원하게 된다.
 - 만약 그래픽을 많이 쓰는 견적에는 cpu보다 그래픽에 대한 투자가 더 있어야하는 경우이기 때문이다.
 - 그래서 견적데이터를 가져와 LLM파인튜닝을 하여 더 객관적이고 구체적인 분석을 하여 챗봇을 대답을 하기 원했다.
4. 3.5를 썼는데 나은점이 있냐
- 전에 대답과 현재 대답을 비교해서 성능을 확인해야함 (그냥 대답말고 어떤 성능적으로 대답을 더 잘할수있게 되었는지)
5. 성능 지표와 평가방법: 이 시스템의 성능을 어떻게 평가했나요? 어떤 지표를 사용했으며, 왜 이러한 지표가 중요한가요? 또한, 테스트 세트의 구성은 어떻게 되나요?
위에 디스에 대한 주제 보완할 점
- 견적 데이터에 대한 수치를 보여줘서 보다 설명을 직관적이게 보여줘야함
- 주관적인 견적데이터를 객관적으로 판단할수있다는 지표가 있어야함
그냥 보완점
- 가격에 대한 데이터를 인식을 못할경우 gtx 3060뭐시기뭐시기 써있으면 인식을 못하니까 
그냥 3060이라는 대표적단어를 가져와서 3060그래픽카드의 평균값을 넣어야될것같다.
왜 이렇게 했냐하면 표준편차를 따졌을때 그렇게 많은 영향을 안줄것같다. 완벽하게 할수없기에 차선책을 실행함

해야할거
챗봇이 어떻게 말했으면 좋겠냐는거를 생각해보자
지표로 분석하는거를 구상, 주관적->객관적으로 판단하도록 프롬프트 작성 , 사용자의 질문리스트를 생각을 해서 카테고리를 분류하기 , 가격매칭보완하기 , 출력이 더 길고 자세하게 나오도록 코드 수정

파인튜닝관련해서 지원금 후불제로 바뀐거 담당선생님한테 문의 다시 해보기

--------------

4월 28일 
RAG 가격 데이터 매칭하는거 한번 1시간정도 해보기
안되면 샘플데이터 작업후 RAG로직을 짜서 실행해보기
추천뿐만아니라 그에 대한 설명을 덧붙여야함 


----------------
4월 29일
### 한것
1. 가격 매칭 데이터 완성을 해서 견적에 대한 실시간 가격을 가져올수있다.
2. 총가격을 갱신을 할수있다.

###  마저 해야하는것
1. 카테고리 : 사용용도 , 성능 , 얼마대~얼마대?



------------------------

5월 6일
현재 견적데이터가 완벽하게 있지만 그걸 사용해서 RAG에 적용을 못하고 있다. 
먼저 의문점은
meta_data에 왜이렇게 많은 데이터들이 있는가?
또한 filter라는 곳에 값이 넣어지게 되면 아예 작동을 안한다는것이다.
작동보다 출력을 안하게 됨


그래서 생각했을때 강의 고급기법을 참고해서 다른 방식으로 접근하는게 좋을것같다.

기본적인 RAG 시스템에서 + RAG 고급기법을 활용해서 좋은 답변을 내도록
현재는 CSV나 JSON둘중에 어떤 파일로 할지도 고민이다.


그래서 고급 RAG기법을 정리해서 어떻게 적용할지 생각을 해볼것이다.

## 고급 RAG 기법

리트리버에 관한 여러가지의 기법을 통해 다음과 같은 내용들을 해결하기

1. 대충 질문해도 좋은 답변을 원할때
2. 앞뒤 문맥 잘 담아야 할때 (청크를 담을때 짤린 청크를 저장할때 틀린 답변을 줄때가 없음)
3. 시멘틱 검색 말고 쿼리가 필요함 - 시멘틱 검색이란 우리문서와 사용자질문을 가지고 유사도검사를 통해 문서와 질문을 LLM에  참고 문서로 넘겨주는 과정임 (단점: 사용자질문을 조금 다르게 했을때 유사한 청크가 달라질수있다는 수있다 (일관성이 떨어짐)) , 쿼리 - 명확하게 어떤 정보들을 기준으로 필터링을 해야되고 그정보들만 뽑아내야하는 경우에는 시멘틱검색이 아니라 sql과 파이썬으로 짤라내는 과정이 필요하다
4. 최신자료만 참고했으면 좋을때

대충 질문해도 충분히 좋은 답변을 원한다면 Multi_query
문맥잘담기 - Parent-Document
쿼리 - Self_Querying
최신 - Time-wig

## Multi_query
사용자의 질문을 유사 질문으로 재생성하게 된다.
추상적인 질문을 했을때 좋은 답변을 내야되기에 이걸쓴다.

재생성질문을 멀티쿼리리트리버가 직접만들어내버림 
질문을 다각도로 해석가능

## 실습

https://colab.research.google.com/drive/1PALBOJ-vXgKe3LOIbKoqeD8kuZYx_Lnr#scrollTo=vL-HP-9L8OIq

selft_query

메타데이터 기반으로 먼저 질문을 주면 메타데이터 기반으로 쿼리로 가져옴![[스크린샷 2024-05-06 23.47.22.png]]

Document에 page_content랑 metadata를 넣어서 
page_contnet는 LLM이 참고할 내용들
meta_data는 쿼리로 확인할 데이터들
![[스크린샷 2024-05-06 23.49.36.png]]
그 메타데이터 카테고리에 대한 설명?

밑에 리트리버로 만약 8.5인 영화 데이터 이야기해라 그러면 
Document에서 필터링해서 하나 던져줌
![[스크린샷 2024-05-06 23.51.29.png]]



-----------------
5월12일

메타데이터 기반으로 selfquery리트리버가 걸러지는 거에 대해 성공을 했지만 아직 가격데이터만 가능하다.



근데 단점이라고 하면 만약 카테고리에 없고 인식이 안되는데 필터에 들어갔다고 할시에 걸러지지않는다.
문자열을 보고도 가능한지 테스트후 

설명할떄 
각 게임이나 프로그램 , 벤치마크에서 성능에 대한 지표로 보고 카테고리를 재가공

사실 챗지피티
json데이터를 간추려서 인풋 (카테고리 한 2개)
그래서 사용용도, 가능한게임, 성능 3개을 카테고리에 추가한후에  그다음에 부품도 나눠서 간단하게 걸러지는지에 대한 self쿼리리트리버 
150만원짜리 롤,배그돌아가고 취미삼아 영상편집을 할수있으며 가성비제품인 gtx3060이 들어간 컴퓨터 견적추천해줘
이런느낌을 걸릴수있으면 성공이다.
만약 이상한 아이작 게임이런거 들어가있는데 우리데이터에 없으면 rag에서 오류가 발생
-> 그거는 그냥 챗지피티가 다시 재질문하게 만약 아이작이면 그비슷한 사양의 게임을 질문에 넣고 아이작을 배제해서 다시 rag프로세스 넣음

설명할때 
그 아이작에 대한 비슷한 게임을 판별하기위한 데이터셋을 만들어둠 
아이작의 게임의 적정사양이나 최고사양을 가져와서 데이터셋과 비교해서 질문을 재정비했다하면됨




이제시나리오
1. 첫질문 (견적에 대한 질문을 하게 됨)
- rag -> 견적추출 -> 파인튜닝된 LLM이 견적에 대한 분석 -> 견적내용과 분석내용을 주게됨
2. 두번째 질문 (새로운견적받기 , 견적에 대해 이어물어보기)
- 새로운 견적받기 : (세션초기화가 필요)
-1. 질문을 같은 질문인데 다른 견적을 원하는 경우 -> 더 자세히 말하라고 명시하게 하던가 ,우리가 더 자세히 나올정도의 질문을 재정비해야함
-2. 다른질문일시에 RAG 다시 들어가서 LLM으로 출력하면됨
- 이어말하기 (세션유지가 필요): 이미 프롬프트에 견적내용이 올라간 LLM이 다시 답하면됨 
-여기서는 현재 견적의 cpu의 벤치마크점수는? 현재 cpu를 지정한이유가 뭐야? 장점이뭐야?



RAG에서 해야될거 
1. 견적을 보고 컴퓨터 부품 나누기  o 
2. 테스트 데이터셋을 만들어 긴문자열 롤배그가되는 컴퓨터입니다. 이런식으로 카테고리안에 있을경우 어떻게 self리트리버의 오류 체크 심지어 롤 , 배그 이것도 안걸러지나? 이것도 테스트해야함
3. 만약 성공시에 json카테고리를 몇개 선정해 해석한후 카테고리 3개만 추가
4. 그리고 RAG완성시키기




-------------------
5/14 화

문제점과 해결해야되는점


문제점 
LLM 
- 이전 질문에 대한 저장한 데이터에 대한 프롬프트 할루시네이션 
- 전체 견적에 대한 프롬프트의 길이문제로 할루시네이션
RAG 
- 벡터스토어 S3저장문제  - 해결
- 필터생성할때 부품에 대한 인식문제 (해결방법: 모든 부품에 대해 ex넣고 다른 부품이 들어오면 오류처리, 이오류처리를 어떻게 할것인가) 심각
- 또한 30만원짜리 고성능 (이거는 심각)

부품리스트에 없으면 어떻게 처리할지 생각 cpu gpu만



--------
RAG다양성있는 프롬프트로 인식 더 잘되게 하기
질문이 들어오고 나서 바로 넣지말고 정제해서 넣는 방법으로 RAG해결해야함
그러면 완벽한