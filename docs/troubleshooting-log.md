# Git 트러블슈팅 기록

팀 전체가 아래 **4종을 모두 실습**하고, **각 팀원은 최소 1개 시나리오의 기록 작성에 참여**합니다. 현재 `reset --soft`, `revert`, `stash / stash pop` 3종의 실습 기록이 있으며, `amend`는 아직 미실습입니다. 아래 양식은 추가 실습을 위한 형식입니다.
팀 전체가 아래 **4종을 모두 실습**하고, **각 팀원은 최소 1개 시나리오의 기록 작성에 참여**합니다. `stash` / `stash pop` 1건을 실습했고, 나머지 3종은 아직 미실습입니다. 양식 작성만으로는 실습 완료가 아닙니다.

개인 `feature/*` 브랜치에서 진행합니다. 공유 브랜치의 기록을 다시 쓰거나 팀 합의 없이 강제 푸시·리베이스하지 않습니다.

## 실습 현황과 주의점

| 시나리오 | 실습 내용과 주의점 | 참여자(작성·실습·검토) | 기록·증빙 | 상태 |
| --- | --- | --- | --- | --- |
| `git commit --amend` | 최근 커밋 메시지 수정. **아직 push하지 않은 본인의 개인 브랜치 커밋에만** 사용합니다. | 미기록 | 미기록 | 미실습 |
| `git reset --soft HEAD~1` | 최근 로컬 커밋 1개 취소, 변경은 스테이징 상태로 유지. **아직 push하지 않은 본인의 개인 브랜치 커밋에만** 사용합니다. | yujinchoe (작성·실습) | [Issue #23](https://github.com/book732/Codyssey_2-2/issues/23), PR 리뷰에서 추가 | 실습 완료·리뷰 대기 |
| `git revert 커밋해시` | 원격에 push된 실습 커밋의 변경을 취소하는 **새 커밋**을 만듭니다. 개인 `feature/*`에서 진행하고 PR로 반영합니다. | 나현준(vivleon): 실습·기록 | [PR #27](https://github.com/book732/Codyssey_2-2/pull/27) | 실습 완료·PR 검토 대기 |
| `git stash` / `git stash pop` | 커밋하지 않은 작업을 보관하고 다른 브랜치로 전환한 뒤, 원래 브랜치로 돌아와 복원합니다. `pop`할 때 충돌할 수 있습니다. | 정근혁(book732): 실습·기록 | [PR #28](https://github.com/book732/Codyssey_2-2/pull/28) | 실습 완료·PR 검토 대기 |
| `git reset --soft HEAD~1` | 최근 로컬 커밋 1개 취소, 변경은 스테이징 상태로 유지. **아직 push하지 않은 본인의 개인 브랜치 커밋에만** 사용합니다. | 미기록 | 미기록 | 미실습 |
| `git revert 커밋해시` | 원격에 push된 실습 커밋의 변경을 취소하는 **새 커밋**을 만듭니다. 개인 `feature/*`에서 진행하고 PR로 반영합니다. | 미기록 | 미기록 | 미실습 |
| `git stash` / `git stash pop` | 커밋하지 않은 작업을 보관하고 다른 브랜치로 전환한 뒤, 원래 브랜치로 돌아와 복원합니다. `pop`할 때 충돌할 수 있습니다. | 정근혁(book732): 실습·기록; 검토: PR 리뷰 대기 | [실제 기록](#stash-practice-book732), [Issue #25](https://github.com/book732/Codyssey_2-2/issues/25), [PR #28](https://github.com/book732/Codyssey_2-2/pull/28) | 실습·기록 완료, PR 검토 대기 |

- `revert`의 `커밋해시`는 실제 취소할 실습 커밋으로 바꿉니다. 팀원의 커밋을 임의로 취소하지 않습니다.
- 기본 `stash`는 새로 만든 미추적 파일을 보관하지 않습니다. 필요하면 `git stash -u`를 사용하고, 전후에 `git status`로 확인합니다.
- `stash pop`이 충돌하면 보관한 항목이 남을 수 있으므로 `git stash list`를 확인하고 팀원과 해결합니다.

## 시나리오: git reset --soft HEAD~1

- 날짜: 2026-10-15
- 참여자: 작성·실습 yujinchoe, 검토 PR 리뷰어 추가 예정
- 브랜치와 파일: `feature/yujinchoe-soft-reset-log`, `src/practice.txt`

### 상황과 재현 방법

원격에 push하지 않은 개인 브랜치에서 최근 커밋을 취소하되, 해당 커밋의 변경 내용은 유지해야 하는 상황을 재현했다. 실습용 변경은 `src/practice.txt`에 한 줄을 추가하는 방식으로 만들었다.

### 시도한 명령과 결과

```text
$ git add src/practice.txt
$ git commit -m "chore: prepare soft reset practice"
[feature/yujinchoe-soft-reset-log 8288e77] chore: prepare soft reset practice

$ git log -2 --oneline
8288e77 chore: prepare soft reset practice
9ed1718 Merge pull request #22 from book732/feature/yujinchoe-status-links

$ git reset --soft HEAD~1

$ git log -1 --oneline
9ed1718 Merge pull request #22 from book732/feature/yujinchoe-status-links

$ git status --short
M  src/practice.txt
```

- 해결 결과: `8288e77` 커밋은 현재 브랜치의 커밋 기록에서 제거됐고, 커밋에 포함했던 `src/practice.txt` 변경은 staged 상태로 유지됐다.
- 확인 방법과 결과: `git diff --cached -- src/practice.txt`로 변경 내용이 staged 상태임을 확인했다. 확인 후 `git restore --staged src/practice.txt`와 파일 원상복구로 임시 실습 변경을 제거했다.
- 관련 Issue·PR·커밋 또는 출력 증빙: [Issue #23](https://github.com/book732/Codyssey_2-2/issues/23), 실습용 커밋 `8288e77`(원격 push하지 않음)

### 이 방법을 선택한 이유와 주의점

- 선택 이유: 아직 원격에 push하지 않은 개인 브랜치의 최근 커밋만 취소하면서 변경 내용은 다시 다듬거나 새 커밋으로 만들 수 있기 때문이다.
- 협업에 미치는 영향과 주의점: reset은 로컬 커밋 포인터를 이동하므로 이미 공유한 커밋에는 사용하지 않는다. 원격에 push된 커밋을 취소해야 한다면 `git revert`로 새 커밋을 만든다.

실습할 때마다 아래 양식을 복사하고, 위 표에 참여자 이름과 실제 기록·증빙 링크를 채웁니다. 괄호 안 안내는 실제 증빙이 아니며, 각자의 역할이 이름과 함께 보여야 합니다.

<a id="stash-practice-book732"></a>

## 실제 실습: `git stash` / `git stash pop`

- 날짜: 2026-10-15
- 참여자: 정근혁(book732) — 실습·기록; 검토는 PR에서 진행 예정
- 브랜치와 파일: `feature/book732-stash-practice`, `src/practice.txt`
- 관련 Issue: [#25](https://github.com/book732/Codyssey_2-2/issues/25)
- 관련 PR: [#28](https://github.com/book732/Codyssey_2-2/pull/28)

### 상황과 실행 순서

최신 `main`에서 실습 브랜치를 만들고, 추적 중인 `src/practice.txt`에 `stash 실습: 정근혁의 임시 작업을 보관 후 복원` 한 줄을 추가했습니다. 이 변경은 커밋하거나 push하지 않은 상태였습니다. 기존 미추적 파일 `.gitignore`와 `2-2.pdf`는 건드리지 않았습니다.

```text
git switch -c feature/book732-stash-practice
git status --short
git stash
git stash list -1
git switch main
git switch feature/book732-stash-practice
git stash pop
git status --short
git stash list
```

### 실제 결과와 확인

- 보관 전 `git status --short`: ` M src/practice.txt`, `?? .gitignore`, `?? 2-2.pdf`.
- `git stash`: `Saved working directory and index state WIP on feature/book732-stash-practice: 9ed1718 ...`가 출력됐습니다. 수정한 줄은 작업 파일에서 사라졌고 `git stash list -1`에 `stash@{0}`이 표시됐습니다.
- `main`으로 전환한 다음 실습 브랜치로 돌아왔습니다.
- `git stash pop`: `modified: src/practice.txt`와 `Dropped refs/stash@{0} (235418d8e4bc71389ca33e1a4a00f7b32eaa744f)`가 출력됐습니다.
- 복원 후 `git diff -- src/practice.txt`에 추가한 한 줄이 다시 나타났고 `git stash list`는 비어 있었습니다. 두 미추적 파일은 그대로 남았습니다.

커밋 전 임시 변경을 보관하면 브랜치를 전환한 뒤 원래 작업을 이어갈 수 있습니다. 기본 `git stash`는 미추적 파일을 보관하지 않으므로 전후에 `git status`를 확인해야 합니다. 이 실습에서는 충돌이 발생하지 않았습니다.

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
