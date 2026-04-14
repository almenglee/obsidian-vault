## range 끝값

```python
range(1, 100)   # 1~99 ❌
range(1, 101)   # 1~100 ✅
```
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
s.islower()
"ab" in s
"".join()
```

---

## 문자열 처리 패턴

### 뒤집기

```python
s[::-1]
```
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
