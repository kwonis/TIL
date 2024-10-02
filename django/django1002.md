# 회원 가입

UserCreationForm()
회원 가입시 사용자 입력 데이터를 받는 모델폼

회원가입 시 
manager isn`t availanle 'auth.User' han been swapped for 'accounts.User'
에러 발생

meta 에 model = user 이기에 재작성이 필요.

django에서는 유저를 직접 참조하는 것을 권장하지 않는다.

get_user_model() 을 사용하여 유저모델 간접 참고 가능 

UserChangeForm 의 문제점

모든 필드가 출력되므로 출력되지않아야하는부분 조정해야함..

비밀번호 변경
PAsswordChangeForm()

# 세션 무효화 방지

- 비밀번호 변경 후 기존 세션과의 회원 인증 정보가 이치하지 않음
update_session_auth_hash(request,user)
암호 변경 시 세션 무효화를 막아주는 함수

## 인증된 사용자에 대한 접근 제한
- is_authenticated(속성)
- login _ required(데코레이터)

login_required()
인증된 사용자 경우 view 함수 실행 
비인증 경우 accounts/login/주소로 redirect
