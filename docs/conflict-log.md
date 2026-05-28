# Conflict Log

## 3주차 충돌 해결 기록

### 1. 자동 병합 실습

#### 관련 Issue
#16 3주차 자동 병합 실습

#### 발생 파일
docs/auto-merge.md

#### 실습 내용
두 명이 같은 파일의 서로 다른 줄을 수정했다.

- A 담당자: 설명 줄 수정
- B 담당자: 상태 줄 수정

#### B 담당 작업 내용
B 담당자는 `상태: 준비 중` 줄을 `상태: B 담당자 수정 완료`로 수정했다.

#### 결과
A 담당자와 B 담당자가 서로 다른 줄을 수정했기 때문에 Git이 자동 병합할 수 있는지 확인하는 실습을 진행했다.

#### 사용한 명령어
```bash
git checkout main
git pull origin main --no-rebase
git checkout -b docs/week3-auto-merge-b
git status
git diff
git add docs/auto-merge.md
git commit -m "docs: update auto merge status"
git push origin docs/week3-auto-merge-b
```
#### 배운 점
같은 파일을 수정하더라도 서로 다른 줄을 수정하면 항상 충돌이 발생하는 것은 아니다. Git은 변경 위치가 겹치지 않으면 자동으로 병합할 수 있다.

---

### 2. 같은 줄 충돌 실습

#### 관련 Issue
#17 3주차 같은 줄 충돌 실습

#### 발생 파일
docs/conflict-practice.md

#### 충돌 원인
두 branch가 같은 파일의 같은 줄을 서로 다르게 수정했다. 먼저 한 branch를 main에 merge한 뒤, 다른 branch를 merge하려고 하면서 Git이 어느 내용을 선택해야 하는지 자동으로 판단하지 못해 conflict가 발생했다.

#### 충돌 내용
- A branch: 프로젝트 한줄소개를 A안으로 수정
- B branch: 프로젝트 한줄소개를 B안으로 수정

#### 최종 결정
팀에서 최종 문장을 결정한 뒤 conflict marker를 삭제하고 하나의 문장으로 정리했다.

#### 사용한 명령어
```bash
git status
git add docs/conflict-practice.md
git commit -m "resolve line conflict"
git push origin main
```
#### 배운 점
같은 파일을 수정하더라도 서로 다른 줄이면 자동 병합될 수 있지만, 같은 줄을 서로 다르게 수정하면 Git이 자동으로 판단하지 못해 충돌이 발생할 수 있다. 충돌이 발생하면 conflict marker를 확인하고 사람이 최종 내용을 선택해야 한다.

---

### 3. 삭제/수정 충돌 실습

#### 관련 Issue
#18 3주차 삭제/수정 충돌 실습

#### 발생 파일
docs/notice.md

#### 충돌 원인
한 branch에서는 docs/notice.md 파일을 삭제했고, 다른 branch에서는 같은 파일을 수정했다. 먼저 한 branch가 main에 merge된 뒤 다른 branch를 merge하려고 하면서 Git이 파일을 유지할지 삭제할지 자동으로 결정하지 못해 modify/delete conflict가 발생했다.

#### 충돌 내용
- A branch: docs/notice.md 파일 삭제
- B branch: docs/notice.md 파일 수정

#### 최종 결정
팀에서 파일을 유지할지 삭제할지 결정한 뒤, 최종 상태에 맞게 파일을 정리했다.

#### 사용한 명령어
```bash
git status
git rm docs/notice.md
# 또는 파일을 유지한 경우
git add docs/notice.md
git commit -m "resolve modify delete conflict"
git push origin main
```

#### 배운 점
삭제/수정 충돌은 Git이 파일의 최종 상태를 자동으로 결정할 수 없는 상황이다. 따라서 팀원이 직접 파일을 유지할지 삭제할지 판단하고, 그 결과를 git add 또는 git rm으로 반영해야 한다.

