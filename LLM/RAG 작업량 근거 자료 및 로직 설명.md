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