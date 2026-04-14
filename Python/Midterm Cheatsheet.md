좋습니다. 기존 노트는 기본기가 잘 잡혀 있고, 내가 만든 치트시트는 실전 최적화에 가까웠습니다.  
두 개를 **통합 + 보강 + 실수 방지 중심으로 재구성**하면 아래가 가장 효율적인 최종 형태입니다.

불필요한 중복은 제거하고, **시험장에서 바로 쓰는 구조**로 압축했습니다.

---

# ✅ Python 중간고사 Cheat Sheet (최종 통합본)

---

# 🔴 0. 실수 방지 (가장 중요)

## range 끝값

```python
range(1, 100)   # 1~99 ❌
range(1, 101)   # 1~100 ✅
```

---

## 완전제곱수 (float 비교 금지)

```python
int(x**0.5)**2 == x   # ✅
```

---

## 나눗셈

```python
/   # float
//  # int (시험에서 자주 요구)
```

---

## split

```python
input().split()   # ✅
input().split(" ") # ❌ 비추천
```

---

## set 사용 시 순서

```python
list(set(arr))           # ❌ 순서 깨짐
list(dict.fromkeys(arr)) # ✅ 순서 유지
```

---

## 출력

```python
print(arr)   # ❌
print(*arr)  # ✅
```

---

# 🟢 1. 입력 & 기본

```python
n = int(input())
arr = list(map(int, input().split()))
s = input().strip()
```

---

# 🟢 2. 문자열 핵심

```python
s[i]
s[1:4]
len(s)

s.lower(), s.upper()
"ab" in s
```

---

## 문자열 처리 패턴

### 뒤집기

```python
s[::-1]
```

### 치환

```python
"".join('*' if c in "aeiouAEIOU" else c for c in s)
```

### 모음 / 자음 개수

```python
vowels = "aeiouAEIOU"

v = sum(1 for c in s if c in vowels)
c = sum(1 for c in s if c.isalpha() and c not in vowels)
```

---

# 🟢 3. 리스트 핵심

## 기본

```python
arr = [1,2,3]
arr.append(x)
arr.pop()
arr.sort()
arr.reverse()
```

---

## 필수 builtin

```python
sum(arr)
min(arr)
max(arr)
len(arr)
```

---

## 반복

```python
for x in arr:
    ...

for i in range(len(arr)):
    ...
```

---

## 가장 큰 두 수의 곱

```python
arr.sort()
print(arr[-1] * arr[-2])
```

---

## 중복 제거

```python
list(dict.fromkeys(arr))
```

---

# 🟢 4. 딕셔너리 & 튜플

```python
d = {"a":1}
d["b"] = 2

for k in d:
    print(k, d[k])

for k, v in d.items():
    print(k, v)
```

```python
t = (1,2,3)
a,b,c = t
```

---

# 🟢 5. 반복문

```python
for i in range(5)
for i in range(1,6)
for i in range(0,10,2)
```

```python
while condition:
    ...
```

---

## break / continue

```python
if condition:
    break
```

---

# 🟢 6. 함수

```python
def f(x):
    return x
```

```python
def f(x, y=10):
    return x+y
```

---

# 🟢 7. 핵심 알고리즘 (시험 필수)

---

## 소수 판별

```python
def is_prime(x):
    if x < 2:
        return False
    for i in range(2, int(x**0.5)+1):
        if x % i == 0:
            return False
    return True
```

---

## 완전제곱수

```python
def is_square(x):
    return int(x**0.5)**2 == x
```

---

## 공통 문자

### set (빠름)

```python
set(a) & set(b)
```

### 순서 유지

```python
res = []
for c in a:
    if c in b and c not in res:
        res.append(c)
```

---

## 리스트 필터

```python
[x for x in arr if 조건]
```

---

## 합 직접 구현

```python
total = 0
for x in arr:
    total += x
```

---

# 🟢 8. 출력 포맷

```python
print(f"{value:.2f}")
print(*arr)
```

---

# 🟢 9. 패턴 출력

## 기본

```python
for i in range(n):
    print("*"*(i+1))
```

---

## 피라미드

```python
for i in range(n):
    print(" "*(n-i-1) + "*"*(2*i+1))
```

---

## 다이아몬드

```python
for i in range(n):
    print(" "*(n-i-1) + "*"*(2*i+1))

for i in range(n-2, -1, -1):
    print(" "*(n-i-1) + "*"*(2*i+1))
```

---

## X자

```python
for i in range(n):
    for j in range(n):
        if i == j or i+j == n-1:
            print("*", end="")
        else:
            print(" ", end="")
    print()
```

---

# 🔵 10. 시험용 핵심 트릭

```python
x in arr
x in string
```

---

```python
a, b = b, a   # swap
```

---

```python
[x for x in arr if 조건]
```

---

# 🔥 11. 실전 전략 (이게 점수 만든다)

- 소수 → **√n까지만**
    
- 문자열 → **set 먼저 고려**
    
- 리스트 → **builtin 적극 사용**
    
- 출력 → **format 정확히**
    
- 패턴 → **규칙 먼저 찾고 구현**
    
- 중복 제거 → **dict.fromkeys 또는 set**
    
- 완전제곱수 → **float 비교 절대 금지**
    
- range → **끝값 항상 확인**
    

---

# 결론

이 치트시트 수준이면 이미 “개념 부족” 단계가 아닙니다.

👉 점수를 깎는 요소는 단 하나:

- **range / 출력 형식 / 사소한 조건 실수**
    

특히 당신이 실제로 했던 실수:

> `range(1,100)` → 100 누락

이런 유형이 시험에서 가장 위험합니다.

---

원하면  
👉 “교수가 낼 법한 문제 + 함정까지 포함된 예상 문제 세트” 만들어드리겠습니다.