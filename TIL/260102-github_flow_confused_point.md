# TIL — fetch / merge / branch / PR 헷갈림 정리 & 작업 루틴

## 왜 이 정리를 하게 되었는가
### Git을 사용하면서 가장 헷갈렸던 지점

- fetch와 merge의 차이와 **언제 써야 하는지**
- 브랜치에서 작업한 뒤
  → 계속 브랜치에서 해야 하는지
  → main으로 돌아가야 하는지
- 내가 **지금 어느 브랜치에 서 있는 상태에서**
  어떤 작업을 해야 하는지 판단이 어려웠음
- Pull Request 과정에서
  push는 됐는데 PR이 안 뜨는 이유,
  upstream 설정의 필요성 등

그래서 **개념 + 판단 기준 + 실제 루틴**을 한 번에 정리해본다.

---

## 1. fetch와 merge 개념 정리 (가장 헷갈렸던 부분)

### git fetch란?
> **원격 저장소의 변경 사항을 “가져오기만” 하는 명령어**

- 내 작업 파일은 바뀌지 않음
- “원격에 뭐가 바뀌었는지” 확인용

```
git fetch origin
git fetch upstream
```
👉 fetch = 정보만 업데이트

### git merge란?

> 가져온 변경 사항을 내 브랜치에 “합치는” 명령어
- 이때 파일이 실제로 바뀜
- 충돌(conflict)이 발생하는 시점
```
git merge origin/main
```
👉 merge = 실제 코드 변경

### 한 문장 요약

- fetch는 “보러 가는 것”,
- merge는 “가져와서 합치는 것”

## 2. 내가 어디에 서 있어야 하는지 판단 기준
- 항상 먼저 확인할 것
```
git branch
git branch --show-current
```
- “지금 내가 서 있는 브랜치가 어디냐”가 모든 판단의 시작

## 3. 브랜치 작업 기본 원칙 (이걸 기준으로 판단)

### 원칙 1️⃣ 작업은 항상 브랜치에서 한다

- 파일 생성
- 코드 수정
- 커밋

👉 ❌ main에서 직접 작업하지 않음
```
git switch fb

# 작업
git add .
git commit -m "feat: 작업 내용"
```
### 원칙 2️⃣ merge는 ‘합치려는 쪽’에서 한다

## 4. merge 상황별 정리 (여기서 가장 많이 헷갈림)

- 상황 A : main의 최신 내용을 내 브랜치에 반영하고 싶을 때
- 목적: “내 작업 중인데, main이 바뀌었으니 반영하고 계속 작업”

👉 브랜치에 서 있어야 한다
```
git switch fb
git fetch upstream
git merge upstream/main
```

- 상황 B : 브랜치 작업을 main에 합치고 싶을 때 (로컬 merge)
- 목적: “작업이 끝났고, main에 반영”

👉 main에 서 있어야 한다

```
git switch main
git fetch origin
git merge fb
```

※ 팀 프로젝트에서는 보통 이 단계는 PR로 대체

## 5. Pull Request 기준 작업 루틴 (정리)

### PR 기준 기본 흐름
1. 브랜치에서 작업
2. 브랜치에 commit
3. 브랜치를 origin(내 포크)에 push
4. GitHub에서 PR 생성
5. 리뷰
6. merge

## 6. upstream 설정 개념 & 이유
왜 upstream이 필요한가?
- origin = 내 포크
- upstream = 팀 원본 레포

👉 팀 프로젝트에서는
항상 “upstream/main”이 기준(mainline)

#### upstream 설정 방법
```
git remote add upstream https://github.com/팀레포주소.git
```

확인: git remote -v

## 7. Pull Request 하면서 헷갈렸던 점 & 해결
❓ 헷갈림 1: push 했는데 PR이 안 뜸

- 원인: push는 PR을 만들지 않음
- 해결: PR은 GitHub에서 직접 생성

> https://github.com/내계정/레포/pull/new/브랜치명

❓ 헷갈림 2: PR 링크가 갑자기 안 나옴

- 원인:새 커밋 없음
- 이미 브랜치가 존재
- 해결: 링크는 한 번만 안내되는 경우가 많음
- 규칙으로 직접 생성

❓ 헷갈림 3: PR이 팀 레포에 안 보임

- 원인: base repository가 내 포크로 설정됨
- 해결: PR 생성 시 반드시
- base: upstream 레포
- compare: 내 포크 브랜치

## 8. fetch / merge / PR 전체 판단 루틴 (핵심)
🔁 작업 시작 전

```
git fetch upstream
```
🔁 작업 중 (브랜치에서)
- 작업 + commit
```
git switch fb
```
🔁 main 변경사항 반영하고 싶을 때

```
git fetch upstream
git merge upstream/main
```
🔁 작업 완료 후
- GitHub에서 PR 생성

```
git push -u origin fb
```

![img.png](img.png)
