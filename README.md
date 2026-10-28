# Sprint CLI 공식 문서

Sprint는 이슈, 프로젝트, 스프린트와 팀 업무를 관리하는 CLI입니다. npm 패키지는 `@hyungjuk/sprint`, 실행 명령은 `sprint`입니다.

```sh
npm install --global @hyungjuk/sprint
sprint --version
sprint --help
```

## 문서 찾아보기

- [CLI 명령 레퍼런스](cli/README.md): 전체 → 그룹 → 개별 명령의 문법·예시·플래그.
- [AI 사용 안내](cli/agents.md): 명령 탐색, JSON 응답, 프로젝트 지시와 MCP 연결.
- [인증과 프로필](cli/reference/topic/authentication.md): Sprint 서버 로그인과 private 자동화 토큰.
- [출력과 종료 코드](cli/reference/topic/output.md): JSON, 페이지네이션과 오류 처리.
- [리비전과 변경](cli/reference/topic/revisions.md): 충돌 검사와 중복 요청 방지.
- [업데이트](cli/reference/update.md): 자동 업데이트, 수동 y/n, 자동화 옵션.

## 도움말 예시

```sh
sprint --help
sprint issues --help
sprint issues get --help
sprint help --limit 10 -- subscription
sprint topic authentication
sprint --schema issues
```

개별 명령 도움말은 NAME, SYNOPSIS, DESCRIPTION, EXAMPLES, POSITIONAL ARGUMENTS, FLAGS, GLOBAL FLAGS, OUTPUT, AUTHENTICATION, NOTES, SEE ALSO로 구성됩니다. 그룹은 바로 아래 하위 명령만 표시합니다. `github pairs`처럼 직접 실행할 수 있으면서 하위 명령도 가진 경우 두 가지를 함께 표시합니다.

`--schema DOMAIN`은 API 동작 계약 JSON입니다. CLI의 실제 플래그 문법은 해당 명령의 `--help`를 확인하세요. `--llms`는 짧은 AI 안내, `--llms DOMAIN`은 기존 도메인 계약 JSON입니다. 업무 명령은 이미 JSON을 출력하므로 `--format=json` 옵션은 없습니다.

## 시작 전 알아둘 사항

CLI 설치만으로 Sprint 서버나 프로젝트가 연결되지는 않습니다. 업무 명령에는 자신의 Sprint 서버에 접근할 수 있는 프로필 또는 private 자동화 토큰 파일이 필요합니다. npm 로그인은 패키지 배포용이며 Sprint 로그인과 다릅니다.

AI가 Sprint를 사용하게 하려면 프로젝트 지시 파일에 사용 정책을 두거나 Sprint MCP를 에이전트에 등록해야 합니다. 단순 설치만으로 모든 AI에 도구나 지시가 등록되지는 않습니다. 사용자 요청과 프로젝트 범위에 맞게 조회·변경하고, 변경 후 서버 응답을 확인하세요.

## 문서 관리

이 저장소는 공개 CLI 문서만 관리합니다. 앱의 DB, 자격증명, 세션, 작업 기록과 내부 인수 자료를 포함하지 않습니다.

`cli/`는 Sprint 패키지의 명령 정의와 같은 렌더러에서 생성됩니다. 배포 소스에서 `npm run docs:generate`로 갱신하고 `npm run docs:check`로 변경 누락을 검사합니다. `prepack`도 이 검사를 실행합니다. 생성된 페이지를 직접 수정하기보다 명령 정의를 고친 뒤 다시 생성해야 합니다.

명령 그룹, 명령별 도움말, 검색과 자동화용 출력을 나누는 방식은 [Google Cloud CLI 도움말](https://docs.cloud.google.com/sdk/gcloud/reference/help)과 [자동화 안내](https://docs.cloud.google.com/sdk/docs/scripting-gcloud)를 참고했습니다.
