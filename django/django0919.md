# Template system
표현을 제어하고 관련 부분 담당

#### HTML의 콘텐츠를 변수 값에 따라 변경하기 
views 파일에서 변수 값 정의
```python 
def index(request):
    context ={
        'name' :'alice',
    }
    return render(request, 'articles/index.html',context)
```
이후 html 파일에서 사용
```python
{{ name }}
```
# DTL Syntax
1. Variable
2. Filters
3. Tags
4. Comments

Filters
변수를 수정할 때 사용 (변수 + | 필터)
```python 
{{ variable | filter}}
{{name | truncatewords :30}}
```

Tags
반복 또는 논리를 수행하여 제어 흐름을 만듦
일부는 시작과 종료 태그 필요

```python
{% tag %}
{% if %} {% endif%}
```

```python
<body>
  <h1>디너</h1>
  <p>{{ picked }} 메뉴는 {{ picked|length}} 글자입니다.</p>
  <ul>
    {% for food in foods %} 
    <li>{{food}}</li>
    {% endfor%}
  </ul>

  {% if foods|length == 0 %}
  <p>메뉴가 소진 되었습니다.</p>
  {% else%}
  <p>아직 메뉴가 남았습니다.</p>
  {% endif %}
</body>
```
# 템플릿 상속

```python 
    {% block content%}
    {% endblock content%}

    # 상속받는곳에 가서 
{% extends "articles/base.html" %}
{%block content%}
<h1>안녕하세요! {{ name }} </h1>
{%endblock content%}
```
extends tag 는 가장위에 위치해야한 상속가능 2개 이상 사용 불가

# 요청과 응답

form 은 요청을 서버에 보내는 가장 편한 방법

```python 
{% extends 'articles/base.html' %}

{% block content %}
<form action ='https://search.naver.com/search.naver?where=nexearch&sm=top_hty&fbm=0&ie=utf8&' method='GET'>
  <label for="message">검색어</label>
  <input type="text" name ='query' id ='message'>
  <input type="submit" value ='submit'>
</form>
{% endblock content %}
```
- action
  입력 데이터가 전송될 URL (name 속성 햇심)
- method 
  어떤 방식으로 보낼 것인지 정의

throw / catch
```python
def throw(request):
    return render (request,'articles/throw.html')

def catch(request):
    message = request.GET.get('message')
    context = {
        'message' : message
    }
    return render (request,'articles/catch.html',context)
#throw.html
<h1>Throw</h1>
<form action="http://127.0.0.1:8000/catch/" method='GET'>
  <input type="text" id='message' name='message'>
  <input type="submit">
</form>
```

# Variavle Routing
```python
path('hello/<str:name>/' ,views.greeting),
path('hello/<int:num>/' ,views.detail),
```
# App URL mapping

```python
path('articles/', include('articles.urls')),

```

# Naming URL patterns

path 함수에 3번째 인자에 name ='' 작성
이후 사용할때
{% url 'ar ' ' index' %} == www./ar/index

앱이 많아 지면
app_name ='앱이름' 작성하면
'앱이름 : 링크' 로 작성가능

