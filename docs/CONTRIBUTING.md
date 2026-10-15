# 기여 가이드

## 브랜치 전략 (GitHub Flow)

- `main`: 항상 병합 가능한 상태로 유지하며, 직접 작업하거나 푸시하지 않습니다.
- `feature/*`: Issue별 작업 브랜치로 사용합니다. 최신 `main`에서 분기하고, 작업이 끝나면 PR을 통해 `main`에 병합합니다.
- PR은 다른 팀원 1명 이상의 승인을 받은 뒤 병합합니다.

### 브랜치 네이밍 규칙

Issue 하나마다 최신 `main`에서 브랜치를 하나 만듭니다. 이름은 `feature/<github-id>-<task>` 형식을 사용합니다.

- `<github-id>`: 작업자의 GitHub 사용자 이름을 소문자로 적습니다.
- `<task>`: 작업 내용을 소문자 영문, 숫자, 하이픈으로 짧게 적습니다. 공백과 한글은 사용하지 않습니다.
- 하나의 브랜치에서는 해당 Issue의 작업만 진행합니다. 완료 후 PR을 병합하면 브랜치를 삭제합니다.

예: `feature/book732-team-intro`, `feature/book732-github-flow-guide`

### 이 방식을 선택한 이유

네 명이 동시에 작업하므로 작업별 브랜치를 분리해 `main`을 안정적으로 유지할 수 있습니다. PR에서 변경 내용을 검토하고 승인한 뒤 병합하면 각 작업의 담당자와 수정 과정을 추적할 수 있습니다.

### 커밋 메시지 컨벤션

첫 줄은 `<type>: <summary>` 형식으로 작성합니다. `<summary>`는 변경한 내용을 영어 명령형으로 간결하게 적고, 마침표는 붙이지 않습니다.

| type | 사용 시점 | 예시 |
| --- | --- | --- |
| `feat` | 기능 추가 | `feat: add team profile index` |
| `fix` | 오류 수정 | `fix: correct broken profile link` |
| `docs` | 문서 작성·수정 | `docs: add commit message convention` |
| `chore` | 설정·정리 작업 | `chore: update gitignore` |

한 커밋에는 한 가지 목적의 변경만 담습니다. 관련 Issue는 PR 설명에 `Closes #이슈번호`로 연결합니다.
