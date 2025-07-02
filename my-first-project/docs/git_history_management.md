# GitHub 연계 이력관리 가이드

이 문서는 `my-first-project/cursor_test.txt` 파일을 GitHub와 연계하여 이력(버전) 관리하는 방법과, 이전 버전 조회 및 복원 절차를 정리한 문서입니다.

---

## 1. 파일 이력 관리 기본 절차

1. **파일 생성 또는 수정**
   - 예시: `my-first-project/cursor_test.txt` 파일을 새로 만들거나 수정합니다.

2. **변경사항 확인**
   ```bash
   git status
   ```

3. **파일을 스테이징(add)**
   ```bash
   git add my-first-project/cursor_test.txt
   ```

4. **커밋**
   ```bash
   git commit -m "Add or update cursor_test.txt"
   ```

5. **GitHub로 푸시**
   ```bash
   git push
   ```

6. **GitHub에서 이력 확인**
   - GitHub 저장소 웹사이트에서 해당 파일을 클릭 후, History(이력) 탭에서 변경 내역을 확인할 수 있습니다.

---

## 2. 파일의 이전 버전 조회 및 복원

### 2.1. 커밋 이력 확인
```bash
git log --oneline my-first-project/cursor_test.txt
386875c (HEAD -> main, origin/main) 이력 테스트
f357f97 Add my-first-project files as normal folder

```
- 원하는 커밋 해시를 확인합니다.

### 2.2. 이전 버전 내용 조회
```bash
git show <커밋해시>:my-first-project/cursor_test.txt
```
- 해당 커밋 시점의 파일 내용을 터미널에서 확인할 수 있습니다.

### 2.3. 특정 버전으로 파일 복원(다운로드)
```bash
git checkout <커밋해시> -- my-first-project/cursor_test.txt
git checkout f357f97 -- my-first-project/cursor_test.txt
```
- 해당 커밋 시점의 파일을 로컬에 복원합니다.

### 2.4. 복원 후 커밋/푸시(선택)
```bash
git add my-first-project/cursor_test.txt
git commit -m "Restore cursor_test.txt to previous version"
git push
```

---

## 3. 전체 절차 다이어그램

```mermaid
flowchart TD
    A[파일 생성/수정/삭제] --> B[git add my-first-project/cursor_test.txt]
    B --> C[git commit -m "메시지"]
    C --> D[git push]
    D --> E[GitHub에서 이력 확인]
    E --> F[git log --oneline my-first-project/cursor_test.txt]
    F --> G[git show <해시>:my-first-project/cursor_test.txt]
    F --> H[git checkout <해시> -- my-first-project/cursor_test.txt]
    H --> I[필요시 add/commit/push]
```

---

## 4. 참고 사항
- 여러 파일을 한 번에 관리하려면 `git add .`로 전체 변경사항을 스테이징할 수 있습니다.
- 커밋 메시지는 변경 내용을 명확히 남기는 것이 좋습니다.
- 복원은 현재 작업 디렉토리에 바로 반영되므로, 기존 파일이 덮어써집니다. 필요하다면 복원 전에 백업해두세요. 