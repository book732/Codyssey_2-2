# Git 트러블슈팅 기록

팀 전체가 아래 **4종을 모두 실습**하고, **각 팀원은 최소 1개 시나리오의 기록 작성에 참여**합니다. 현재는 양식만 준비했으며, 양식 작성은 실습 완료가 아닙니다.

개인 `feature/*` 브랜치에서 진행합니다. 공유 브랜치의 기록을 다시 쓰거나 팀 합의 없이 강제 푸시·리베이스하지 않습니다.

## 실습 현황과 주의점

| 시나리오 | 실습 내용과 주의점 | 참여자(작성·실습·검토) | 기록·증빙 | 상태 |
| --- | --- | --- | --- | --- |
| `git commit --amend` | 최근 커밋 메시지 수정. **아직 push하지 않은 본인의 개인 브랜치 커밋에만** 사용합니다. | 작성·실습: 이은서 / 검토: (PR 리뷰어 이름) | [기록](#amend), [스크린샷](evidence/amend.png) | 실습함 · PR 검토 전 |
| `git reset --soft HEAD~1` | 최근 로컬 커밋 1개 취소, 변경은 스테이징 상태로 유지. **아직 push하지 않은 본인의 개인 브랜치 커밋에만** 사용합니다. | 미기록 | 미기록 | 미실습 |
| `git revert 커밋해시` | 원격에 push된 실습 커밋의 변경을 취소하는 **새 커밋**을 만듭니다. 개인 `feature/*`에서 진행하고 PR로 반영합니다. | 미기록 | 미기록 | 미실습 |
| `git stash` / `git stash pop` | 커밋하지 않은 작업을 보관하고 다른 브랜치로 전환한 뒤, 원래 브랜치로 돌아와 복원합니다. `pop`할 때 충돌할 수 있습니다. | 미기록 | 미기록 | 미실습 |

- `revert`의 `커밋해시`는 실제 취소할 실습 커밋으로 바꿉니다. 팀원의 커밋을 임의로 취소하지 않습니다.
- 기본 `stash`는 새로 만든 미추적 파일을 보관하지 않습니다. 필요하면 `git stash -u`를 사용하고, 전후에 `git status`로 확인합니다.
- `stash pop`이 충돌하면 보관한 항목이 남을 수 있으므로 `git stash list`를 확인하고 팀원과 해결합니다.

실습할 때마다 아래 양식을 복사하고, 위 표에 참여자 이름과 실제 기록·증빙 링크를 채웁니다. 괄호 안 안내는 실제 증빙이 아니며, 각자의 역할이 이름과 함께 보여야 합니다.

<a id="amend"></a>

## 실제 기록: `git commit --amend`

- 날짜: 2026-10-15
- 참여자: 작성·기록 이은서, 실습 이은서, 검토 (PR 리뷰어 이름)
- 브랜치와 파일: `feature/eunseo-415-amend-practice`, `docs/troubleshooting-log.md`

### 상황과 재현 방법

- 시작 상태: 이 기록 양식을 추가한 뒤, 커밋 메시지 컨벤션(`<type>: <summary>`)에 맞지 않는 `update` 메시지로 커밋했습니다. 아직 원격에 push하지 않은 상태입니다.
- 재현 순서:
  1. 최신 `main`에서 개인 브랜치를 만듭니다.
  2. 파일을 수정한 뒤 `git commit -m "update"`로 커밋합니다.
  3. push하기 전에 `git commit --amend -m "<올바른 메시지>"`로 메시지를 수정합니다.
- 참고: 처음에는 파일을 수정하지 않고 커밋해 `nothing to commit, working tree clean`이 출력되었고 커밋이 만들어지지 않았습니다. 변경 사항이 있어야 커밋할 수 있습니다.

### 시도한 명령과 결과

```text
$ git switch -c feature/eunseo-415-amend-practice
Switched to a new branch 'feature/eunseo-415-amend-practice'
$ git add docs/troubleshooting-log.md
$ git commit -m "update"
[feature/eunseo-415-amend-practice c912c06] update
 1 file changed, 30 insertions(+)
$ git log --oneline -1
c912c06 (HEAD -> feature/eunseo-415-amend-practice) update
$ git commit --amend -m "docs: add amend troubleshooting record"
[feature/eunseo-415-amend-practice 29a30af] docs: add amend troubleshooting record
 Date: Thu Oct 15 16:54:29 2026 +0900
 1 file changed, 30 insertions(+)
$ git log --oneline -1
29a30af (HEAD -> feature/eunseo-415-amend-practice) docs: add amend troubleshooting record
```

- 해결 결과: `update` 커밋(`c912c06`)이 `docs: add amend troubleshooting record` 커밋(`29a30af`)으로 교체되었습니다. 커밋 개수는 그대로 1개이고, 변경 내용(30줄 추가)도 같습니다.
- 확인 방법과 결과: `git log --oneline -1`로 수정 전후를 비교했습니다. 메시지가 바뀌었고 커밋 해시도 `c912c06`에서 `29a30af`로 바뀌었습니다. amend는 기존 커밋을 고치는 것이 아니라 새 커밋으로 교체한다는 것을 확인했습니다.
- 관련 Issue·PR·커밋 또는 출력 증빙: [터미널 스크린샷](evidence/amend.png), PR (생성 후 링크 추가)

### 이 방법을 선택한 이유와 주의점

- 선택 이유: 아직 push하지 않은 본인 브랜치의 최근 커밋이라 메시지만 바로잡으면 되었습니다. 새 커밋을 추가하지 않고 히스토리를 깔끔하게 유지할 수 있습니다.
- 협업에 미치는 영향과 주의점: amend는 커밋 해시를 바꾸므로 이미 push한 커밋에 사용하면 원격과 기록이 달라져 강제 푸시가 필요합니다. 다른 팀원이 그 커밋을 받았다면 기록이 꼬일 수 있으므로, push 전의 본인 커밋에만 사용하고 push한 커밋은 `git revert`로 되돌립니다.

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
