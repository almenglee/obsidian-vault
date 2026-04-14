# 📘 Discrete Mathematics Midterm Cheat Sheet (Markdown)

> 범위: Logic, Sets & Numbers, Proofs, Matrix  
> 기반: 실제 과제 문제 + 정답 패턴

---

# 1. Logic (명제 논리)

## 1.1 기본 변환 규칙

### Implication 제거

p→q≡¬p∨qp → q ≡ ¬p ∨ q

### Negation

¬(p∧q)≡¬p∨¬q¬(p∨q)≡¬p∧¬q¬(p ∧ q) ≡ ¬p ∨ ¬q ¬(p ∨ q) ≡ ¬p ∧ ¬q

### 핵심 패턴

- **Implication 부정**
    

¬(p→q)≡p∧¬q¬(p → q) ≡ p ∧ ¬q

👉 시험에서 매우 자주 나옴

---

## 1.2 Truth Table 핵심 결과

|표현|결과|
|---|---|
|p ∨ ¬p|항상 True (tautology)|
|p ∧ ¬p|항상 False (contradiction)|
|¬¬p|p|

---

## 1.3 Logical Equivalence

- 분배법칙:
    

p∧(q∨r)≡(p∧q)∨(p∧r)p ∧ (q ∨ r) ≡ (p ∧ q) ∨ (p ∧ r)

- DeMorgan:
    

¬(A ∩ B) = A̅ ∪ B̅

---

## 1.4 Quantifier 핵심

- 순서 중요:
    

∀x∃y≠∃y∀x∀x ∃y ≠ ∃y ∀x

- 예시:
    
- ∀x ∈ (3,4] ∃y > x → ❌ (최댓값 존재)
    
- ∀x ∃y < x → ⭕
    

---

## 1.5 XOR

p⊕q≡(p∧¬q)∨(¬p∧q)p ⊕ q ≡ (p ∧ ¬q) ∨ (¬p ∧ q)

---

# 2. Sets & Numbers

## 2.1 기본 연산

|연산|의미|
|---|---|
|A ∪ B|합집합|
|A ∩ B|교집합|
|A − B|차집합|
|A̅|여집합|

---

## 2.2 포함 관계

- 핵심:
    

A∩B=A⇒A⊆BA ∩ B = A ⇒ A ⊆ B

- 항상 참:
    

B⊆C⇒A∪B⊆A∪CB ⊆ C ⇒ A ∪ B ⊆ A ∪ C

---

## 2.3 Power Set

∣P(A)∣=2∣A∣|P(A)| = 2^{|A|}

- 예:
    

```text
∅ → 0
{∅} → 1
```

👉 nested 구조 주의

---

## 2.4 Inclusion-Exclusion

∣A∪B∣=∣A∣+∣B∣−∣A∩B∣|A ∪ B| = |A| + |B| - |A ∩ B|

👉 문제에서 반드시 사용  
예: 13 + 16 - x = 23 → x = 6

---

## 2.5 Interval 계산

- 핵심:
    

```text
A = [-5,1], B = (-1,3)
```

```text
A ∪ B = [-5,3)
A ∩ B = (-1,1]
```

👉 경계 포함 여부 실수 주의

---

## 2.6 Cardinality

∣A×B∣=∣A∣⋅∣B∣|A × B| = |A| · |B|

---

## 2.7 Number Systems

### Binary → Decimal

```text
1101₂ = 13
```

### Decimal → Binary

- 계속 2로 나눔
    

---

## 2.8 Base Arithmetic

- base-n:
    

```text
carry occurs if sum ≥ n
```

---

## 2.9 1’s Complement

- 양수: 그대로
    
- 음수: 비트 반전
    

예:

```text
5 → 0101
-5 → 1010
```

---

# 3. Proof Techniques

## 3.1 Direct Proof

형식:

```text
가정 → 전개 → 결론
```

---

## 3.2 Contrapositive (가장 중요)

p→q≡¬q→¬pp → q ≡ ¬q → ¬p

예:

```text
9x+19 even ⇒ x odd
```

👉 실제 풀이:

- x even 가정 → 모순 유도
    

---

## 3.3 Proof by Contradiction

```text
가정: 명제 false
→ 모순 도출
```

예:

```text
a+b odd인데 둘 다 even → 모순
```

---

## 3.4 Divisibility Proof

핵심 템플릿:

a∣b⇒b=kaa|b ⇒ b = ka

예:

b=ka,c=ja→b+c=(k+j)a→a∣(b+c)b = ka, c = ja → b+c = (k+j)a → a|(b+c)

👉 시험에서 그대로 쓰면 됨

---

## 3.5 Set Proof

P(C)∪P(D)⊆P(C∪D)P(C) ∪ P(D) ⊆ P(C ∪ D)

패턴:

1. x ∈ LHS 가정
    
2. subset 관계 변환
    
3. RHS 도달
    

---

# 4. Matrix

## 4.1 Matrix Operations

### Addition

- 같은 크기만 가능
    

### Multiplication

(m×n)(n×k)→(m×k)(m × n)(n × k) → (m × k)

👉 dimension mismatch = DNE

---

## 4.2 Matrix Size Rules

예:

```text
A: 3×4, B: 2×3
→ BA: 2×4
```

---

## 4.3 Determinant

### 기본 성질

- row swap → 부호 반전
    
- triangular matrix:
    

det=diagonalproductdet = diagonal product

👉 매우 중요

---

## 4.4 Cofactor / Minor

det(A)=ΣaijCijdet(A) = Σ a_{ij} C_{ij}

---

## 4.5 Inverse

A−1exists⇔det(A)≠0A^{-1} exists ⇔ det(A) ≠ 0

---

## 4.6 Row Operations

|연산|영향|
|---|---|
|swap|sign change|
|multiply row|det × k|
|add row|no change|

---

## 4.7 Gaussian Elimination

목표:

```text
REF → RREF
```

패턴:

1. pivot 만들기
    
2. 아래 제거
    
3. 위 제거 (Jordan)
    

---

## 4.8 Linear System

Ax=bAx = b

- augmented matrix 사용
    
- 해:
    
    - unique
        
    - infinite
        
    - none
        

---

## 4.9 Special Matrices

|형태|특징|
|---|---|
|symmetric|A = Aᵀ|
|skew-symmetric|A = -Aᵀ|

👉

A+AT→symmetricA−AT→skew−symmetricA + A^T → symmetric A - A^T → skew-symmetric

---

# 🔥 시험 핵심 전략 (중요)

## 1. Logic

- implication 부정 = **p ∧ ¬q**
    
- truth table 대신 **패턴 암기**
    

## 2. Sets

- **inclusion-exclusion 거의 필수**
    
- power set vs subset 구분
    

## 3. Proof

- contrapositive / contradiction 둘 다 준비
    
- divisibility template 암기
    

## 4. Matrix

- dimension 먼저 확인
    
- determinant → triangular로 만들기
    
- row operation 영향 정확히 기억
    

---

# ✅ 한 줄 요약

> 이 시험은 "개념 이해"보다  
> **패턴 인식 + 공식 적용 속도 싸움**입니다.

---

원하면  
👉 “시험 예상 문제 세트 (난이도별)”도 만들어드리겠습니다.