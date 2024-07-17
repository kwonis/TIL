# 함수 
특정 작업을 수행하기 위해 재사용 가능한 코드 묶음

## 함수의 구조
INPUT
BODY
OUTPUT

\`\`\`를 사용 하여 함수의 설명
```python
def 함수이름(매개변수(input)): 설명
return 반환 값 (함수의 종료 시점)
```

함수 호출로 함수 사용


print도 함수이고 print함수를 print하면 None이 나온다.
##  print 함수는 리턴이 없는 함수이다.
return 과 print는 다르다. 
print가 포함된 함수는 print 없이 함수만 호출해서 프린트 가능
### 매개변수
함수를 정의 할때 사용 

### 인자
호출 할때 사용

### 다양한 인자 종류
- 위치 인자
  - 반드시 값을 전달 누락 x (TypeError가 뜬다)
  - 순서가 바뀌어도 사용은 된다.
- 기본 인자 값
  - 기본 인자 값이 부여된 매개변수에 인자를 보내지 않으면 저장된 값 리턴
  - 인자가 있으면 인자값으로 리턴
- 키워드 인자
  - 호출시 매개변수 이름과 함께 값을 전달
  - 키워드 인자 사용 이후에는 위치인자 사용이 안된다.
  - 키워드 인자를 모두 사용하면 위치 변경해도 사용 가능
- 임의의 인자 목록
  - 갯수가 정해지지 않을때 매개변수 앞에 * 을 붙혀 사용하며 여러 개의 tuple로 처리
  - 뒤에는 위치인자가 위치 할 수 없다.
- 임의의 키워드 인자 목록
  - ** 를 붙여서 사용
  - 여러 개의 인자를 dict로 묶어서 처리
  
## 함수 인자 권장 작성순서
위치 -> 기본-> 가변 -> 가변 키워드

## 재귀 함수
함수 내에서 자기 함수를 다시 호출하는 함수

변수의 사용을 줄이고 가독이 높아질 수 있다.

1개 이상의 base case가 존재하고, 수렴하도록 작성

## 내장 함수
파이썬이 기본적으로 제공하는 함수

- len() 길이
- max() 최댓값
- min() 최솟값
- sum() 합 
- sorted(,reverse =True 사용하여 거꾸로) 정렬

### 유용한 함수

map(function, iterable)
요소에 함수를 하나하나 적용해서 하나의 맵 덩어리로 결과를 보내고 그것을 사용하여 확인 가능

zip(*iterables)

girls = ['jane','ashly]
boys =['peter,'jay]
pair = zip(girls, boys)

print(list(pair)) #[('jane', 'peter'), ('ashley,'jay)]

### scope
함수의 내부는 local scope / 그 외의 공간인 global scope

함수내에서 명시된 변수는 밖에서는 사용 불가능

### 변수 수명주기
1. built-in scope
  - 파이썬이 실행된 이후 부터 유지
2. global scope
  - 모듈이 호출 된 시점 이후 혹은 인터프리터가 끝날때까지
3. local scope
   - 함수가 호출될 떄 생성, 함수가 종료될때까지

안에서 밖으로 접근은 가능하지만 수정은 불가능

# LEGB Rule
내장함수를 변수명으로 사용시 내장함수 사용 불가능
안에서 부터 찾아나가기 때문이다.

변수의 스코프를 전역 범위로 지정하기 위해 사용
수정하기 위해

```python
num = 0  # 전역 변수


def increment():
    global num  # num를 전역 변수로 선언
    num += 1
```
선언 없이 할때 매개변수에는 사용 금지

### Packing & Unpacking
```python
다중 변수 값이면 한번에  tuple로 묵는다
```

*를 사용하여 패킹
numbers = [1, 2, 3, 4, 5]
a, *b, c = numbers
print(a)  # 1
print(b)  # [2, 3, 4]
print(c)  # 5


unpacking
a, b, c, d, e = packed_values
print(a, b, c, d, e)  # 1 2 3 4 5
갯수가 다르면 오류

dict 풀기가능 **를 사용하여

a,b,c = global_data.values()
a,b,c = global_data.keys()

my_dict = {'x': 1, 'y': 2, 'z': 3}
my_function(**my_dict)  # 1 2 3
매개변수와 인자의 키값이 맞아야한다.

## 람다 표현식 lamada

익명 함수  한줄로 간단한 함수

lamda 매개변수, 매개변수 ~~: 표현식
일회성을 쓸때 사용