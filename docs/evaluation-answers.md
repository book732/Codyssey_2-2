# Git 협업 평가 질문과 답변

팀원이 함께 보는 평가 준비 자료입니다. 질문 아래 답변을 읽고, 필요한 경우 **확인 근거** 링크에서 실제 작업 기록을 보면 됩니다.

> **확인 기준:** 2026-10-15, PR #35 병합 직후의 `main` [f5349b2](https://github.com/book732/Codyssey_2-2/commit/f5349b2fb642abc004df0604cbb56889681c1805). 이후 생긴 Issue·PR·리뷰는 아래 개수에 포함하지 않습니다.

과제 평가 항목 1부터 항목 4까지 질문 22개에 답변했습니다. 항목 1은 실제 GitHub 기록, 항목 2와 3은 협업 규칙과 실습 사례, 항목 4는 가정 상황에 대한 대응입니다. 필수 실습과 개인별 최소 개수는 충족했지만, PR #35의 이슈 연결·본문 작성과 일부 PR의 상호작용, 제출 인덱스 최신화는 남아 있습니다.

## 목차

- [항목 1. 결과물과 협업 기록 확인](#section-1)
- [항목 2. 협업 방식 설명](#section-2)
- [항목 3. Git 협업 원리](#section-3)
- [항목 4. 가정 상황에 대한 대응](#section-4)
- [항목 5. 보너스 수행 여부](#section-5)
- [제출 전 확인할 현재 항목](#remaining)

<a id="section-1"></a>

## 항목 1 결과물과 협업 기록 확인

### 1-1. (옵션 A/B) 저장소가 팀 단위로 1개이며, 팀원이 협업 가능한 권한으로 참여했는가?

**답변:** 네. 옵션 B인 개인 저장소에 Collaborator를 초대하는 방식을 사용했습니다. book732 소유의 Codyssey_2-2 저장소 하나에서 정근혁·나현준·이은서·최유진 네 명이 작업했습니다. 팀장은 관리자 권한, 나머지 세 명은 쓰기 권한을 갖고 있습니다.

**확인 근거:** [팀 저장소](https://github.com/book732/Codyssey_2-2) · [팀 소개 파일 4개](https://github.com/book732/Codyssey_2-2/tree/f5349b2fb642abc004df0604cbb56889681c1805/team)

### 1-2. main 브랜치에 Branch Protection이 설정되어 있고, 직접 push 없이 PR로만 병합되었는가?

**답변:** 네. main에 적용된 ruleset으로 PR 병합과 최소 1명 승인을 요구하고, 미해결 리뷰 스레드·강제 push·브랜치 삭제도 제한했습니다. 현재 main의 첫 부모 기록은 초기 커밋 1개와 PR 병합 16개로 구성되어, 초기화 이후 main에 직접 작업한 커밋은 보이지 않습니다.

**확인 근거:** [main 보호 규칙](https://github.com/book732/Codyssey_2-2/rules/25139963) · [Git 히스토리 증빙](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/evidence/git-log.txt)

### 1-3. 각 PR이 이슈와 연동되어 있으며(예: Closes #n), 추적 가능한가?

**답변:** 현재는 한 건을 보완해야 합니다. 병합 PR 16개 중 15개는 실제 Issue와 연결되지만, 추가 병합된 PR #35에는 ‘Closes #이슈번호’가 그대로 남아 있습니다. 이 PR의 실제 작업 Issue를 연결하고 Why·How 등 본문도 채워야 전체 충족으로 답할 수 있습니다.

**확인 근거:** [PR #34 문서 정리](https://github.com/book732/Codyssey_2-2/pull/34) · [PR #35 현재 확인할 항목](https://github.com/book732/Codyssey_2-2/pull/35)

### 1-4. 팀원별로 PR 2개 이상이 병합되어 있고, 팀원별 PR 링크를 SUBMISSION.md에서 확인할 수 있는가?

**답변:** 개수 기준은 충족했고, 제출 인덱스의 최신화는 필요합니다. 전원 최소 2개 이상 병합했고 인덱스에 각자의 PR 링크가 있습니다. 현재 GitHub에서 확인한 병합 개수는 아래와 같습니다. 인덱스에는 PR #34·#35 병합과 최신 답변이 아직 모두 반영되지 않아 표기 갱신이 필요합니다.

| 팀원 | 병합 PR | 실질 리뷰 |
| --- | ---: | ---: |
| 정근혁 (book732) | 4 | 3 |
| 나현준 (vivleon) | 6 | 6 |
| 이은서 (Eunseo-415) | 2 | 2 |
| 최유진 (yujinchoe) | 4 | 2 |

리뷰는 다른 사람의 서로 다른 PR 기준입니다. 단순 승인과 같은 PR의 중복 승인은 제외했습니다.

**확인 근거:** [SUBMISSION.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/SUBMISSION.md) · [PR #34 문서 정리](https://github.com/book732/Codyssey_2-2/pull/34) · [PR #35 현재 확인할 항목](https://github.com/book732/Codyssey_2-2/pull/35)

### 1-5. 팀원별로 리뷰 2개 이상이 존재하고, 각 팀원이 최소 1회는 본인 PR에서 리뷰를 반영했는가?

**답변:** 네. 본인 PR을 제외한 실질 리뷰가 전원 2개 이상이며, 같은 PR의 코멘트와 승인은 하나로 셌습니다. 리뷰 반영은 수정 또는 답글을 인정하는 과제 기준으로 전원 확인됩니다. 정근혁은 PR #4 수정, 나현준은 PR #9 등의 답변, 이은서는 PR #13 본문 보완·답변, 최유진은 PR #22 링크 수정·답변이 근거입니다. 답글 증빙을 직접 코드 수정으로 표현하지는 않습니다.

**확인 근거:** [PR #4 리뷰 반영 커밋](https://github.com/book732/Codyssey_2-2/commit/2a692af990676f9280449162831a3d384e7fc1bd) · [PR #9 답변](https://github.com/book732/Codyssey_2-2/pull/9#issuecomment-6186126422) · [PR #13 답변과 본문 보완](https://github.com/book732/Codyssey_2-2/pull/13#issuecomment-6188331630) · [PR #22 답변과 링크 반영](https://github.com/book732/Codyssey_2-2/pull/22#issuecomment-6187274792)

### 1-6. 충돌 해결 기록이 최소 2회 존재하며, 그중 1회는 비자명 충돌 기준을 충족하는가?

**답변:** 네. 제출 인덱스의 인접한 팀원 행이 충돌한 사례와, README의 같은 소개 영역을 목록·표로 다르게 바꾸어 충돌한 사례가 있습니다. 두 사례 모두 같은 hunk 또는 인접한 줄이 겹쳐 비자명 충돌 기준에 해당합니다. 두 번째 소개 PR #16은 닫혔지만 충돌 해결 커밋과 기록 PR #20은 남아 있습니다.

**확인 근거:** [충돌 해결 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/conflict-resolution.md)

### 1-7. 트러블슈팅 4종(amend/reset/revert/stash)이 모두 수행되었고, 팀원별로 최소 1개 시나리오 기록에 참여했는가?

**답변:** 네. 이은서는 amend, 최유진은 reset --soft, 나현준은 원격에 push한 커밋의 revert, 정근혁은 stash와 stash pop을 실습하고 기록했습니다. 네 기록에 참여자·역할·실제 명령·결과·주의점이 있으며, PR #30·#26·#27·#28로 각각 병합됐습니다.

**확인 근거:** [트러블슈팅 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/troubleshooting-log.md) · [PR #27 원격 커밋 취소 실습](https://github.com/book732/Codyssey_2-2/pull/27) · [PR #30 amend 실습](https://github.com/book732/Codyssey_2-2/pull/30)

### 1-8. docs/CONTRIBUTING.md, docs/conflict-resolution.md, docs/troubleshooting-log.md가 존재하고 템플릿 수준의 구조를 갖추었는가?

**답변:** 네. CONTRIBUTING에는 협업 규칙, conflict-resolution에는 상황·충돌 내용·해결 과정·결과·배운 점, troubleshooting-log에는 상황·명령·결과·선택 이유·주의점이 있습니다. 충돌·트러블슈팅 문서에는 실제 기록과 추가 기록용 양식이 함께 있습니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md) · [충돌 해결 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/conflict-resolution.md) · [트러블슈팅 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/troubleshooting-log.md)

<a id="section-2"></a>

## 항목 2 협업 방식을 설명하는 답변

### 2-1. 브랜치 전략을 ‘작업 단위’로 나누는 기준을 어떻게 정했는지 설명할 수 있는가?

**답변:** Issue 하나에 하나의 목표를 두고, 그 목표를 처리하는 브랜치 하나를 만들도록 정했습니다. 예를 들어 자기소개 추가, revert 실습, 공통 문서 정리는 각각 다른 작업입니다. 최신 main에서 `feature/<github-id>-<task>`로 분기하면 수정 목적과 담당자를 구분하기 쉽습니다. 브랜치는 특정 커밋을 가리키는 이름이며 커밋이 추가되면 그 위치도 이동합니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md)

### 2-2. PR 본문에 What/Why/How와 이슈 연동 정보를 일관되게 남기기 위해 어떤 규칙·도구(템플릿 등)를 썼는지 설명할 수 있는가?

**답변:** PR 양식에 연결 Issue, 변경 사항 What, 변경 이유 Why, 확인 방법과 결과 How를 넣었습니다. 개인 작업은 Closes #실제번호로 연결하고, 여러 명이 쓰는 공동 Issue는 Refs로 참조하도록 정했습니다. 관련 문서 갱신 여부와 실제 수행 기록 확인 항목도 체크하도록 했습니다. PR #35처럼 양식이 비어 있으면 제출 전에 채워야 합니다.

**확인 근거:** [PR 작성 양식](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/.github/PULL_REQUEST_TEMPLATE.md) · [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md) · [PR #35 현재 확인할 항목](https://github.com/book732/Codyssey_2-2/pull/35)

### 2-3. 리뷰 코멘트가 ‘LGTM’에 그치지 않도록 팀에서 적용한 최소 품질 기준과 운영 방법을 설명할 수 있는가?

**답변:** 파일·줄·확인 결과를 근거로 질문이나 개선 의견을 하나 이상 남기도록 했습니다. 예를 들어 ‘현황표는 실습 완료인데 위 설명은 미실습이라 상태를 맞춰 주세요’처럼 확인한 대상을 적습니다. 작성자는 실제로 확인하거나 수정한 내용을 답변하고, 다른 팀원 1명 이상의 승인을 받은 뒤 병합하는 규칙입니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md) · [PR #26 상태 문구 검토](https://github.com/book732/Codyssey_2-2/pull/26#pullrequestreview-5530004211)

### 2-4. 충돌 발생 시, 팀이 어떤 흐름(공유→해결→기록)으로 대응했는지 설명할 수 있는가?

**답변:** 충돌한 브랜치와 파일을 공유하고, 양쪽 변경의 목적을 확인한 뒤 내용을 합치는 흐름으로 정했습니다. 해결 후에는 충돌 마커·파일 내용·링크를 확인해 커밋하고 충돌 문서에 기록합니다. 실제 README 충돌에서는 최신 표 형식을 유지하면서 팀원 소개 링크도 살렸습니다. 해결이 어려우면 팀장에게 도움을 요청하도록 했습니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md) · [충돌 해결 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/conflict-resolution.md)

### 2-5. 트러블슈팅 로그를 ‘재현 가능’하게 만들기 위해 어떤 항목(상황/절차/결과/주의점)을 고정했는지 설명할 수 있는가?

**답변:** 날짜와 참여자, 브랜치·파일, 시작 상태, 실행한 명령과 출력, 해결 결과, 확인 방법, 선택 이유와 주의점을 적도록 했습니다. 특히 push 전인지 후인지와 커밋 해시를 남겨 같은 상황을 구분할 수 있게 했습니다. 예를 들어 revert는 원격 push 확인 값과 취소 전후 비교 결과까지 기록했습니다.

**확인 근거:** [트러블슈팅 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/troubleshooting-log.md) · [revert 명령과 실제 출력](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/evidence/revert-vivleon.txt)

<a id="section-3"></a>

## 항목 3 Git 협업 원리를 설명하는 답변

### 3-1. GitHub Flow에서 main을 ‘항상 배포 가능 상태’로 유지해야 하는 이유를 설명할 수 있는가?

**답변:** main은 팀원들이 새 작업을 시작하고 최종 결과를 확인하는 기준이기 때문입니다. 확인되지 않은 변경이 들어가면 다른 사람의 작업도 불안정한 상태에서 시작됩니다. 이 프로젝트에서는 배포 가능 상태를 ‘소개 파일과 링크, 문서가 깨지지 않고 제출 가능한 상태’로 이해했습니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md)

### 3-2. main에 직접 push하지 않고 PR과 승인으로 병합하는 이유(품질/책임/추적성)를 설명할 수 있는가?

**답변:** 다른 사람이 변경 내용을 확인하면 빠진 링크나 잘못된 기록을 발견할 수 있습니다. PR에는 작성자·검토자·수정 이유가 남아 누가 어떤 판단을 했는지도 확인할 수 있습니다. 문제가 생겼을 때 관련 Issue와 커밋까지 따라갈 수 있어, 실수를 찾고 되돌리기에도 좋습니다.

**확인 근거:** [main 보호 규칙](https://github.com/book732/Codyssey_2-2/rules/25139963) · [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md)

### 3-3. 이슈와 PR을 연동하는 이유(추적성/커뮤니케이션/자동화)를 설명할 수 있는가?

**답변:** Issue에는 해야 할 일과 이유를, PR에는 실제 변경과 검증 결과를 남깁니다. 둘을 연결하면 작업 요청부터 수정 결과까지 한 흐름으로 볼 수 있고 팀원도 진행 상황을 이해하기 쉽습니다. Closes #번호를 올바르게 연결하면 기본 브랜치에 병합할 때 해당 Issue를 자동으로 닫을 수 있습니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md) · [PR #34 문서 정리](https://github.com/book732/Codyssey_2-2/pull/34)

### 3-4. 원격에 push된 커밋을 되돌릴 때 reset 대신 revert를 선택해야 하는 이유를 설명할 수 있는가?

**답변:** reset은 로컬 브랜치가 가리키는 커밋 위치를 옮깁니다. 이를 원격 기록에도 반영하려고 강제 push하면 다른 팀원이 가진 기록과 달라질 수 있습니다. revert는 원래 커밋을 남기고 변경을 취소하는 새 커밋을 만들어 강제 push 없이 공유할 수 있습니다. 나현준(vivleon)의 실습에서도 원격의 3449502를 확인한 뒤 취소 커밋 6690b3b를 만들어 두 기록을 모두 남겼습니다.

**확인 근거:** [PR #27 원격 커밋 취소 실습](https://github.com/book732/Codyssey_2-2/pull/27) · [revert 명령과 실제 출력](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/evidence/revert-vivleon.txt)

### 3-5. 충돌 마커(`<<<<<<<`, `=======`, `>>>>>>>`)의 의미와 비자명 충돌을 해결할 때 고려한 의사결정 기준을 설명할 수 있는가?

**답변:** 일반적인 merge에서 `<<<<<<<` 아래는 현재 브랜치 내용, `=======`는 두 내용의 구분선, `>>>>>>>` 쪽 표시는 상대 브랜치를 뜻합니다. 두 변경이 각각 필요한지, 최신 형식·올바른 링크를 지키는지 보고 합칠 내용을 결정합니다. README 충돌에서는 최신 표와 팀원 소개 링크를 모두 살렸으며, 마지막에 마커가 남지 않았는지 확인했습니다.

```text
  <<<<<<< HEAD
  현재 브랜치 내용
  =======
  합치려는 브랜치 내용
  >>>>>>> 상대 브랜치
```

**확인 근거:** [충돌 해결 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/conflict-resolution.md)

<a id="section-4"></a>

## 항목 4 가정 상황에 대한 대응

### 4-1. 만약 main에 긴급 핫픽스가 필요하다면, GitHub Flow에서 어떤 순서로 처리할지(브랜치/PR/리뷰/배포) 설명할 수 있는가?

**답변:** 최신 main에서 feature/vivleon-hotfix-link처럼 작은 수정 브랜치를 만들겠습니다. 문제를 Issue로 남기고 필요한 부분만 수정·검증한 뒤 PR을 열어 최소 1명에게 긴급 리뷰와 승인을 받겠습니다. 팀장이 병합을 확인하면 배포하거나 제출본을 갱신하고 결과를 다시 확인하겠습니다. 이 프로젝트는 문서 결과물이므로 별도 서버 배포 대신 main의 파일과 링크를 확인합니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md) · [main 보호 규칙](https://github.com/book732/Codyssey_2-2/rules/25139963)

### 4-2. 만약 팀원이 실수로 ‘의미없는 커밋 메시지’를 여러 개 push했다면, 협업 중단 없이 개선하는 방법을 설명할 수 있는가?

**답변:** 먼저 다른 팀원이 받은 공유 기록인지 확인하겠습니다. 이미 공유했다면 과거 커밋은 유지하고, PR 본문이나 Issue에 각 커밋이 무엇을 왜 바꿨는지 보충하겠습니다. 이후 커밋부터 구체적인 메시지를 쓰며, 메시지만 고치려고 변경 내용을 취소하는 revert를 하지는 않겠습니다. 기록 정리는 혼자 쓰는 push 전 브랜치에서 연습하고, 공유 브랜치는 합의 없이 amend·rebase·강제 push하지 않겠습니다.

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md)

### 4-3. 만약 충돌이 반복적으로 발생한다면(같은 파일/같은 영역), 원인 분석과 예방 방안을 제시할 수 있는가?

**답변:** 누가 같은 영역을 동시에 바꾸는지와 작업 브랜치가 얼마나 오래된 main을 기준으로 하는지 확인하겠습니다. 공통 문서는 수정 범위와 병합 순서를 먼저 공유하고, 작은 PR로 자주 합치겠습니다. main을 반영할 때 양쪽 문구를 전부 붙여 넣어 중복시키지 않고 현재 내용으로 정리하겠습니다. 우리 팀에서 반복된 현황표 중복도 이런 확인이 필요한 사례였습니다.

**확인 근거:** [충돌 해결 기록](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/conflict-resolution.md) · [PR #34 문서 정리](https://github.com/book732/Codyssey_2-2/pull/34)

### 4-4. (보너스 수행 시) 왜 리베이스가 히스토리를 ‘깨끗하게’ 만들지만 협업에서는 위험할 수 있는지 전후 예시를 통해 설명할 수 있는가?

**답변:** 아래는 원리 설명용 예시입니다. rebase -i의 squash로 여러 커밋을 하나로 합치면 작업 목적이 읽기 쉬워지지만, 커밋 해시가 바뀝니다. 다른 팀원이 예전 커밋을 받은 상태라면 서로 다른 기록이 생겨 중복이나 충돌을 유발할 수 있습니다. 따라서 공유 main은 다시 쓰지 않고, 혼자 쓰는 push 전 feature 브랜치에서만 선택적으로 정리하겠습니다. 이 설명은 보너스 실습 수행 증빙을 뜻하지 않습니다.

```text
정리 전   A -- B 초안 -- C 문구 수정 -- D 보완
정리 후   A -- E 완성된 작업
B C D를 합치면 새 해시의 E가 만들어짐
```

**확인 근거:** [docs/CONTRIBUTING.md](https://github.com/book732/Codyssey_2-2/blob/f5349b2fb642abc004df0604cbb56889681c1805/docs/CONTRIBUTING.md)

<a id="section-5"></a>

## 항목 5 보너스 수행 여부

제출 자료에 rebase 전후 비교나 CODEOWNERS 보너스 수행 기록이 없어 보너스 완료로 표시하지 않습니다. 항목 4의 rebase 답변은 개념 설명용입니다. 보너스 크레딧 부여 여부는 평가자가 판단하며, 선택 과제 미수행과 필수 요구사항 충족 여부는 따로 봅니다.

<a id="remaining"></a>

## 제출 전 확인할 현재 항목

1. PR #35에 실제 작업 Issue 연결과 What·Why·How를 보완합니다. 브랜치명도 팀 규칙의 예외였으므로 이후에는 `feature/<github-id>-<task>`를 사용합니다. 과거 main 기록을 다시 쓸 필요는 없습니다.
2. SUBMISSION의 PR #34·#35 병합, vivleon 병합 PR 6개, 이은서의 최신 답변·본문 보완 상태를 갱신합니다. 파일 안의 이전 점검 표기와 현재 GitHub 상태를 구분합니다.
3. PR #2·#15·#20·#28·#32 등의 작성자 상호작용과 #34·#35의 실질 리뷰 기록을 더 확인합니다. 개인별 최소 개수를 충족했다는 이유만으로 모든 PR의 품질 기준을 완료로 단정하지 않습니다.

이 문서는 평가 답변 자료입니다. [SUBMISSION.md](../SUBMISSION.md)의 이전 점검 표기와 확인 기준이 다르므로, 최종 제출 전에는 실제 GitHub 상태를 다시 확인합니다.
