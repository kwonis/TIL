# Model
class로 작성
Database 관리를 함.

테이블을 생성
id는 django가 자동으로 생성

```python
class Article(models.Model):
    title = models.CharField(max_length=10)
    content = models.TextField()

# 이미 만들어진 모델클래스를 상속 받아서 사용
```
# Model Field

## Field Types
데이터의 종류

- 문자열  필드
  - CharField,TextField
- 숫자 필드
  - IntegerField, FloatField
- 날짜/시간 필드
  - DateField, TimeField, DateTimeField
- 파일 관련 필드
  - FileField, ImageField


### CharField()
제한된 길이의 문자열을 저장 (max_length는 필수 이다.)

## 주요 필드 옵션
- null
  - 빈값은 사용 불가
- blank 
  - form에서 빈 값을 허용할지 여부 결정
- default
  - 필드의 기본값 설정

# Migrations
model 클래스의 변경사항을 db에 최종 반영하는 방법

 ```python 
python manage.py makemigrations

python manage.py migrate
 ```

 데이터베이스 테이블에 이름은

앱이름 _ 클래스이름으로 생성됨

DateTimeField 는 날짜와 시간 가능

auto_now
데이터가 저장될 때마다 자동으로 현재 날짜시간을 저장

auto_now_add
처음 생성될 때만 자동으로 현재 날짜시간을 저장

이미 생성된 테이블에 필드를 추가해야한다면??
질문을 1번 2번 질문을 하게됨
데이터 추가가 필요하기 때문에 
1을 입력하면 그상태그대로 진행
2번은 대화를 종료

0002 데이터는 새로 만들어진게 아니라 원래 있는것에 추가가 되는것이기에 이전꺼가 없어지면 작동 안됨.

admin
데이터 확인 및 테스트 등을 진행하는데 매우 유용

```python admin 계정 생성 명령어
python manage.py createsuperuser
```


admin site에 등록

```python
# admin.py 파일
from django.contrib import admin
from .models import Article
# Register your models here.
admin.site.register(Article)
```

$ python manage.py showmigrations
migrate 됐는지 안됐는지 여부 확인
$ pytohn manage.py sqlmigrate articles 0001
sql 언어로 번역되어 전달되는 확인하는 명령어