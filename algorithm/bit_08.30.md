# 비트연산
1bit : 0과 1을 표현하는 정보의 단위
1Byte : 8bit를 묶어 1 Byte

비트연산 - 컴퓨터의 cpu는 0과 1로 다루어 동작되며, 내부적으로 비트 연산을 사용하여 덧셈, 뺄셈,곱셈 등을 계산한다.

 2진수, 16진수 ,10지누 변환하여 출력하기

 2진수는 0b를 접두사로 (0b1010)  / int('1011',2)
 16진수는 0x를 접두사로 (0xa)  / int('b',16)

 ### XOR 
 다르면 1 같으면 0
 - 7070 ^ 1004 = 6258
 - 6258 ^ 1004 =7070

## 2의보수(컴퓨터의 음수) 찾기
10001 의 2의 보수
수를 모두 뒤집고 +1
01110 +1 =01111

NOT 연산자를 사용하여 모든 비트를 반전시킨다.
bin(4) (0b100)
bin(~4) (-0b101) (-5)