# Contributing Guide

## 1. 문서 목적

이 문서는 오픈소스SW 및 협업실무 4주 팀 Git 미션을 수행하면서  
팀원들이 같은 방식으로 Git과 GitHub를 사용하기 위해 만든 협업 규칙입니다.

우리 팀은 이 문서를 기준으로 branch 생성, commit 작성, push, Pull Request, review, merge, conflict 해결 과정을 진행합니다.

이 저장소의 목표는 단순히 파일을 완성하는 것이 아니라,  
GitHub에 협업 과정이 기록되도록 하는 것입니다.

---

## 2. 기본 협업 원칙

우리 팀은 다음 원칙을 지킵니다.

1. `main` branch에는 직접 작업하지 않습니다.
2. 모든 작업은 개인 branch 또는 issue branch에서 진행합니다.
3. 작업 전에는 항상 원격 저장소의 최신 내용을 가져옵니다.
4. commit message는 작업 내용을 알 수 있게 작성합니다.
5. Pull Request를 만든 뒤 최소 1명 이상의 review를 받습니다.
6. 충돌이 발생하면 파일을 바로 삭제하지 않고 `git status`를 먼저 확인합니다.
7. 오류나 충돌이 발생하면 `docs/error-log.md` 또는 `docs/conflict-log.md`에 기록합니다.
8. 한 사람이 모든 작업을 대신하지 않고, 팀원 모두가 branch, commit, PR, review를 직접 경험합니다.

---

## 3. 작업 시작 전 준비

작업을 시작하기 전에는 항상 `main` branch를 최신 상태로 맞춥니다.

