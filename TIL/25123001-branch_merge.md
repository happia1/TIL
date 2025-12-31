# Git Branch & Merge Conflict
**TIL | 25-12-30**

---

## 오늘의 학습 목표

- git의 **branch**를 활용해 코드 관리하기
- git branch 사용 중 발생하는 **Merge Conflict**를 직접 해결해보기

---

## 1. GitHub 기능 이해

### GitHub의 주요 기능
- **Issues** : 업무 문서, 작업지시서 역할 - 버그, 할 일, 논의 사항 등을  관리
- **Projects** : 칸반 보드 형태의 작업 관리
- **Pull Request(PR)** : 브랜치 간 변경 사항 리뷰 및 병합-> Issue작성시 #으로 연결 가능
- **Actions** : CI/CD 자동화
- **Settings** : 저장소 설정 관리

---

## 2. GitHub 기능 설정 실습

- Issues 활성화 / 비활성화
- Projects 생성 및 관리
- 저장소 설정 확인

---

## 3. Pre-commit 개념 및 실습

### Pre-commit이란?
- **commit 전에 자동으로 코드 체크를 수행**
- 실수로 잘못된 코드가 커밋되는 것을 방지
- url : https://pre-commit.com/hooks.html 에서 필요한 hook 찾아서 적용

### Pre-commit의 역할
- 코드 스타일 검사
- 포맷팅 검사
- 간단한 오류 사전 차단

### Pre-commit 사용방법

$ pip install pre-commit
$ pre-commit --v 로 pre-commit 명령어 인식유무 확인
$ pre-commit sample-config > .pre-commit-config.yaml
$ pre-commit install 하여 commit 시 자동실행하기 (강제실행은 $ pre-commit run)
작업 -> add, commit -> pre-commit 동작 및 자동수정 -> 수정사항 add, commit -> 완료
https://pre-commit.com/hooks.html 추가 방법
-   repo: https://github.com/psf/black
    rev: stable
    hooks:
    - id: black
      language_version: python3.14.2
-   repo: https://github.com/PyCQA/flake8
    rev: 7.0.0
    hooks:
    - id: flake8

---

## 4. Branch란 무엇인가?

### Branch의 개념
- 하나의 코드 베이스에서 **독립적인 작업 흐름**
- main 브랜치는 항상 **안정적인 상태 유지**
- 기능/실험은 branch에서 진행

---

## 5. Branch 생성 및 사용

### Branch 생성

- git branch {branch-name} : 브랜치 생성
- git switch {branch-name} : 브랜치로 이동
- git branch : 브랜치 목록 확인

## 6. Branch별 작업 및 Merge
Branch에서 작업
git switch feature-branch

# 코드 수정
1. git add .
2. git commit -m "feat: 작업 내용"
3. main으로 merge

- git switch main
- git merge feature-branch
기능 개발 후 main에 반영하는 기본 흐름 기억해두기

## 7. Branch 관리
더 이상 필요 없는 브랜치 삭제

git branch -D {branch-name} : merge되지 않은 브랜치 강제 삭제

## 8. Merge Conflict란?
Merge Conflict 발생 조건
- 같은 파일
- 같은 줄
- 서로 다른 브랜치에서 다르게 수정

## 9. Merge Conflict 해결 (merge 방식)

1. Conflict 발생
2. git merge {branch-name}
3. 충돌 파일 확인

$$
<<<<<<< HEAD
main 브랜치 내용
=======
feature 브랜치 내용
>>>>>>> feature-branch
$$

### 해결 방법
- main 내용 유지
- branch 내용 유지
- 두 내용을 조합하여 새로 작성
- 충돌 표시(<<<<<<<, =======, >>>>>>>)는 모두 제거해야 함

### 해결 후
- git add {file}
- git commit -m "merge: resolve conflict"

## 10. Merge Conflict 해결 (rebase 방식)
Rebase 개념
브랜치의 기준을 다른 브랜치 위로 재배치
커밋 히스토리를 더 깔끔하게 정리

- git switch feature-branch
- git rebase main
충돌 발생 시
충돌 해결 후

- git add {file}
- git rebase --continue

## Today Commnets

branch 까지는 괜찮은데 conflict 만드는것 부터 막히기 시작했다.
merge conflict 하는것도 방식이 두가지가 있는데 그 두가지가 아직은 개념구분이 잘 안간다. merge 방식과 rebase방식 두가지인데 이건 자꾸 해봐야 알 듯 하다. 그래도 어제보다는 타이핑하는게 많이 익숙해진듯..
