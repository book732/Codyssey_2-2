# Git 트러블슈팅 기록

팀 전체가 아래 **4종을 모두 실습**하고, **각 팀원은 최소 1개 시나리오의 기록 작성에 참여**합니다. 아래 표에는 실제 수행한 실습만 완료로 표시합니다. 양식 작성은 실습 완료가 아닙니다.

개인 `feature/*` 브랜치에서 진행합니다. 공유 브랜치의 기록을 다시 쓰거나 팀 합의 없이 강제 푸시·리베이스하지 않습니다.

## 실습 현황과 주의점

| 시나리오 | 실습 내용과 주의점 | 참여자(작성·실습·검토) | 기록·증빙 | 상태 |
| --- | --- | --- | --- | --- |
| `git commit --amend` | 최근 커밋 메시지 수정. **아직 push하지 않은 본인의 개인 브랜치 커밋에만** 사용합니다. | 미기록 | 미기록 | 미실습 |
| `git reset --soft HEAD~1` | 최근 로컬 커밋 1개 취소, 변경은 스테이징 상태로 유지. **아직 push하지 않은 본인의 개인 브랜치 커밋에만** 사용합니다. | 미기록 | 미기록 | 미실습 |
| `git revert 커밋해시` | 원격에 push된 실습 커밋의 변경을 취소하는 **새 커밋**을 만듭니다. 개인 `feature/*`에서 진행하고 PR로 반영합니다. | 나현준(vivleon): 실습·기록, AI 도구 보조 | [실제 기록](#revert-vivleon), [명령·출력](evidence/revert-vivleon.txt) | 실습 완료 · PR 검토 대기 |
| `git stash` / `git stash pop` | 커밋하지 않은 작업을 보관하고 다른 브랜치로 전환한 뒤, 원래 브랜치로 돌아와 복원합니다. `pop`할 때 충돌할 수 있습니다. | 미기록 | 미기록 | 미실습 |

- `revert`의 `커밋해시`는 실제 취소할 실습 커밋으로 바꿉니다. 팀원의 커밋을 임의로 취소하지 않습니다.
- 기본 `stash`는 새로 만든 미추적 파일을 보관하지 않습니다. 필요하면 `git stash -u`를 사용하고, 전후에 `git status`로 확인합니다.
- `stash pop`이 충돌하면 보관한 항목이 남을 수 있으므로 `git stash list`를 확인하고 팀원과 해결합니다.

실습할 때마다 아래 양식을 복사하고, 위 표에 참여자 이름과 실제 기록·증빙 링크를 채웁니다. 괄호 안 안내는 실제 증빙이 아니며, 각자의 역할이 이름과 함께 보여야 합니다.

<a id="revert-vivleon"></a>

## 시나리오: 원격에 push한 커밋을 git revert로 취소

- 날짜: 2026-10-15 16:57 (한국 시간)
- 실습·기록 담당: 나현준(vivleon). 명령 실행과 기록 정리는 AI 도구의 도움을 받았습니다.
- 팀원 검토: [PR #27](https://github.com/book732/Codyssey_2-2/pull/27)에서 팀장 book732에게 요청했으며, 아직 승인받은 상태는 아닙니다.
- 브랜치: `feature/vivleon-revert-practice`
- 실습 파일: `src/revert-practice-vivleon.txt` (취소 후에는 파일이 없어집니다.)
- 연결 Issue: [#24](https://github.com/book732/Codyssey_2-2/issues/24)

### 상황과 재현 방법

원격에 이미 올린 커밋을 취소하는 상황을 연습했습니다. 다른 팀원의 파일 대신 본인의 임시 파일을 추가하고 push한 뒤, 그 커밋만 취소했습니다.

시작할 때 작업 폴더는 깨끗했으며, `origin/main`의 `9ed1718`에서 새 브랜치를 만들었습니다. 임시 파일에는 아래 두 줄을 작성했습니다.

```text
Git revert 실습용 임시 파일입니다.
원격에 push한 후 이 파일을 추가한 커밋을 취소합니다.
```

아래는 실제 수행한 명령입니다. 다시 실습할 때는 최신 `main`에서 본인용 새 브랜치와 파일을 만들고, 커밋 해시도 새로 생성된 값으로 바꿉니다. 이 기록의 해시를 그대로 취소하지 않습니다.

### 시도한 명령과 결과

```bash
git switch -c feature/vivleon-revert-practice origin/main
# 위 내용으로 임시 파일을 만든 뒤 실행
git add src/revert-practice-vivleon.txt
git commit -m 'chore: add vivleon revert practice file'
git push --set-upstream origin feature/vivleon-revert-practice

# GitHub에서 원격 브랜치의 커밋을 확인
gh api repos/book732/Codyssey_2-2/git/ref/heads/feature/vivleon-revert-practice --jq .object.sha
# 결과: 3449502195dfca605681bd02d90cd5628ce8d884

git revert --no-commit 3449502195dfca605681bd02d90cd5628ce8d884
git commit -m 'chore: revert pushed vivleon practice file' -m 'This reverts commit 3449502195dfca605681bd02d90cd5628ce8d884.'
git push origin feature/vivleon-revert-practice

gh api repos/book732/Codyssey_2-2/git/ref/heads/feature/vivleon-revert-practice --jq .object.sha
# 결과: 6690b3b83ca1e51b84ab4a6bdc7b22e4016075c8
```

`--no-commit`은 취소할 변경을 먼저 준비하는 옵션입니다. 이어서 팀 커밋 메시지 규칙에 맞는 새 커밋을 만들었습니다. 이전 커밋의 기록은 지우지 않았습니다. 위 원격 조회 결과는 실습 당시 값이며, 기록 문서 등을 push하면 브랜치의 최신 커밋은 달라집니다.

### 해결 결과와 확인

- [실습 커밋 `3449502`](https://github.com/book732/Codyssey_2-2/commit/3449502195dfca605681bd02d90cd5628ce8d884): 임시 파일 추가 후 원격 push를 확인했습니다.
- [취소 커밋 `6690b3b`](https://github.com/book732/Codyssey_2-2/commit/6690b3b83ca1e51b84ab4a6bdc7b22e4016075c8): 임시 파일을 삭제하는 새 커밋을 만들어 원격 push를 확인했습니다.
- `git diff --exit-code 3449502195dfca605681bd02d90cd5628ce8d884^ 6690b3b83ca1e51b84ab4a6bdc7b22e4016075c8`: 출력 없이 종료 코드 0. 실습 전과 취소 직후의 전체 파일 내용이 같았습니다.
- `git ls-tree --name-only HEAD src/revert-practice-vivleon.txt`: 취소 직후 출력이 없어 파일이 남지 않았음을 확인했습니다.
- `git status --porcelain=v1`: 취소 직후 출력이 없어 작업 폴더가 깨끗했습니다.
- `git log --oneline -3`: 실습 커밋과 취소 커밋이 모두 남았습니다. 실제 명령·출력은 [증빙 파일](evidence/revert-vivleon.txt)에서 확인할 수 있습니다.

### 이 방법을 선택한 이유와 주의점

이미 push한 커밋이므로 과거 기록을 바꾸는 대신, 변경을 취소하는 새 기록을 남기는 `revert`를 선택했습니다. `reset --soft`는 커밋을 되돌리면서 변경은 남길 때 쓰며, 원격에 공유한 기록을 지우기 위한 용도로 쓰지 않습니다. `stash`는 아직 커밋하지 않은 작업을 잠시 보관하는 기능이라 이번 상황과 다릅니다.

이번에는 본인이 만든 임시 파일의 커밋만 취소했습니다. 공유 `main`에 직접 push하거나 강제 push하지 않았고, 다른 팀원의 커밋도 취소하지 않았습니다. 실제 작업에서는 취소할 커밋을 먼저 확인하며, 이후 변경과 겹치면 충돌이 날 수 있으므로 내용을 확인하고 해결합니다.

## 복사해서 사용할 양식

### 시나리오: (amend / soft reset / revert / stash 중 실제 실습명)

- 날짜: (실제 실습 날짜)
- 참여자: 작성·기록 (이름), 실습 (이름), 검토 (이름)
- 브랜치와 파일: (실제 개인 브랜치 이름과 파일 경로)

#### 상황과 재현 방법

- 시작 상태: (변경 내용, 커밋 여부, 원격 push 여부)
- 재현 순서: (다른 팀원이 따라 할 수 있는 준비 과정)

#### 시도한 명령과 결과

```text
(실제로 수행한 명령과 필요한 출력)
```

- 해결 결과: (어떤 변경과 커밋이 남았는지)
- 확인 방법과 결과: (`git status`, `git log`, 파일 내용 등 실제 전후 확인)
- 관련 Issue·PR·커밋 또는 출력 증빙: (실제 링크나 파일 경로)

#### 이 방법을 선택한 이유와 주의점

- 선택 이유: (예: 이미 push한 커밋이라 기록을 지우지 않는 revert 선택)
- 협업에 미치는 영향과 주의점: (공유 기록 변경 여부, 재발 방지 방법 등)

기록 후 [`SUBMISSION.md`](../SUBMISSION.md)에 실제 기록과 증빙 링크를 연결합니다. 기본 협업 규칙은 [기여 가이드](CONTRIBUTING.md)를 따릅니다.
