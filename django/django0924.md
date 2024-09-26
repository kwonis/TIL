# Read
단일 게시글 조회

url 작성 
```python 
def detail(request,pk):
    article = Article.objects.get(pk=pk)
    context = {
        'article' : article,
    }
    return render(request,'articles/detail.html',context)
```

### GET method

1. 데이터 전송
    - 쿼리 문자열을 통해 전송하기에 크기 제한
2. 브라우저 히스토리에 남게됨(뒤로가기 기능 저장을 사용)
3. 캐싱
  - 로컬에 저장할 수 있어서 서버에 접속하지 않고 저장
  - 페이지 로딩 시간 단축
- GET은 조회 요청때에만 사용

## POST method
변경 ( 생성, 수성 ,삭제)
DB를 건들여야하는 문제
1. 데이터 전송
2. 데이터 제한
3. 브라우저 히스토리
4. 캐싱 데이터 없음
예시
- 로그인 정보 제출
- 파일 업로드 
- 새 데이터 생성
- api에서 데이터 변경 요청


GET을 POST 로 바꾸고 나니 403에러 CRSF 토큰이 없다는 오류 

```
{% csrf_token %}
```
django 에서 만들어서 응답마다 새로운 토큰 생성

HTTP response status code 
응답 반응 

post일때 token 이 필요한 이유
생성, 수정 ,삭제를 요구 하기 때문에 db조작에 필요한 인증수단이다.

# Redirect
사용자가 get 요청을 한번더 보낸다.

# DELETE
```python
path('<int:pk>/delete/',  views.delete,name='delete')


def delete(request,pk):
    article =Article.objects.get(pk=pk)
    article.delete()
    return redirect('articles:index')
```


아래 코드를 사용하여 정렬순을 바꿀 수 있다.
```
Restaurant.objects.all().order_by('name(변수명)')
```