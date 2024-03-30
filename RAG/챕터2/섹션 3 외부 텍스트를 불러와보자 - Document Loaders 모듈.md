
2단계 진행중 (파일로부터 텍스트 읽어오기)
### WebBaseLoader - url로부터 HTML 텍스트를 읽어오기

**Document Loaders**의 종류를 크게 분류하면 다음과 같습니다.
1. WebBaseLoader
2. CSV
3. File Directory
4. HTML
5. JSON
6. Markdown
7. PDF

실습 순서
1.  랭체인 라이브러리 설치
```bash 
pip install langchain
```

1-1.  webBaseLoader

    웹사이트를 HTML파일로 가져와 데이터셋으로 쓸수있음.
    
```bash
form langchain.document_loaders import WebBaseLoader
loader = webBaseLoader("http://www.espn.com/")
data = loader.load()
data
```
    
    여러 웹사이트도 로더로 손쉽게 HTML파일을 긁어올수있다.
 ---------------------------------------------------------------------------------
1-2. CSVLoader

    csv파일을 그냥 다운후 넣어서 데이터셋으로 가져올수있음
    
```bash
from langchain.document_loaders.csv_loader import CSVLoader

loader = CSVLoader(file_path='./mlb_teams_2012.csv')

data = loader.load()

data
```
	
	추가적인 parsing을 하고싶을때 
	
```bash
loader = CSVLoader(file_path='./mlb_teams_2012.csv', csv_args={

'delimiter': ',',

'quotechar': '"',

'fieldnames': ['MLB Team', 'Payroll in millions', 'Wins']

})

data = loader.load()

data
```

-------------------------------------------------------------
1-3. DirectoryLoader

    DirectoryLoader는 폴더 안에 존재하는 파일들을 필터링해서 읽어옵니다.

```bash
pip install unstructured
```

```bash
from langchain.document_loaders import DirectoryLoader

loader = DirectoryLoader('./sample_data', glob="**/*.md")

docs = loader.load()
```

	이와 같이 폴더를 설정해주고 어떤 파일만 읽어 올것인지 설정할수있다.


이와 같이 여러가지 JSON , HTML, MarkdownLoader로 텍스트 읽어올수있음
PDF파일 또 한 가져오기 가능하다.
