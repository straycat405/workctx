# workctx

Codex와 Claude가 같은 프로젝트에서 이어서 작업하도록, 에이전트에 종속되지 않는 로컬 Markdown 상태 파일을 준비하는 작은 CLI입니다.

## 요구 사항

- Python 3.9 이상
- 외부 패키지, 서버, 계정, 데이터베이스 불필요

## 사용법

저장소에서 실행할 때:

```sh
python3 /Users/djp/2026/dev/workctx/workctx init
python3 /Users/djp/2026/dev/workctx/workctx show
```

다른 폴더에서 프로젝트 경로를 지정할 수도 있습니다:

```sh
python3 /Users/djp/2026/dev/workctx/workctx init /path/to/project
```

`init`은 `.workctx/STATE.md`가 없을 때만 만들고, `AGENTS.md`와 `CLAUDE.md`에는 식별 가능한 안내 블록을 추가합니다. 기존 파일과 상태 기록은 덮어쓰지 않습니다. 다시 실행해도 안내 블록은 중복되지 않습니다.

## 상태 기록 규칙

작업 시작 시 에이전트가 `.workctx/STATE.md`를 읽습니다. 작업을 저장하거나 끝낼 때 목표, 현재 상태, 완료한 일, 바로 할 다음 행동, 결정 사항, 관련 파일을 한국어로 갱신합니다. 최신 사용자 요청이 오래된 기록보다 우선합니다.

## 범위

MVP는 한 프로젝트 폴더를 두 에이전트가 함께 사용하는 흐름을 지원합니다. 상태 기록은 프로젝트 안에 남으므로 에이전트와 별도로 자동 동기화되지 않습니다. 다른 컴퓨터나 별도 복제본 간 동기화, 자동 훅, GUI는 포함하지 않습니다.
