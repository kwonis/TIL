## 모듈
ex. math 내장 모듈

모듈을 가져오는 방법
```
1. import math
print(math.sqrt(4))

2. form math import sqrt
print(sqrt(4))
(모듈의 함수인지 내가만든 함수인지에 대해 문제가 생길수도 있다.)
```

똑같은 이름의 함수를 사용하게 되면 가장 마지막에 import된 이름으로 대체

### 파이썬 표준 라이브러리
파이썬 언어와 함께 제공되는 다양한 모듈과 패키지의 모음

패키지 : 연관된 모듈들을 하나의 디렉토리에 모아 놓은 것

패키지 사용법
```
from 문서 경로 import py이름
from my_package.math import my_math
from my_package.statistics import tools
```

외부 패키지를 설치 하기 위한 명령어 `pip`

설치 방법으로는 최신 버전/특정 버전 ==/최소 버전 >=

`requests` api 요청을 하기위한 패키지 활용 다수

전역환경에 설치해서 다른곳에서도 사용 가능

# 제어문
코드의 실행 흐름을 제어하는 데 사용되는 구문
조건과 반복으로 코드를 실행

### 조건문 
if,elif,else

### 반복문
for, while

### 반복문 제어
break, continue, pass


반복문 
for는 종료 시점이 보인다
while는 종료 시점을 모른다 조건에서 벗어나야만 종료된다.

for 단수형 in 복수형 형식을 맞추자.

중첩 반복문에 횟수 == len(outers) *len(inners)
while은 참인동안 반복, 거짓이 될때 까지


### 반복문 제어 키워드

- break
  반복을 즉시 중지
- continue
  다음 반복으로 건너뜀
- pass
  아무런 동작 하지않고 넘어감


  flag variable 기준점

  ## list comprehension 
  간결하고 효율적인 리스트 생성 방법

  특징 : 한줄로 작성

  if 문도 추가 가능 뒤쪽에

comprehension을 남용하지 말자

목적은 리스트 생성이다.

"""

성능 비교

1. list comprehension
    - 대부분의 경우 가장 빠르고 파이썬스러운(Pythonic) 방법
2. map
    - 특정 상황(예: 기존 함수를 사용할 때)에서 리스트 컴프리헨션과 비슷하거나 약간 더 빠를 수 있음
3. loop
    - 일반적으로 가장 느리다고 알려져 있지만,
      python 버전이 올라가면서 다른 방식과 비슷하거나 때로는 더 나은 결과를 보이기도 함
    - 복잡한 로직이 필요한 경우에는 여전히 유용하게 사용될 수 있음

결론
- 성능 차이는 대부분의 경우 미미하므로, 
  코드의 가독성과 유지보수성을 고려하여 상황에 맞는 적절한 방법을 선택하는 것을 권장
"""

enumerate(interable, start =0(인덱스 시작번호))
```
fruits = ['apple', 'banana', 'cherry']

for index,fruit in enumerate(fruits):
  print(f'인덱스 {index}: {fruit}')

  인덱스 0: apple
  인덱스 1: banana
  인덱스 2:cherry
```