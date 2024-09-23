# ORM
object-relational-mapping
객체 지향 프로그래밍 언어를 사용하여 호환되지 않는 유형의 시스템 간에 데이터 변환 기술

Django 와 db 언어가 다르기에 사용

API를 사용하여 sql이 아닌 python 코드로 데이터를 처리

## QuerySet API 구문
Article.objects.all()
model class/Manager/Queryset API


Query 데이터베이스에서 특정한 데이터를 보여 달라는 요청
QuerySet 데이터베이스에게서 전달 받은 객체 목록 (순회가 가능한 데이터 반복문으로 사용 가능)
단일 객체는 모델(Class)의 인스턴스로 반환.

$ pip install ipython

$ pip install django-extensions

'django_extensions', app 추가를 해야 사용가능하다.

migrations는 공유가 되지만 db는 공유되지 않는다.

shell 실행
$ python manage.py shell_plus

한줄씩 실행하는것을 한번에 볼수 있게

인스턴스를 우선적으로 생성


첫번째 방법
```python
article = Article()
article.title ='첫글입니다.'
article.content ='안녕하세요.'
# 저장을 하지 않으면 아무일도 일어나지 않는다.
Article.objects.all()  => []
article.save() # 세이브
```

두번째 방법
```python
article =Article(title='second',content='djang')
article.save() # 세이브
```
세번째 방법
```python 
Article.objects.create(title='third',content='django')
#세이브가 필요없다.
```

$ all()
전체 데이터 조회

$ filter()
주어진 매개변수와 일치하는 객체를 포함하는 QuerySet반환
있든 단일이든 QuerySet으로 리턴

$ get()
매개변수에 일치하는 객체를 반환
없으면 예외 발생 / 여러개여도 예외 발생
그렇기에 고유성을 보장하는 id 와같은것으로 조회해야한다.(pk)

수정을 위한 순서

1. 조회
<!-- $ article = Article.objects.get(pk=2) -->
2. 수정
3. 저장

삭제
```
article.delete()

삭제 객체 반환
```
django 는 삭제 된 pk 는 다시 사용하지 않는다.


# view 함수에서의 전체 게시글 조회

```python
from django.shortcuts import render
from .models import Article
# Create your views here.

def index(request):
    #게시글 전체 조회 요청
    articles = Article.objects.all()
    context={
        'articles' : articles,
    }
    return render(request,'articles/index.html',context)


# index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <h1>qwe</h1>
  <p>{{ articles }}</p>
  {% for article in articles %}
  <p>{{article.pk}}</p>
  <p>{{article.title}}</p>
  <p>{{article.content}}</p>
  <hr>
  {% endfor %}
</body>
</html>
```
