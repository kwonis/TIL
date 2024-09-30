# HTTP
리소스들을 가져올 수 있도록 해주는 규약
웹에서 이루어지는 모든 데이터 교환의 기초

## 특징

1. 비 연결 지향
   - 서버는 요청에 대한 응답을 보낸 후 연결을 끊음
2. 무상태
   - 연결을 끊는 순간 클라이언트와 서버 간의 통신이 끝나며 상태 정보가 유지되지 않음

# 쿠키(Cookie)
서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각

동작 예시

웹 서버에 페이지 요청  - 페이지와 쿠키를 포함해서 전송 - 저장소에 저장 (만료시간,도메인,주소) - 같은 웹서버에 요청할때 쿠키를 포함하여 전송 - 쿠키를 통해 사용자 식별 - 새로운 쿠키를 설정하거나 기존 쿠키 수정

1. 쿠키 저장 방식
   - KEY - VALUE의 데이터 형식으로 저장

### 쿠키 사용 목적

1. 세션 관리
  - 로그인,아이디 자동완성,공지 하루 안 보기, 팝업 체크, 장바구니 등의 정보관리
2. 개인화
  - 사용자 선호 설정
3. 트래킹
  - 사용자 행동을 기록 및 분석

# 세션
서버 측에서 생성되어 클라이언트와 서버 간의 상태를 유지
상태 정보를 저장하는 데이터 저장 방식

작동원리
1. 클라이언트가 로그인 요청 후 인증에 성공하면 서버가 세션 테이터를 생성 후 저장
2. 생성된 세션 데이터에 인증 할 수 있는 세션 id 발급
3. 발급한 세션 id 를 클라이언트에 응답
4. 클라이언트는 응답 받은 세션 id를 쿠키에 저장
5. 클라이언트가 다 시 동일한 서버에 접속하면 요청과 함께 쿠키를 전달
6. 쿠키는 요청 때마다 서버에 함께 전송 되므로 서버에서 id를 확인해 로그인 되었다는 것을 계속해서 확인하도록함

# Django Authentication System
인증 신원 확인 사용자가 누구인지 확인하는 것.

기본 user model 의 한계
- Django의 기본 User 모델은 username, password 등 제공되는 필드가 매우 제한적
- 추가 정보를 위하 User Model변경에 어려움을 가짐

Custom User Model로 대체하기

AbstractUser 클래스를 상속받는 커스텀 User 클래스 작성

기존 user 클래스도 AbstractUser를 상속받기 때문에 완전히 같은 모습을 가짐.

```python 
#settings.py
AUTH_USER_MODEL = 'accounts.User'

```
로 변경

```python
#accounts/admin.py
from django.contrib.auth.admin iimport USerAdmin
from .models import User

admin.site.register(User,UserAdmin)
```

중간에 변경할수 없기 때문에 변경하려면 초기화가 필요


AuthenticationForm()

# Template with Authentication data

