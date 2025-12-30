# TIL

How to start git

## Template

- filename:./TIL/251229.md

### 251229

## 오늘 한 것

## 1. 오늘의 목표

- Git과 GitHub의 기본 개념 이해
- GitHub 저장소 생성 후 로컬과 연결
- 파일 생성 → 수정 → 커밋 → 푸시까지 전체 흐름 실습

---

## 2. GitHub 저장소 생성

### 저장소 만들기
1. GitHub → **New Repository**
2. 저장소 이름 설정
3. Public 선택
4. License 선택
5. `README.md` 생성 옵션 선택

> 이 단계에서 **원격 저장소(GitHub)** 가 생성된다.

---

## 3. 로컬에 저장소 연결 (clone)

```
git clone {repo_address}
cd {repo_name}
```

### 기본 명령어

* `pwd` : 현재 위치 확인
* `git clone` : GitHub 저장소를 로컬로 복사
* `cd` : 해당 프로젝트 폴더로 이동
* `ls` : 현재 폴더 안 파일/폴더 목록 확인
* `cd ..` : 상위 폴더로 이동
* `git status` : 현재 git 상태 확인

---

## 4. 폴더와 파일 생성

### 폴더 만들기

```bash
mkdir my_project
cd my_project
ls
```

### 파일 만들기

```bash
touch main.py
touch README.md
```

---

## 5. README.md 작성 가이드

README는 **저장소의 소개 문서** 역할을 한다.

### 기본 구성 예시

* **Project name** : 프로젝트 이름
* **Description** : 한 줄 설명
* **Prerequisites** : 요구사항
* **How to Start** : 실행 방법
**Installation** : 설치 방법
**Features** : 주요 기능
* **Tests (optional)** : 테스트 방법

---
## 6. Vim 기본 조작 (파일 수정)

```bash
vi {file_name}
```

### 기본 조작

* `i` : 입력 모드
* `ESC` : 명령 모드
* `:wq` : 저장 후 종료
* `:q!` : 저장하지 않고 종료

### 파일 내용 확인

```bash
cat README.md
```

---

## 7. Git 초기화 (로컬에서 시작할 때만)

```bash
git init
ls -a
```

* `.git` 폴더 생성 확인
* `.git` 폴더가 있어야 git 저장소로 인식됨

> **주의**
>
> * GitHub에서 `clone`한 저장소에는 `.git` 폴더가 이미 존재
> * 이 경우 `git init`을 다시 실행하면 안 됨

---

## 8. 원격 저장소 연결

```bash
git remote add origin {repo_address}
git remote -v
```

* `origin` : 원격 저장소의 기본 이름
* `git remote -v` : 연결 여부 확인

---

## 9. 변경 사항 관리 (add → commit → push)

### 상태 확인

```bash
git status
```

### 스테이징

```bash
git add README.md
git add .
```

### 커밋

```bash
git commit -m "docs: add README"
```

---

## 10. 커밋 메시지 규칙 (Conventional Commit)

| Prefix   | 의미      |
| -------- | ------- |
| feat     | 기능 추가   |
| fix      | 버그 수정   |
| docs     | 문서 수정   |
| refactor | 코드 리팩토링 |
| chore    | 기타 작업   |
| config   | 환경 설정   |
| build    | 빌드 작업   |
| style    | 코드 포맷   |
| test     | 테스트 관련  |
| ci       | CI 설정   |

---

## 11. 브랜치 및 푸시

```bash
git push -u origin main
```

* `-u` 옵션을 사용하면 이후 `git push`만 입력해도 됨

---

## 12. 기본 작업 루틴 (암기용)

```bash
git status
git add {file_name}
git commit -m "message"
git push origin main
```

---

## 13. 오늘 배운 핵심 요약

* Git은 **로컬에서 버전 관리를 위한 도구**
* GitHub는 **원격 저장소 서비스**
* Git은 **폴더 단위**로 동작하며 `.git` 폴더가 핵심
* 기본 흐름은 항상
  **수정 → add → commit → push**



## 내일 할 것

git branch 배우기


## 이슈

1. 레포지토리 만들어서 주소 복사하고 git bash에 clone하기
2. mkdir로 폴더 만들고 그 안에 touch로 파일 만들기
3. README 파일은 이 작업의 소개글 생성 -> 목차가 있음
4. 파일 수정은 vi {파일명}
5. 파일 저장은 esc -> :wq
6. 저장한 내용 확인은 cat {파일명}
7. 파일 깃헙 등록하는 절차는 add -> commit(prefix작성) -> push -> 브랜치 확인

여기까지 오늘 배운 내용 총정리
다양한 배경지식은 강의중간에 들었지만 기억이 하나도 나질 않음..
세상 대단한 개발자들이 참 많다고 느꼈다. 
git도 열받아서 만들었는데 개발자의 95% 이상 사용하고있을정도 라고 하네..
멋진일이고 신기한일이다.
나도 영향력을 가진 사람이고싶다는 생각이 든다.
오늘 한 작업들은 기초중의 기초, 바닥을 잘 다지는 공부들이니 열심히 해놔야지
오늘 한것들은 그리 어렵다는 생각은 들지 않는데 순서가 뒤죽박죽되어서 좀 난감하긴 했다.
일단 git 초기화는 왜하는지 잘 모르겠어서 GPT에 물어봤는데,
내가 깃헙에서 레포지토리를 만들어 내 로컬에 클론하지 않고, 로컬에서 먼저 프로젝트를 만드는 경우에
나중에 깃헙에 올리고싶으면 폴더를 만들고 그폴더 안에 git init 명령을 치면 폴더 안에 .git이라는 숨김폴더가 생긴다
.git이 있으면 git status가 되는데, 없으면 레포지토리가 없다고 나온다
그래서 로컬로 먼저 프로젝트를 만들어서 그걸 깃헙에 올릴때는 init으로 깃폴더를 만들어준 다음 
git remote add origin {github_repo_url}
git push -u origin main 
으로 깃헙에 push해줘야 한다.
깃헙에서 클론해서 로컬에 저장한 경우 .git폴더가 이미 있어서 이때는 절대 init을 하면 안됨