```bash
git checkout main
git pull origin main --no-rebase

---

## 4. branch 이름 규칙

종류/issue번호-작업내용

ex) docs/3-readme-intro
feature/4-team-rule
fix/5-readme-typo
chore/6-create-weekly-folder

## 5. Commit Message 규칠

종류: 작업 내용

ex) docs: add README intro
docs: update contributing guide
fix: correct team member name
chore: create weekly folders
refactor: reorganize README sections

## 6. Commit 단위 규칙

commit은 의미 있는 작업 단위로 나누어 작성합니다.

ex) docs: add README intro
docs: add team member table
docs: add repository structure

## 7. Issue 사용 규칙

작업을 시작하기 전에 GitHub Issue를 생성하고 담당자를 정합니다.

Issue에는 다음 내용을 작성합니다.

## 작업 내용
- 어떤 파일을 수정할 것인지 작성합니다.
- 어떤 내용을 추가하거나 수정할 것인지 작성합니다.

## 완료 조건
- [ ] branch를 생성했습니다.
- [ ] commit을 남겼습니다.
- [ ] Pull Request를 생성했습니다.
- [ ] review를 받았습니다.

## Issue 제목 예시
README에 팀원 표 추가
CONTRIBUTING.md 협업 규칙 작성
docs/command-note.md 명령어 정리
docs/error-log.md 오류 기록 추가

## 8. 작업 진행 순서

우리 팀의 기본 작업 흐름은 다음과 같습니다.

1. Issue를 만든다.
2. 담당자를 정한다.
3. main branch를 최신 상태로 가져온다.
4. 작업 branch를 만든다.
5. 파일을 수정한다.
6. git status로 변경 내용을 확인한다.
7. git add로 commit할 파일을 선택한다.
8. git commit으로 변경 내용을 기록한다.
9. git push로 GitHub에 branch를 올린다.
10. Pull Request를 만든다.
11. 팀원의 review를 받는다.
12. 문제가 없으면 merge한다.
13. 관련 issue를 닫는다.

## 9. Pull Request 작성 규칙

작업 branch를 push한 뒤 GitHub에서 Pull Request를 생성합니다.

PR 제목은 작업 내용을 알 수 있게 작성합니다.

## 10. Review 규칙

Pull Request는 최소 1명 이상의 팀원이 확인합니다.

review는 단순히 “확인”이라고 쓰지 않고, 실제로 읽어 본 내용을 바탕으로 구체적으로 작성합니다.

## 11. Merge 규칙

Pull Request는 다음 조건을 만족한 뒤 merge합니다.

최소 1명 이상의 review가 있다.
conflict가 없다.
PR 설명에 작업 내용이 작성되어 있다.
관련 issue가 연결되어 있다.
main branch에 직접 작업하지 않았다.

merge 후에는 로컬 main branch도 최신 상태로 갱신합니다.

## 12. Conflict 발생 시 해결 규칙

git status로 충돌 파일을 확인한다.
충돌 파일을 열어 conflict marker를 확인한다.
어떤 내용을 남길지 팀원과 결정한다.
<<<<<<<, =======, >>>>>>> 표시를 모두 삭제한다.
최종 내용을 저장한다.
git add로 해결한 파일을 추가한다.
git commit으로 충돌 해결 내용을 기록한다.
docs/conflict-log.md에 원인과 해결 방법을 작성한다.

## 14. Conflict 기록 규칙

충돌이 발생하면 docs/conflict-log.md에 아래 형식으로 기록합니다.

## 충돌 기록 1

### 발생 파일
docs/conflict-practice.md

### 발생 상황
두 branch에서 같은 파일의 같은 줄을 서로 다르게 수정했습니다.

### 충돌 원인
Git이 두 변경 사항 중 어떤 내용을 최종으로 남겨야 하는지 자동으로 판단할 수 없었습니다.

### 충돌 내용
- A branch 내용: 초보자를 위한 Git 협업 연습 도구
- B branch 내용: 팀 프로젝트 관리를 돕는 오픈소스 도구

### 최종 결정
초보자도 팀 프로젝트를 쉽게 관리할 수 있도록 돕는 Git 협업 연습 도구

### 사용한 명령어
git status
git add docs/conflict-practice.md
git commit -m "resolve team project intro conflict"

### 배운 점
같은 파일의 같은 줄을 서로 다르게 수정하면 충돌이 발생할 수 있으며,
충돌은 Git 오류가 아니라 사람이 최종 내용을 결정해야 하는 상황입니다.

## 14. 오류 발생 시 기록 규칙

Git 명령어를 사용하다 오류가 발생하면 오류 메시지를 지우지 말고 기록합니다.

기록 위치 : docs/error-log.md

오류 기록 양식

## 오류 기록 1

### 발생 상황
push를 하려고 했지만 rejected 오류가 발생했습니다.

### 오류 메시지
rejected because the remote contains work that you do not have locally

### 원인
원격 저장소의 main branch가 내 로컬 저장소보다 더 최신 상태였습니다.

### 해결 방법
먼저 원격 저장소의 최신 내용을 가져온 뒤 다시 push했습니다.

### 사용한 명령어
git pull origin main --no-rebase
git push origin branch-name

### 배운 점
push가 거절되면 원격 저장소가 더 최신일 수 있으므로 먼저 pull을 해야 합니다.

## 15. README 수정 규칙

README.md는 저장소를 처음 보는 사람이 가장 먼저 읽는 문서입니다.

README에는 다음 내용이 포함되어야 합니다.

저장소 소개
팀원 정보
저장소 구조
Git 협업 흐름
주차별 미션 요약

README를 수정할 때는 문장이 너무 짧거나 불명확하지 않도록 작성합니다.

## 16. 문서 작성 규칙

문서를 작성할 때는 다음 규칙을 지킵니다.

제목은 #, ##, ###을 사용해 단계적으로 작성합니다.
목록은 - 또는 숫자 목록을 사용합니다.
명령어는 코드 블록 안에 작성합니다.
파일명과 branch 이름은 백틱으로 표시합니다.
문장은 의미가 분명하게 드러나도록 작성합니다.

## 17. 개인별 작업 기록 규칙

각 팀원은 자신의 members/이름.md 파일에 Git 작업 기록을 남깁니다.