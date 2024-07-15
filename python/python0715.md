 ## 파이썬 인터프리터를 사용하는 방법
1. shell 이라는 프로그램으로 한번에 한 명려어 씩 입력해서 실행
1. 확장자가 .py인 파일에 작성된 파이썬 프로그램을 실행

### vscode에서 파이썬 실행 방법
경로에 들어가서 
```
python <파일명>
```
### 표현식이 평가도어 값이 반환된다
3+5 는 표현식, 8은 값
순차적으로 평가하면서 프로그램의 동작을 결정

## 타입
변수나 값이 가질 수 있는 데이터의 종류

1. Numeric Type (int,float,complex)
2. Sequence Type(list,tuple,range)
3. Text Type(str)
4. Non-sequence Type(set,dict)

연산자 우선순위

**(지수) - -(음수) - *,/,//,%(곱셈,나눗셈 등등) - +,-(덧셈,뺄셈)

### 변수 
값을 참조하기 위한 이름

저장이 아닌 할당한다. (=) 할당 연산자


### 변수명 규칙 
1. 영문 알파벳, 언더스코어(_), 숫자로 구성
2. 숫자롤 시작할 수 없음
3. 대소문자를 구분
4. 파이썬의 내부 예약어 사용할 수 없음
 ```python
    ['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 
    'async', 'await', 'break', 'class', 'continue', 'def', 'del', 
    'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 
    'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 
    'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield'] 

```

### 진수 표현
- 2진수 : 0b
- 8진수 : 0o
- 16진수 : 0x

### 실수 연산 시 주의사항
Floating point rounding error(부동소수점 에러)

Decimal 모듈

#### 지수표현 방식
e or E를 사용하여 지수표현

## Sequemce Type
여러 개의 값을 순서대로 나열

1. 순서
   - 값들이 순서대로 저장 (정렬x)
2. 인덱싱
   - 각 값에 고유한 인덱스를 가지고 있으며 특정위치의 값을 선택하거나 수정가능
3. 슬라이싱
    - 인덱스 범위르를 조절해 부분적인 값을 추출할 수 있음
4. 길이 
   -len() 함수를 사용하여 저정된 값을 개수(길이)를 구할 수있음 
5. 반복
- 반복문을 사용하여 저장된 값들을 반복적으로 처리할 수 있음

  ### f-string
String Interpolation "f-string"

bugs = 'roaches'
counts = 13
area = 'living room'
``` 
print(f'Debugging {bugs} {counts} {area}')

Debugging roaches 13 living room
```

### slicing

[0:5:2] 0부터 5까지 2개마다 

[::-1] 뒤집기


구글링은 되도록 영어로 완벽한 문장이 아니어도 된다.

#### 신뢰할 수 있는 출처 활용

- 공식문서
- 개발자 커뮤니티 사이트