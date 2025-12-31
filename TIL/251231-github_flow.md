# TIL 03 — Git Branch 전략 · GitHub Flow · Pull Request 협업 정리

## 학습 목표
- git의 다양한 branch 전략을 이해하고 GitHub Flow를 활용해 프로젝트를 수행한다.
- GitHub Issue / Project를 활용해 이슈를 관리한다.
- git을 통해 타인과 협업하고 Pull Request로 코드 기여를 경험한다.

---

## 1. Git Branch 전략 개념 정리

### 왜 branch 전략이 필요한가?
- 여러 명이 동시에 작업하면 main 브랜치가 쉽게 망가질 수 있음
- 작업 단위를 분리해 **안정적인 코드 관리**가 필요

### 대표적인 branch 전략 개요
- Git Flow:
  - main / develop / feature / hotfix 등 다단계 구조
  - 대규모, 릴리즈 중심 프로젝트에 적합
- GitHub Flow (이번 강의 핵심):
  - main + feature branch 구조
  - Pull Request 중심 협업
  - 단순하고 실무 친화적

---

## 2. GitHub Flow 핵심 개념

### GitHub Flow 기본 규칙
1. main 브랜치는 항상 배포 가능한 상태 유지
2. 작업 단위마다 새로운 branch 생성
3. 작업 완료 후 commit & push
4. Pull Request 생성
5. Code Review
6. Merge

👉 **branch는 작업 공간**
👉 **Pull Request는 협업의 중심**

---

## 3. GitHub Issue & Project 관리

### Issue의 역할 : 작업지시서, 업무분장용
- 해야 할 작업을 문서로 남김
- 팀원 간 작업 범위 명확화

### 기본 흐름
1. Issue 생성 ( Description, Tasks, Reference)
2. Issue 기반 branch 생성
3. 작업 후 PR에서 Issue 연결
4. PR merge 후 Issue close

---

## 4. 팀 프로젝트 협업 구조

### 팀장 역할
- Organization / Repository 생성
- Issue Template, Label 관리
- Pull Request 리뷰 및 Merge

### 팀원 역할
- Issue 기반 작업 정의
- Fork → Branch → Commit → Push
- Pull Request 생성
- 리뷰 반영

---

## 5. Pull Request 전체 흐름 정리(중요)

### 1️⃣ Fork & Clone
```bash
git clone {주소}

2️⃣ 작업 브랜치 생성
git branch : 브랜치 리스트 확인
git switch -c {브랜치명} : 없으면 생성하기

3️⃣ 코드 작성 (예시)
# fizzbuzz.py
# 1부터 15까지 반복하며 FizzBuzz 출력
for i in range(1, 16):
    # 3과 5의 공배수인 경우
    if i % 15 == 0:
        print("fizzbuzz")
    # 3의 배수인 경우
    elif i % 3 == 0:
        print("fizz")
    # 5의 배수인 경우
    elif i % 5 == 0:
        print("buzz")
    # 그 외의 경우 숫자 출력
    else:
        print(i)

4️⃣ commit & push
git add . # 작업한 내용 전체 add
git commit -m "feat: implement fizzbuzz logic"
git push -u origin fb
```

## 6. Pull Request 생성 방식 정리
- PR은 자동 생성되지 않는다
- git push = 브랜치를 원격에 올리는 행위
- PR = “이 브랜치를 main에 합쳐달라”는 요청 문서

- PR 생성 링크 규칙 https://github.com/내계정/레포/pull/new/브랜치명
  - 예시: https://github.com/happia1/251231-fb/pull/new/fb

## 7. Pull Request 하면서 헷갈렸던 점 & 해결

#### ❓ 헷갈림 1: push 했는데 PR이 안 뜸
- 원인: push는 PR을 생성하지 않음
- 해결: GitHub에서 직접 PR 생성

#### ❓ 헷갈림 2: PR 링크가 갑자기 안 나옴

- 원인: 새 커밋이 없거나 브랜치가 이미 존재하는 경우
- 해결: 링크는 한 번만 안내되는 편의 기능, 규칙으로 직접 URL 생성

#### ❓ 헷갈림 3: base / compare 개념 혼란
- base: 합쳐질 대상 (팀 원본 레포의 main)
- compare: 내 작업 브랜치 (fork의 fb)
- 해결: PR 생성 시 반드시 base repository가 upstream(팀 레포) 인지 확인

#### ❓ 헷갈림 4: fetch / merge 타이밍
- fetch: 원격 변경 사항 확인용 (내 파일 안 바뀜)
- merge: 실제 코드 합칠 때 사용

## 8. 오늘 강의 핵심 요약

GitHub Flow는 branch 전략이 아니라 협업 전략
Pull Request는 코드 병합 도구이자 커뮤니케이션 도구
push와 PR은 역할이 완전히 다름
PR은 자동 생성되지 않으며, 사용자가 명시적으로 만든다
