# Git 실습·히스토리 증빙 안내

이 폴더에는 Git 실습의 명령·출력, 스크린샷, 히스토리와 요구사항 점검 자료를 보관합니다. 기준은 2026-10-15, `main`의 `d6f517c4634dde58021187a33a7010455c32a717`입니다. 이번 공통 문서 정리 PR 이후 최종 제출 전에는 히스토리와 진행 상태를 다시 확인합니다.

## 실습 증빙

- [이은서(Eunseo-415)의 amend 스크린샷](amend.png): 메시지와 커밋 해시 변경을 확인할 수 있습니다. 설명은 [amend 기록](../troubleshooting-log.md#amend)에 있습니다.
- [나현준(vivleon)의 revert 명령·출력](revert-vivleon.txt): 원격 push 확인, 새 취소 커밋, 취소 전후 비교 결과입니다. 설명은 [트러블슈팅 기록](../troubleshooting-log.md#revert-vivleon)에 있습니다.

## 히스토리와 요구사항 점검

- [git-log.txt](git-log.txt): `git log --oneline --graph --all`의 실제 출력에서 그래프 줄 끝 공백만 제거했습니다. 위 기준 시점에 생성했으며, 현재 정리 PR의 최종 병합 커밋은 아직 포함하지 않습니다. `--all`에는 미병합·이전 브랜치도 나타납니다.
- [requirements-audit.json](requirements-audit.json): GitHub에서 확인한 팀원별 기여·리뷰·답변, PR별 상호작용, main 규칙과 실습 점검 결과입니다. 기준 시점의 `main` 점검과 이후 활동을 구분하며, `follow_up`에 vivleon의 PR 답변과 이슈 상태 정리를 추가했습니다. 이 PR에서 추가한 히스토리 파일과 문서 정리도 기준 시점 이후 변경입니다. GitHub 활동이 추가되면 내용도 갱신해야 합니다.
- 읽기 쉬운 결과와 보완할 항목은 [제출 전 점검](../../SUBMISSION.md#requirements-check)에 있습니다. 전체 요구사항 완료로 판정한 자료는 아닙니다.

## 히스토리 텍스트 갱신하기

팀 작업을 마친 뒤 저장소 루트에서 아래 명령을 실행합니다.

```bash
git fetch origin
git log --oneline --graph --all | sed 's/[[:blank:]]*$//' > docs/evidence/git-log.txt
```

- `git fetch origin`은 원격 브랜치 정보를 갱신합니다.
- 두 번째 명령은 그래프 줄 끝 공백을 `sed`로 제거한 뒤 커밋 흐름을 `git-log.txt`에 저장합니다. 커밋 해시·메시지와 그래프는 유지합니다. 같은 파일이 있으면 덮어쓰므로 먼저 내용을 확인합니다.
- 결과를 열어 이번 과제의 커밋과 병합 기록이 포함됐는지 확인합니다.
- 텍스트 대신 명령 결과가 보이는 스크린샷을 저장해도 됩니다.

## 제출 문서에 연결하기

증빙 파일을 실제로 만든 뒤 [SUBMISSION.md](../../SUBMISSION.md)의 Git 히스토리 증빙 항목에 파일 링크를 추가하고, PR로 올립니다. 아직 없는 파일의 링크나 수행하지 않은 실습 증빙은 추가하지 않습니다.
