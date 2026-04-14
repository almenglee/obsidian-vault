
# **1. 변수 & 기본 자료형**
  
## **타입 확인 / 변환**

```
type(x)
int("10"), float("3.5"), str(10)
```

## **문자열 핵심**

```
s = "abcde"
s[1:4]      # 'bcd' slicing

len(s)
s.lower(), s.upper()
"ab" in s   # True
```

---

# **2. 리스트 (List)**

## **생성 / 접근**

```
arr = [1, 2, 3]
arr[0]
arr[-1]
```

## **자주 쓰는 연산**

```
arr.append(4)
arr.pop()           # 마지막 제거
arr.sort()          # 오름차순
arr.reverse()
len(arr)
sum(arr)
max(arr), min(arr)
```

## **반복**

```
for x in arr:
    print(x)

for i in range(len(arr)):
    print(arr[i])
```

---

# **3. 딕셔너리 & 튜플**

  

## **딕셔너리**

```
d = {"a": 1, "b": 2}

d["a"]          # 1
d["c"] = 3

for k in d:
    print(k, d[k])

for k, v in d.items():
    print(k, v)
```

## **튜플 (immutable)**

```
t = (1, 2, 3)
x, y, z = t
```

---

# **4. 반복문**

  

## **for**

```
for i in range(5):          # 0~4
for i in range(1, 6):       # 1~5
for i in range(0, 10, 2):   # 0,2,4,6,8
```

## **while**

```
i = 0
while i < 5:
    i += 1
```

## **break / continue**

```
for i in range(10):
    if i == 5:
        break
```

---

# **5. 함수**

```
def f(x):
    return x * 2

def f(x, y=10):     # default parameter
    return x + y
```

## **여러 값 반환**

```
def f():
    return 1, 2

a, b = f()
```

---

# **6. 핵심 알고리즘 패턴 (시험 필수)**

---

## **6.1 소수 판별 (n < 100)**

```
def is_prime(x):
    if x < 2:
        return False
    for i in range(2, int(x**0.5) + 1):
        if x % i == 0:
            return False
    return True
```

### **리스트에서 소수 찾기**

```
result = []
for x in arr:
    if is_prime(x):
        result.append(x)
```

---

## **6.2 두 문자열 공통 문자**

  

### **set 사용 (추천)**

```
a = "abcde"
b = "bdf"

common = set(a) & set(b)
```

### **순서 유지 버전**

```
res = []
for c in a:
    if c in b and c not in res:
        res.append(c)
```

---

## **6.3 리스트 합**

```
sum(arr)
```

또는 직접 구현:

```
total = 0
for x in arr:
    total += x
```

---

## **6.4 별 출력 (기본)**

```
n = 5
for i in range(n):
    print("*" * (i+1))
```

---

## **6.5 피라미드 출력**

```
n = 5
for i in range(n):
    print(" " * (n-i-1) + "*" * (2*i+1))
```

---

# **7. 시험에서 자주 쓰는 트릭**

  

## **7.1 membership**

```
x in arr
x in string
```

## **7.2 swap**

```
a, b = b, a
```

## **7.3 리스트 생성 (컴프리헨션)**

```
[x for x in arr if x % 2 == 0]
```

---

# **8. 실전 전략 (중요)**

- 소수 문제 → **√n까지만 검사**
    
- 문자열 문제 → **set 먼저 고려**
    
- 출력 문제 → **패턴 규칙 먼저 찾기**
    
- 리스트 문제 → sum, max, min 적극 사용
    
- 중복 제거 → set 또는 not in
    

---

# **핵심 요약**

- 반복문 + 조건문 = 거의 모든 문제 해결 가능
    
- 문자열/리스트는 **index + 슬라이싱 + membership**
    
- 시험은 “구현 능력” 테스트 → 복잡한 이론 없음
    

---

원하면 **기출 스타일 문제 + 풀이 세트**도 만들어 드리겠습니다.