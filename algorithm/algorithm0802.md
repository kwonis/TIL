# String

컴퓨터에서 문자는 숫자로 바꿔 저장

영어 대소문자를 6비트로 모드 표현 할 수 있으며 이것을 코드체계라고 부른다.

```python 
# iunput = 'abc'
s1 = list(input()) # s1 = ['a','b','c']
s2 = input() # s2 = 'abc'
```

```python
# strlen
i =0 
while a[i] = '\0':
  i+=1
print(i)
```

문자열 비교에서는 == 연산은 메모리 참조가 같은지를 묻는 것

```python
s1 ='abc'
s2='abc'
s3='def'
s4=s1
s5=s1[:2] +'c'

print(s1 == s5) # True
print(s4 == s5)# True
print(s1 is s5) # False
print(s4 is s5) # False


```