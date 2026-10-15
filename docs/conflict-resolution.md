# 충돌 해결 기록

팀 전체에서 충돌을 **2회 이상** 해결하고, 그중 **1회 이상은 비자명 충돌**로 기록합니다. 현재는 양식만 준비했으며, 양식 작성은 실습 완료가 아닙니다.

- 비자명 충돌 예: 같은 파일의 같은 부분(같은 hunk 또는 인접한 줄)을 서로 다르게 수정하기, 한쪽은 파일 이름 변경·이동·삭제하고 다른 쪽은 내용 수정하기.
- 실습할 파일 예: [`src/practice.txt`](../src/practice.txt). 개인 `feature/*` 브랜치에서 팀원과 합의한 뒤 진행합니다.
- 충돌이 나면 상대 팀원에게 알리고, 두 변경의 목적을 확인한 뒤 함께 해결합니다. 해결 후 실제 내용을 아래 양식에 기록합니다.

## 기록 현황

| 기록 | 충돌 종류 | 참여자 | 실제 PR·커밋 링크 | 상태 |
| --- | --- | --- | --- | --- |
| 1 | 비자명: 같은 README 영역을 서로 다르게 수정 | yujinchoe, vivleon | [PR #16](https://github.com/book732/Codyssey_2-2/pull/16), [해결 커밋](https://github.com/book732/Codyssey_2-2/commit/b867601) | 완료 |
| 2 | 미정 | 미기록 | 미기록 | 미실습 |

실습 후 아래 양식을 복사해 기록하고 현황표를 갱신합니다. 괄호 안 안내와 예시 마커는 실제 증빙이 아니므로, 실제 결과로 바꿉니다.

## 충돌 기록 1: README 팀원 소개 영역

- 날짜: 2026-10-15
- 참여자: 작성자 yujinchoe, 상대 작업자 vivleon
- 브랜치와 파일: `feature/yujinchoe-team-intro`와 `main`, `README.md`
- 충돌 종류: 비자명 충돌 — 같은 팀원 소개 영역을 서로 다른 형식으로 수정함

#### 상황과 재현 절차

- `feature/yujinchoe-team-intro`에서는 팀원 소개를 목록으로 유지하면서 yujinchoe 소개 링크를 추가했다.
- `main`에서는 vivleon의 공통 문서 작업으로 팀원 소개를 표 형식으로 변경하고 공통 문서 안내를 추가했다.
- PR [#16](https://github.com/book732/Codyssey_2-2/pull/16)의 충돌을 로컬에서 재현했다.

```bash
git fetch origin
git switch feature/yujinchoe-team-intro
git merge origin/main
```

#### 실제 충돌 내용

> ```text
> <<<<<<< HEAD
> - [정근혁 (book732, 팀장)](team/book732.md)
> - [나현준 (vivleon)](team/vivleon.md)
> - [최유진 (yujinchoe)](team/yujinchoe.md)
> =======
> | 이름 | GitHub | 역할 | 소개 파일 |
> | --- | --- | --- | --- |
> | 정근혁 | book732 | 팀장 | [소개](team/book732.md) |
> | 나현준 | vivleon | 팀원 | [소개](team/vivleon.md) |
> | 이은서 | Eunseo-415 | 팀원 | 작성 예정: [Issue #5](https://github.com/book732/Codyssey_2-2/issues/5) |
> | 최유진 | yujinchoe | 팀원 | 작성 예정: [Issue #5](https://github.com/book732/Codyssey_2-2/issues/5) |
> >>>>>>> origin/main
> ```

#### 해결 과정과 이유

- 최신 `main`의 표 형식과 공통 문서 안내를 유지했다.
- yujinchoe 행은 이미 생성된 소개 파일을 가리키도록 `[소개](team/yujinchoe.md)`로 수정했다.
- 충돌 마커를 제거하고 다음 명령으로 해결 내용을 커밋·푸시했다.

```bash
git add README.md
git commit -m "fix: resolve README merge conflict"
git push origin feature/yujinchoe-team-intro
```

#### 결과와 배운 점

- `README.md`에서 두 변경의 목적을 모두 보존했고 충돌 마커를 제거했다.
- `git diff --check`와 충돌 마커 검색으로 파일을 확인했으며, PR #16의 병합 가능 상태가 `MERGEABLE`로 변경됐다.
- 해결 커밋: [b867601](https://github.com/book732/Codyssey_2-2/commit/b867601)
- 같은 README 영역을 여러 작업이 수정하면 형식 변경도 충돌을 만들 수 있으므로, 작업 전에 최신 `main`을 반영하고 수정 범위를 공유해야 한다.

## 복사해서 사용할 양식

### 충돌 기록 번호: (실제 번호)

- 날짜: (실제 실습 날짜)
- 참여자: 작성자 (이름), 상대 작업자 (이름), 검토자 (이름)
- 브랜치와 파일: (충돌한 두 브랜치와 파일 경로)
- 충돌 종류: (일반 / 비자명, 비자명이면 해당하는 이유)

#### 상황과 재현 절차

- 두 사람이 각각 무엇을 바꿨는지: (실제 변경 내용)
- 충돌을 다시 확인할 수 있는 순서: (기준 커밋, 브랜치 생성·수정·병합 순서와 실제 사용 명령)

#### 실제 충돌 내용

아래는 마커의 모양만 보여 주는 양식입니다. 실제 충돌 출력으로 바꿉니다. 마커가 없는 이름 변경·삭제 충돌이면 실제 Git 메시지를 붙입니다.

`<<<<<<< HEAD` 아래는 현재 브랜치의 내용, `=======` 아래는 합치려는 브랜치의 내용입니다. `>>>>>>>`에서 상대 변경 구간이 끝납니다.

기록은 아래처럼 각 줄 앞에 `>`가 있는 인용 블록에 넣습니다. 문서의 예시가 해결되지 않은 충돌로 잘못 검사되는 것을 막습니다.

> ```text
> <<<<<<< HEAD
> (현재 브랜치의 실제 내용)
> =======
> (상대 브랜치의 실제 내용)
> >>>>>>> (실제 브랜치 이름)
> ```

#### 해결 과정과 이유

- 선택한 방법과 이유: (둘 다 반영 / 하나 선택 / 내용을 다시 정리한 이유)
- 실제 수행 순서와 명령: (마커 제거, 최종 내용 확인, 커밋 등 실제 절차)

#### 결과와 배운 점

- 검증 방법과 결과: (최종 파일 내용, 충돌 마커 제거 여부, `git status` 등 실제 확인 결과)
- 관련 Issue·PR·커밋: (실제 GitHub 링크)
- 배운 점과 주의점: (다음 작업에서 미리 상의할 내용 등)

기록 후 [`SUBMISSION.md`](../SUBMISSION.md)에 실제 기록과 증빙 링크를 연결합니다. 기본 협업 규칙은 [기여 가이드](CONTRIBUTING.md)를 따릅니다.
