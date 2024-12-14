우리가 서버를 실행하고 나서 urls.py에서 urlpatterns에 url을 추가해서 반환되는 파일을 써줘야지 그 url로 들어갔을때 파일을 쏴줄수있다. (url과 보낼 파일 설정해주는것이다.)


```python
urlpatterns = [
	path('admin/',admin.site.urls),
	path('food')
]
```