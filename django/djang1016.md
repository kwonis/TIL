# REST API

API 두 소프트웨어가 서로 통신할 수 있게 하는 메커니즘

WEB API
웹 서버 또는 웹 브로우저를 위한 API
OPEN API를 활용하는 추세

REST API란
설계 방법론  규칙이 아니다.

RESTful API
자원을 정의 하고 자원에 대한 주소를 지정하는 전반적인 방법을 서술

### 자원을 정의하고 주소를 지정하는 방법
1. 자원의 식별
  - URI
2. 자원의 행위
   - HTTP Methods
3. 자원의 표현
   - JSON 데이터

#### Domain Name
요청 중인 웹서버를 나타냄
어떤 웹 서버가 요구되는 지를 가리키며 직접 ip 주소를 사용하는 것도 가능하지만 외우기 어렵기에 도메이 주소 사용

#### Path
- 웹 서버의 리소스 경로
- 초기에는 물립적 위치를 나타냈지만 오늘날은 추상화된 형태의 구조

#### Parameters
- 웹 서버에 제공하는 추가적인 데이터
- & 기호로 구분되는 key-value쌍 목록
- 서버는 리소스를 응답하기 전에 이러한 파라미터를 사용하여 추가 작업을 수행할 수 있음

#### Anchor
- 일종의 북마크를 나타내며 브라우저에 해당 지점에 있는 콘텐츠를 포시
- '#' 이후 부분은 서버에 전송되지 않음


 ## Methods
1. GET
   - 데이터 검색 R
2. POST
  - 상태를 변경 C
3. PUT
  - 수정 U
4. DELETE
  - 삭제 D

## Serialization
직렬화

구조나 객체 상태를 나중에 재구성할 수 있는 포맷으로 변환하는 과정

ModelSerializer
Django 모델과 연결된 Serializer 클래스

```python
# serializers.py 
from rest_framework import serializers
from .models import Article

class ArticleLisstSerializer(serializers.ModelSerializer):
  class Meta:
    model =Article
    fields = '__all__'
```

## GET

```python
# serializers.py 
from rest_framework import serializers
from .models import Article

class ArticleLisstSerializer(serializers.ModelSerializer):
  class Meta:
    model =Article
    fields = ('id','title','content',)
# views.py
from rest_framework.response import Response
from rest_framwork.decorators import api_view
from .models import Article
from .serializers import ArticleLisstSerializer


@api_view(['GET'])
def article_list(request):
    articles = Article.objects.all()
    serializer =ArticleLisstSerializer(articles,many = True)
    return Response(serializer.data)

def article_detail(request, article_pk):
    pass

```

many 옵션
- Serialize 대상이 QuerySet인 경우

data 속성
- Serialized data 객체에서 실제 데이터를 추출

