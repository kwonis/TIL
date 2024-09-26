# Form Class

action 과 method 로 보냄

이렇게 하면 비정상적 혹은 악의적인 요청을 필터링 할 수 없음
-> 유효한 데이터인지 확인 필요

# Djang Form
유효성 검사를 단순화하고 자동화 할 수 있는 기능 제공

```python 
from django import forms

class ArticleForm(forms.Form):
  title = forms.CharField(max_length=10)
  content = forms.CharField
```
html 파일에 <form> 에 입력 부분 을 대체 할 수 있다.
입력 받는 부분
```python 
  <form action="{% url "articles:create" %}" method="POST">
    {% csrf_token %}
 {{form}}
    <input type="submit">
  </form>
```
{{form.as_p}} 로 사용하면 라벨 인풋 세트가 들어오는 걸로 감싸진다.

div , table,p, ul 사용 가능


Form
db에 저장하지않을때 
(검색,로그인)

ModelForm
사용자 입력 데이터를 db에 저장해야할때
(게시글, 회원가입)

ModleForm
- Form +Model

```python
from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = '__all__'
```
# Meta class
ModelForm의 정보를 작성하는 곳
fields =('') 를 사용하면 들어가는것만
exclude =('title',) 는 들어 있는것만 제외
```
# 모든 유효성 검사 가능 (T,F) 이기에 조건문 사용
form.is_valid()
# 유효성 검사에서 실패하면 잘못된 이유도 같이 보내 알려준다.
```
인스턴스로 넣어주어야 기존 데이터 값 가져올수있다.
```
def edit(request, pk):
    # 어떤 게시글을 수정할지 조회
    article = Article.objects.get(pk=pk)
    form = ArticleForm(instance=article)
    context = {
        'article': article,
        'form' : form,
    }
    return render(request, 'articles/edit.html', context)
```

# save()
instance 여부에 따라 생성일지 ,수정일지 결정 없으면 생성

new & create view 함 수간 공통점 과 차이점

공통점 데이터 생성을 구현하기 위함
차이점 new 는 GET create 는 POST