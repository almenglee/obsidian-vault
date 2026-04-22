# #1. title
주어진 초(second) 단위의 시간을 시:분:초 형태로 변환하는 프로그램을 작성하세요.

# 입력 설명

첫 번째 줄에 양의 정수 N(초)이 주어집니다. (1 ≤ N ≤ 86400)

# 출력 설명

"H:M:S" 형태로 시, 분, 초를 출력하세요.

## 예제 테스트케이스

#### 예제 1

입력

출력

3661

1:1:1

#### 예제 2

입력

출력

7200
## Answer

```python
# code
time = int(input())
print(time//3600, time%3600//60, time%60, sep=":")
```
---
# #1. title
N명의 학생이 시험을 보았습니다. 각 학생의 점수를 입력받아, 전체 학생의 평균 점수와 최저 점수를 계산하는 프로그램을 작성하세요.

# 입력 설명

첫 번째 줄에 학생의 수 N이 주어집니다.

두 번째 줄에 각 학생의 점수가 공백으로 구분되어 주어집니다. (0 ≤ 점수 ≤ 100)

# 출력 설명

첫 번째 줄에 "Average: " 뒤에 평균 점수를 소수점 둘째 자리까지 출력하세요.

두 번째 줄에 "Min: " 뒤에 최저 점수를 출력하세요.

## 예제 테스트케이스

#### 예제 1

입력

출력

4
85 90 78 92

Average: 86.25
Min: 78

#### 예제 2

입력

출력

3
100 95 85

## Answer

```python
# code
num = int(input())
arr = [int(x) for x in input().split()]

print(f"Average: {sum(arr)/num:.2f}")
print("Min:", min(arr))
```
---
# #1. title

N개의 정수가 주어질 때, 두 번째로 큰 수를 찾는 프로그램을 작성하세요. 같은 값이 여러 개 있더라도 고유한 값 기준으로 두 번째로 큰 수를 구합니다.

# 입력 설명

첫 번째 줄에 정수의 개수 N이 주어집니다. (N ≥ 2)

두 번째 줄에 N개의 정수가 공백으로 구분되어 주어집니다.

# 출력 설명

두 번째로 큰 수를 출력하세요. 모든 수가 같을 경우 그 수를 출력합니다.

## 예제 테스트케이스

#### 예제 1

입력

출력

6
3 1 4 1 5 9

5

#### 예제 2

입력

출력

5
10 20 30 40 50

## Answer

```python
# code
num = int(input())
arr = sorted(set(int(x) for x in input().split()))

print(arr[-1] if len(arr) == 1 else arr[-2])
```
---
# #1. title

N개의 숫자가 주어질 때, 그 중 소수(Prime Number)만을 찾아 출력하는 프로그램을 작성하세요. 소수란 1과 자기 자신 외에는 나누어떨어지지 않는 2 이상의 자연수입니다.

# 입력 설명

첫 번째 줄에 숫자의 개수 N이 주어집니다.

두 번째 줄에 N개의 숫자가 공백으로 구분되어 주어집니다. (1 ≤ 숫자 ≤ 1000)

# 출력 설명

소수인 숫자들만 입력 순서대로 공백으로 구분하여 출력하세요. 소수가 없을 경우 "None"을 출력합니다.

## 예제 테스트케이스

#### 예제 1

입력

출력

8
4 7 10 11 15 17 23 24

7 11 17 23

#### 예제 2

입력

출력

6
5 6 11 13 17 19

5 11 13 1

## Answer

```python
# code
def isprime(x):
    if x < 2:
        return False
    for i in range(2, int(x**.5)+1,1):
        if x % i == 0:
            return False
    return True

  

num = int(input())
arr = [int(x) for x in input().split()]

primes = " ".join(str(x) for x in arr if isprime(x))

print(primes if primes != "" else "None")
```
---
# #1. title

문자, 숫자, 특수문자가 섞인 문자열이 주어집니다. 이 문자열에서 알파벳(영문자)만 추출하여 출력하는 프로그램을 작성하세요.

# 입력 설명

첫 번째 줄에 문자열이 주어집니다. 문자열의 길이는 100 이하입니다.

# 출력 설명

알파벳만 추출하여 출력하세요. 알파벳이 없을 경우 "None"을 출력합니다.

💡 힌트: Python에서 문자가 알파벳인지 확인하려면 isalpha() 메서드를 사용할 수 있습니다.

## 예제 테스트케이스

#### 예제 1

입력

출력

H3ll0W0rld!

HllWrld

#### 예제 2

입력

출력

abc123

