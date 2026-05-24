## Modify/Delete Conflict 실습

### 발생 파일
docs/notice.md

### 충돌 원인
A의 branch에서는 docs/notice.md 파일을 삭제했고, 
B의 branch에서는 docs/notice.md 파일을 수정했다.

### 충돌 상황
- docs/delete-notice branch: docs/notice.md 삭제 후 main에 merge
- docs/update-notice branch: docs/notice.md 수정
- B 역할 PR 화면에서 Merge conflicts가 표시되었다.

### 최종 결정
docs/notice.md 파일을 수정상태로 유지하기로 하였다.

### 사용한 명령어
git checkout -b docs/delete-notice
git rm docs/notice.md
git commit -m "docs: delete notice file"
git push origin docs/delete-notice
git checkout main
git pull origin main --no-rebase
git checkout -b docs/update-notice
notepad docs/notice.md
git add docs/notice.md
git commit -m "docs: update notice file"
git push origin docs/update-notice
git add docs/notice.md
git commit -m "resolve modify/delete conflict by keeping notice file"
git push origin docs/update-notice

### 배운 점
같은 파일에 대해 한쪽은 삭제하고 다른 쪽은 수정하면 
Git이 자동으로 판단할 수 없어서 사람이 파일을 유지할지 삭제할지 결정해야 한다.