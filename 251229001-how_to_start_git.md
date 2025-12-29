# TIL

How to start git

## Template
---

TIL

- filename:./TIL/251229.md

# 251229

## 오늘 한 것

레포지토리 만들기
1. 깃헙 저장소에서 New Repository 생성
2. 이름 설정, public, License 선택
3. README.md 생성

만든 레포지토리 API키 발급해서 내git bash에서 연결해주기
git clone {repo_address}
cd {repo_name}

- pwd : 현재 위치 확인
- git clone : github에 있는 레포를 내 컴퓨터로 복사
- cd : 해당 프로젝트 폴더로 이동
- git status : 현재 상태 확인하기
- cd : 현재 폴더 안에 있는 파일, 폴더의 목록 확인
- cd .. : 폴더 밖으로 나오기

폴더 만들기
- mkdir my_project :폴더 생성하기
- cd my_project : 폴더 안으로 이동
- ls : 폴더 안이 비어있는지 확인

파일 만들기
- touch main.py 
- touch README.md


README.md 작성가이드
- # Projejct name 프로젝트 이름
한 줄 설명
- ## Prerequisites 요구사항
- ## How to Start 프로젝트 실행방법
- ## Installation 설치방법
- ## Features 기능
- ## Run Tests(optional) 테스트 방법
- ## Credit 프로젝트 기여자

기본 조작
- i : 입력 모드
- esc : 명령 모드
- :wq 저장 후 종료
- :q! 저장 안하고 종료


파일내용보기
- cat README.md

Git초기화
- git init
- ls -a
- .git 폴더 생성 확인

원격저장소 주소 연결하기
git remote add arigin {repo_address}
연결확인
git remote -v
작업상태확인
git status


수정하기
- vi {file name}


.gitignore 만들기
- touch .gitignore



변경사항 스테이징
- git add README.md
- git add .

커밋 기록 남기기
- git commit

prefix : 커밋 메시지 규칙
- feat: 기능 추가
- fix: 버그 수정
- docs: 문서 수정
- refactor: 코드 리팩토링
- chore: 기타작업
- config: 환경설정
- build: 빌드 작업
- style: 코드 포매팅
- test: 테스트관련
- ci: continous intergration 관련


브랜치 확인 설정
- git push -u origin main

작업 루틴
- git status
- git add {file name} 
- git commit
- git push origin main



## 내일 할 것

## 이슈


