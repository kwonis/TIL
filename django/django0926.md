# Statice Files
정적파일 
서버 측에서 변경되지 않고 고정적으로 제공되는 파일

특정 위치에 있는 자원을 요청받아서 응답을 처리하고 제공하는 것

정적 파일을 제공하기 위한 경로가 있어야함.

경로 
1. 경로
2. 추가 경로

app폴더/static/
에 이미지 추가

DTL의 static tag 사용
built-in tag 가 아니기에 load tag.를 사용해 import후 사용

```python
{% load static %}

<img src="{% static "articles/sample-1.png" %}" alt="sample1">
```
부모에서 load static을 한다면 자식에서도 될까 ? 

STATIC_URL
settings.py 에서 설정 가능

ImageField()
객체가 저장되는 것이 아닌 이미지 파일의 경로가 저장됨.


settilng.py 에 MEDIA_ROOt, MEDIA_URL 설정

url.py 파일에 작성
```python
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('articles/', include('articles.urls')),
] + static(settings.MEDIA_URL,document_root =settings.MEDIA_ROOT)
```

$ pip install pillow
ImageField를 사용하기위 라이브러리 필요
```python
<form action="{% url "articles:create" %}" method="POST" enctype = 'multipart/form-data'>
```
input이 파일일 경우 enctype 설정이 필요하다.
view.py 에
request.FILES 추가 필요

  <img src="{{article.image.url}}" alt="img"> 사용 하여 렌더 가능