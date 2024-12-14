우리가 서버를 실행하고 나서 urls.py에서 urlpatterns에 url을 추가해서 반환되는 파일을 써줘야지 그 url로 들어갔을때 파일을 쏴줄수있다. (url과 보낼 파일 설정해주는것이다.)


### 1. constaurant에 urlpatterns바꿔주기
```python

from django.urls import path,include

urlpatterns = [
	path('admin/',admin.site.urls),
	path('foods/',include('foods.urls')
]
```
여기서 include로 admin쪽의 urls.py에 추가해준다. path를 그러면 foods파일에 있는걸 리턴할수있게 도와주는듯?
**도메인 옆에 foods를 입력하면 foods.urls파일을 봐라**
### 2. foods 앱에 urls.py를 만들어서 
```python

from django.urls import path
from . import views # .현재폴더안에 views를 가져와라

urlpatterns = [

path('index/',views.index) #foods/views.py를 봐라

]
```
위에서 저 admin에 urls에서 저렇게 foods폴더를 접근할수있다.
이처럼 urls.py에 하게되면 views파일에 있는 index를 리턴할수있다.
**foods/index/를 입력하면 views안에 있는 index함수를 실행해라**
```python
from django.shortcuts import render
from django.http import HttpResponse

# Create your views here.

def index(request):

	return HttpResponse('<h2>hello, django</h2>') #html태그를 사용할 수 있다.

```
views.py에 위처럼 해주면 HttpsResponse를 사용하게 되면 저 html태크를 페이지에 리턴해줄수있다.
**index라는 함수는 HttpResonse그니까 이걸 줄거야**