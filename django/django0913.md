Web Framework
웹 서비스를 빠르게 개발할 수 있도록 도와주는 도구

# Django
- 다양성
- 확장성
- 보안
- 커뮤니티 지원

대규모 트래픽 서비에서 안정적인 서비스 제공

# 가상환경
격리하여 관리할 수 있는 독립적인 실행 환경

하나의 컴퓨터에서 각 다른 버전을 사용해야 할때

생성
$ python -m venv ///venv(폴더이름)
가상 환경 활성화
$ source venv/Scripts/activate
목록 확인
$ pip list
패키지 목록 생성
$ pip freeze > requirements.txt
패키지 목록 기반 설치
$ pip install -r requirements.txt

주의사항 및 권장 사항

on/off 이기에 새로운 터미널에서는 다시 활성화 필요
venv 이름으로 고정

Django 프로젝트 생성
$ django-admin startproject firstpjt .
서버실행
python manage.py runserver

# 디자인 패턴
소프트웨어 설계에서 발생하는 문제를 해결하기 위한 일반적인 해결책 (공통적인 문제를 해결하는 데 쓰이는 형식화 된 관행)

### MVC 디자인 패턴
(Model,View,Controller)

애플리케이션을 구조화하는 대표적인 패턴
데이터 / 사용자 인터페이스 / 비즈니스로직으로 분리

MTV 디자인패턴
Django 에서 사용
MVC 패턴과 동일하나 단순히 명칭을 다르게 정의

기능단위로 나누어지는 앱

앱생성
(이름은 복수형으로 지정을 권장)
python manage.py startapp articles,

- settings.py
  - 프로젝트의 모든 설정을 관리
- urls.py
  - 요청 들어오는 URL에 따라 이에 해당하는 적절한 views를 연결
  
### 앱 구조
-admin.py
  관리자용
- models.py
  - DB와 관련된 Modle을 정의
- views.py
  - 요청을 처리하고 해당요청에 대한 응답을 반환
  
  URl.s 파일에

  import 와 path  작성

```python
from articles import views

urlpatterns =[
  path('index/', views.index),
]
```

```python
from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request,'articles/index.html')
```
프로젝트 폴더안에 templates 폴더생성

가상환경 종료 명령어 
$ deactivate