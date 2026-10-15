# 충돌 해결 기록

팀 전체에서 충돌을 **2회 이상** 해결하고, 그중 **1회 이상은 비자명 충돌**로 기록합니다. 현재 실제 충돌 해결 1건을 기록했으며, 두 번째 기록은 미실습 상태입니다. 양식 작성만으로 실습 완료가 되지는 않습니다.

- 비자명 충돌 예: 같은 파일의 같은 부분(같은 hunk 또는 인접한 줄)을 서로 다르게 수정하기, 한쪽은 파일 이름 변경·이동·삭제하고 다른 쪽은 내용 수정하기.
- 실습할 파일 예: [`src/practice.txt`](../src/practice.txt). 개인 `feature/*` 브랜치에서 팀원과 합의한 뒤 진행합니다.
- 충돌이 나면 상대 팀원에게 알리고, 두 변경의 목적을 확인한 뒤 함께 해결합니다. 해결 후 실제 내용을 아래 양식에 기록합니다.

## 기록 현황

| 기록 | 충돌 종류 | 참여자 | 실제 PR·커밋 링크 | 상태 |
| --- | --- | --- | --- | --- |
| [1](#conflict-1) | 비자명: 같은 표의 인접한 줄 수정 | 변경: book732·vivleon / 해결: vivleon | [PR #15](https://github.com/book732/Codyssey_2-2/pull/15), [PR #18](https://github.com/book732/Codyssey_2-2/pull/18) | 충돌 해결 |
| 2 | 미정 | 미기록 | 미기록 | 미실습 |

실습 후 아래 양식을 복사해 기록하고 현황표를 갱신합니다. 괄호 안 안내와 예시 마커는 실제 증빙이 아니므로, 실제 결과로 바꿉니다.

<a id="conflict-1"></a>

## 실제 충돌 기록 #1: 제출 인덱스 표

- 날짜: 2026-10-15
- 변경 작성자: 정근혁(book732, PR #15), 나현준(vivleon, PR #18)
- 충돌 해결: 나현준(vivleon)
- 브랜치·파일: `feature/book732-turkey-experience`와 `main`의 `SUBMISSION.md`
- 종류: 비자명 충돌. 같은 표의 인접한 세 줄을 서로 다른 브랜치에서 수정했습니다.

### 상황과 재현

PR #15는 book732 행에 Issue #14·PR #15를 추가했고, PR #18은 vivleon·Eunseo-415 행을 갱신했습니다. PR #18이 먼저 main에 병합되자 인접한 변경이 충돌했습니다.

- 공통 기준 커밋: `de929ea87a3c08cd7c53d6dba1ea608d5282c799`
- 당시 PR #15 커밋: `b13e27ff7f046dfd6c48410e79fd80cfc2a6df35`
- 당시 main 커밋: `6c8f8ee3f889e773bda955e923903a551bfa64d8`
- 실제 사용한 명령: PR 브랜치에서 `git merge --no-commit --no-ff origin/main`
- 실제 결과: `CONFLICT (content): Merge conflict in SUBMISSION.md`

같은 상황을 재현하려면 별도 복제본에서 위 두 커밋을 사용합니다. 아래는 재현용 절차입니다.

```bash
git switch -c reproduce-pr15 b13e27ff7f046dfd6c48410e79fd80cfc2a6df35
git merge --no-commit --no-ff 6c8f8ee3f889e773bda955e923903a551bfa64d8
```

### 실제 충돌 내용

> ```text
> <<<<<<< HEAD
> | book732 | [#1](https://github.com/book732/Codyssey_2-2/issues/1), [#3](https://github.com/book732/Codyssey_2-2/issues/3), [#6](https://github.com/book732/Codyssey_2-2/issues/6), [#14](https://github.com/book732/Codyssey_2-2/issues/14) | [#2](https://github.com/book732/Codyssey_2-2/pull/2), [#4](https://github.com/book732/Codyssey_2-2/pull/4), [#7](https://github.com/book732/Codyssey_2-2/pull/7), [#15](https://github.com/book732/Codyssey_2-2/pull/15) |
> | vivleon | [#8](https://github.com/book732/Codyssey_2-2/issues/8), [#10](https://github.com/book732/Codyssey_2-2/issues/10) | [#9](https://github.com/book732/Codyssey_2-2/pull/9), [#12](https://github.com/book732/Codyssey_2-2/pull/12) |
> | Eunseo-415 | 본인이 링크 추가 | 본인이 링크 추가 |
> =======
> | book732 | [#1](https://github.com/book732/Codyssey_2-2/issues/1), [#3](https://github.com/book732/Codyssey_2-2/issues/3), [#6](https://github.com/book732/Codyssey_2-2/issues/6) | [#2](https://github.com/book732/Codyssey_2-2/pull/2), [#4](https://github.com/book732/Codyssey_2-2/pull/4), [#7](https://github.com/book732/Codyssey_2-2/pull/7) |
> | vivleon | [#8](https://github.com/book732/Codyssey_2-2/issues/8), [#10](https://github.com/book732/Codyssey_2-2/issues/10), [#17](https://github.com/book732/Codyssey_2-2/issues/17) | [#9](https://github.com/book732/Codyssey_2-2/pull/9), [#12](https://github.com/book732/Codyssey_2-2/pull/12), [#18](https://github.com/book732/Codyssey_2-2/pull/18) |
> | Eunseo-415 | [#11](https://github.com/book732/Codyssey_2-2/issues/11) | [#13](https://github.com/book732/Codyssey_2-2/pull/13) |
> >>>>>>> origin/main
> ```

### 해결 방법과 결과

- 한쪽 표 전체를 선택하지 않고 행별로 합쳤습니다. book732 행은 PR #15의 Issue #14·PR #15를 유지하고, 나머지 행은 최신 main의 링크를 보존했습니다.
- vivleon의 Issue #17·PR #18, Eunseo-415의 Issue #11·PR #13과 소개 링크를 함께 유지했습니다.
- 소개 본문이 PR #15의 원문과 같은지 확인했고, 다른 팀원 행과 상대 링크 28개를 검증했습니다. `git diff --cached --check`가 통과했고, 미해결 파일도 남아 있지 않았습니다. 최종 반영은 이 PR의 병합 상태에서 확인할 수 있습니다.
- 관련 PR: [소개 변경 #15](https://github.com/book732/Codyssey_2-2/pull/15), [공통 문서 변경 #18](https://github.com/book732/Codyssey_2-2/pull/18)
- 배운 점: 서로 다른 팀원 행도 인접해 있으면 충돌할 수 있습니다. 공유 문서를 수정하기 전에 최신 main을 확인하고, 충돌 시 양쪽 링크를 행별로 비교합니다.

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
