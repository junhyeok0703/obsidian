기본 rag 기능 - 방대한 문서를 가지고 검색증강생성을 통해 사용자질문을 시멘틱서치를 하여 문서에서 원하는 문서를 가지고 올수있도록 해줌


셀프쿼리리트리버
기존 리트리버에서 메타데이터로 근거로 필터를 넣을수있음
필터를 통한 1차적인 문서를 필터하고 필터로 줄은 문서안에서 시멘틱서치를 통해 원하는 문서를 보다 더 정확한 문서를 가져올수있음 

기존 셀프쿼리리트리버 예시
![[스크린샷 2024-05-22 14.25.50.png]]

![[스크린샷 2024-05-22 14.26.01.png]]

![[스크린샷 2024-05-22 14.26.14.png]]

1. 기존rag에 넣을 데이터document타입에서 메타데이터를 활용 -  카테고리에 대한 메타데이터를 뽑아 기존데이터 가공 - 벡터 디비저장
2. metadata의 info를 입력하여 알게 한다. (name, description,type)형식이야함
3. 벡터디비와 문서의 내용설명 , 메타데이터의 설명, llm을 통해 리트리버를 생성한다.

기존 셀프쿼리리트리버에서 chain을 사용해서 다양한 라이브러리 커스텀을 활용해서 셀프쿼리리트리버 강화 - 보통은 셀프쿼리만 씀 

1. 메타데이터의 설명중 유니크한 값들에 대한 명시를 하여 필터의 퀄리티를 높일수있었음 
2. 중요한 부분 chain

```
from langchain.chains.query_constructor.base import ( #커스텀 쿼리 프롬프트 작성하기위해 기존

get_query_constructor_prompt,

load_query_constructor_runnable,

)
```

```
doc_contents = "견적에 대한 자세한 설명"

prompt = get_query_constructor_prompt(doc_contents, attribute_info)

print(prompt.format(query="{query}"))
```
3.









## 우리의 RAG 로직
랭체인라이브러리설치 -> 랭체인 loader를 이용하여 json파일읽기 ->
유니코드데이터에서 분석을 위해 한글인코딩처리 -> 파이썬 딕셔리너파일을  df으로 변환 -> 숫자데이터를 문자열로 되있어서 숫자int타입으로 컨버터, 벤치마크순위도 컨버터 -> 필요없는 카테고리 버리기 -> attributeinfo를 추출하기위한 df.head를 뽑아서 카테고리에 대해 분석하여 설명을 붙이기 (name,description,type순으로)-> attributeinfo추가 -> 그러한 데이터 유니크한값은 attributeinfo에 명시하면 더 정확하게 알려줄수있음 ->  chain을 생성해서 커스텀 쿠리 프롬프트를 생성할수있음 -> attribute_info와 스키마를 설정하여 get_query_constructor_prompt로 프롬프트 작성 -> load_query_constructor_runnable이걸로 만든 프롬프트와 LLM을 설정하면 필터생성해줌 -> ![[스크린샷 2024-05-25 15.15.48.png]]
이러한 query의 오류와 filter의 오류를 잡기 위한 더 명시적으로 프롬프트에 추가하여 ![[스크린샷 2024-05-25 15.16.53.png]]
이런식으로 대표적인 명시를 통해 필터의 유효성을 올리게 됨 -> 다시 load_query_constructor_runnable을 이용하여 ex(저러한 예시)까지 추가하여 체인생성 -> invoke를 통한 필터테스트![[스크린샷 2024-05-25 15.18.41.png]]-> 필터의 정확도 상승 및 기존 가격에 대한 명시가 없어 170만원이하면 50만원도 보여주는 오류?가 떠서 리미트를 잡아 2,30만원에 대한 리미트를 설정하였기 때문에 저런 필터가 만들어짐 ->  허깅페이스를 통한 gpu 임베딩모델설정 -> 현재 data_df에 있던 것을 document타입으로 설정하여 랭체인 인식이 되게끔 바꾸게 됨 ->docs에는 document타입으로 변환된 견적데이터와 임베딩모델을 설정해서 chroma라이브러리를 이용하여 벡터디비를 임베딩하여 벡터디비만들게됨 -> selfqueryretriever랭체인 라이브러리를 가져와 , 커스텀쿼리(체인)와 벡터디비,k값설정하여 리트리버설정 -> 리트리버를 통해 견적추천받기 