abc

## Answer

```python
# code
msg = "".join(ch for ch in input() if ch.isalpha())

print(msg if msg != "" else "None")
```
---
# #1. title

비밀 요원이 남긴 암호를 해독하려면, 문자열을 뒤집은 후 대문자는 소문자로, 소문자는 대문자로 바꿔야 합니다. 암호를 해독하는 프로그램을 작성하세요.

# 입력 설명

첫 번째 줄에 암호 문자열이 주어집니다. 문자열은 알파벳으로만 구성되며 길이는 100 이하입니다.

# 출력 설명

뒤집힌 문자열에서 대소문자를 반전하여 출력하세요.

## 예제 테스트케이스

#### 예제 1

입력

출력

HaLlO

oLlAh

#### 예제 2

입력

출력

Python
## Answer

```python
# code
print("".join(ch.lower() if ch.isupper() else ch.upper() for ch in input()[::-1]))
```
---
# #1. title

N개의 정수가 주어졌을 때, 양수, 음수, 0의 개수를 각각 세어 출력하는 프로그램을 작성하세요.

# 입력 설명

첫 번째 줄에 정수의 개수 N이 주어집니다.

두 번째 줄에 N개의 정수가 공백으로 구분되어 주어집니다.

# 출력 설명

첫 번째 줄에 "Positive: " 뒤에 양수의 개수를 출력하세요.

두 번째 줄에 "Negative: " 뒤에 음수의 개수를 출력하세요.

세 번째 줄에 "Zero: " 뒤에 0의 개수를 출력하세요.

## 예제 테스트케이스

#### 예제 1

입력

출력

7
3 -1 0 5 -2 0 7

Positive: 3
Negative: 2
Zero: 2

#### 예제 2

입력

출력

5
1 2 3 4 5

Positive: 5
Negative: 0

## Answer

```python
# code
num = int(input())

arr = [int(x) for x in input().split()]

pos = 0
neg = 0

for x in arr:
    if x >0:
        pos+=1
    elif x < 0:
        neg +=1

print("Positive:",pos)
print("Negative:",neg)
print("Zero:", num-pos-neg)
```
---
# #1. title

창고에 상자들이 쌓여 있습니다. 각 상자에는 고유 번호가 있으며, 짝수 번호의 상자를 앞쪽에, 홀수 번호의 상자를 뒤쪽에 배치해야 합니다. 원래 순서는 유지하면서 재배치하는 프로그램을 작성하세요.

# 입력 설명

첫 번째 줄에 상자의 개수 N이 주어집니다.

두 번째 줄에 N개의 상자 번호가 공백으로 구분되어 주어집니다. (1 ≤ 번호 ≤ 100)

# 출력 설명

짝수 번호는 앞에, 홀수 번호는 뒤에 배치된 상자 번호를 공백으로 구분하여 출력하세요.

## 예제 테스트케이스

#### 예제 1

입력

출력

6
5 8 2 7 6 3

8 2 6 5 7 3

#### 예제 2

입력

출력

5
9 2 4 5 7

## Answer

```python
# code
num = int(input())

arr = [int(x) for x in input().split()]

print(*[x for x in arr if x%2<1], *[x for x in arr if x%2])
```
---
# #1. title

직사각형의 가로 W와 세로 H가 주어질 때, 대각선의 길이를 계산하는 프로그램을 작성하세요. 대각선의 길이는 √(W² + H²)입니다.

# 입력 설명

첫 번째 줄에 가로 길이 W가 주어집니다.

두 번째 줄에 세로 길이 H가 주어집니다.

# 출력 설명

대각선의 길이를 소수점 둘째 자리까지 출력하세요.

💡 힌트: Python에서 제곱근은 math.sqrt() 또는 ** 0.5로 계산할 수 있습니다.

## 예제 테스트케이스

#### 예제 1

입력

출력

3
4

5.00

#### 예제 2

입력

출력

5
12

## Answer

```python
# code
print(f"{(int(input())**2 + int(input())**2)**.5:.2f}")
```
---
# #1. title

1부터 N까지의 정수 중에서 짝수만 골라 합산하는 프로그램을 작성하세요.

# 입력 설명

첫 번째 줄에 양의 정수 N이 주어집니다. (1 ≤ N ≤ 1000)

# 출력 설명

1부터 N까지의 짝수의 합을 출력하세요.

## 예제 테스트케이스

#### 예제 1

입력

출력

10

30

#### 예제 2

입력

출력

7

## Answer

```python
# code
n = int(input())//2
print(n(n+1))
```
---
