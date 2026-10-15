# Codyssey 2-2

초보자 4명이 Issue, 브랜치, PR, 코드 리뷰를 통해 Git 협업을 연습하는 프로젝트입니다. 결과물은 **B: 팀 소개**입니다.

소개글을 함께 완성하고, 충돌 해결과 Git 트러블슈팅 과정을 실제로 연습해 기록합니다. `src/practice.txt`는 충돌 실습용 예시 파일입니다.

## 팀원 소개

| 이름 | GitHub | 역할 | 소개 파일 |
| --- | --- | --- | --- |
| 정근혁 | book732 | 팀장 | [소개](team/book732.md) |
| 나현준 | vivleon | 팀원 | [소개](team/vivleon.md) |
| 이은서 | Eunseo-415 | 팀원 | [소개](team/eunseo-415.md) |
| 최유진 | yujinchoe | 팀원 | [소개](team/yujinchoe.md) |

## 공통 문서

| 문서 | 확인할 내용 |
| --- | --- |
| [협업 가이드](docs/CONTRIBUTING.md) | 브랜치, 커밋, PR, 리뷰, 문서 갱신 규칙 |
| [충돌 해결 기록](docs/conflict-resolution.md) | 실제 충돌 해결 기록과 추가 실습 양식 |
| [트러블슈팅 기록](docs/troubleshooting-log.md) | Git 명령의 실제 실습 기록과 추가 실습 양식 |
| [제출물 인덱스](SUBMISSION.md) | 팀원별 Issue·PR·리뷰와 제출 증빙 링크 |
| [실습·히스토리 증빙](docs/evidence/README.md) | 실제 증빙 파일과 히스토리 갱신 방법 |
| [AI 도구 작업 안내](AGENTS.md) | AI와 작업할 때 함께 지킬 규칙 |

`team/`에는 네 명의 소개 파일, `docs/`에는 협업 문서와 실습 기록, `src/`에는 간단한 실습 파일을 둡니다.

2026-10-15 기준 팀 소개 4개, 비자명 충돌 해결 기록 2건, Git 트러블슈팅 4종이 `main`에 반영됐습니다. 실습은 [amend](docs/troubleshooting-log.md#amend), [soft reset](docs/troubleshooting-log.md#soft-reset), [revert](docs/troubleshooting-log.md#revert-vivleon), [stash / stash pop](docs/troubleshooting-log.md#stash-practice-book732)에서 확인합니다.

제출 요구사항이 모두 완료된 상태는 아닙니다. 팀원별 기여 증빙과 아직 보완할 리뷰·답변 기록은 [제출 전 점검](SUBMISSION.md#requirements-check)에 정리했습니다.

## 작업 시작과 마무리

1. 협업 가이드와 맡은 Issue를 읽고 `feature/<github-id>-<task>` 브랜치를 만듭니다.
2. 맡은 파일을 수정하고 관련 문서도 함께 확인합니다.
3. PR에 변경 사항·이유·확인 방법을 적고 다른 팀원에게 리뷰를 받습니다.
4. 리뷰를 반영하고, 본인 Issue·PR·리뷰 링크를 제출물 인덱스에 갱신합니다.

기록 양식의 빈칸은 실제 실습 후 참여자와 명령, 결과, PR·커밋 링크로 채웁니다.
