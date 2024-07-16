## List

변경가능하다는 특징
0개 이상의 객체를 포함

[ ]를 사용하여 표기

데이터 제한 없음 모든 타입 가능

## Tuple

변경불가능하다는 특징

( )를 사용하여 표기

(1,) ,없이 (1)은 그냥 int로 되기 때문에 요소가 1개이면 ,가 필요

내부 동작에서 주로 사용됨

## range
연속된 정수를 생성하는 변경 불가능한 자료

range(시작, 끝, 증가)
range(n)
- 0부터 n-1 까지
range(n,m)

# Non - sequence Types

## dict
- key -value 1개의 쌍
- 순서와 중복이 없다
- 변경 가능

key는 변경 불가능한 자료형만 값은 제한없음

딕셔너리는 key에 접근하여 값을 얻어내야한다.

```
my_dict = {'apple': 12, 'list': [1, 2, 3]}

print(my_dict['apple'])
#12

# {'apple': 12, 
'list': [1, 2, 3], 'banana': 50}
my_dict['banana'] =50

```

## set (집합자료형)

{}를 사용하여 표시

a = {} #딕셔너리

set() #빈집합일때


## Other type

None == 값이 없을을 표현
N은 대문자

Boolean
False ore True

## Collection

여러개를 당으면 collectin


# 형변환

## 암시적 형변환
자동으로 수행되는 형변환

```
print (3 +5.0) # 8.0
print (TRUE + #4) # 4
print (True + False)# 1
```

## 명시적 형변환

int - str / str - int


# 연산자

## 복합연산자

==는 동등성, is는 식별성

값만 비교하는 == 와 는 다르게 저장된 값을 비교
is 는 보통 None - Bool 에  주소까지 확인한다.

## 단축평가
코드 실행을 최적화하고, 불필요한 연산을 피할 수 있도록함
```
print(('a' and 'b') in vowels)  - . 'b'in vowels #False

print(('b' and 'a') in vowels)  - . 'a'in vowels #False
```

## 멤버십 연산자

딕셔너리는 key를 확인


## 백준 풀다가

max()
sum()
mix()
를 사용해서 함수 사용가능 




