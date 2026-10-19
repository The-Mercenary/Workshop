# Workshop

**A local workspace for images, illustrations, writing, PDFs, data and design — by The Mercenary.**

하나의 로컬 Workgroup 폴더에서 여섯 종류의 작업을 생성하고 편집하는 macOS 데스크톱 앱입니다. 파일은 선택한 폴더에 저장되며, 계정이나 클라우드 업로드가 필요하지 않습니다.

## Download · 다운로드

**[macOS Apple Silicon용 DMG 다운로드](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.1/Workshop-0.1.0-alpha.1-macos-arm64.dmg)**

[ZIP](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.1/Workshop-0.1.0-alpha.1-macos-arm64.zip) · [릴리스 안내와 이전 버전](https://github.com/The-Mercenary/Workshop/releases) · [SHA-256](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.1/SHA256SUMS.txt)

현재 버전은 **0.1.0-alpha.1 공개 알파**입니다. **Apple Silicon(M1 이상), macOS 14 이상**이 필요합니다. Intel Mac·Windows·Linux 설치 파일은 아직 제공하지 않습니다.

1. DMG를 열어 `Workshop.app`을 Applications로 복사합니다. 기존 Workshop 에디션이 있다면 별도 위치에 보관해 두세요.
2. Workshop을 열고 **Open Folder…**로 사용할 로컬 폴더를 선택하거나, **New Workgroup…**로 새 폴더를 만듭니다.
3. 왼쪽 **+ New**에서 작업 유형을 선택합니다. 기존 파일은 파일 트리에서 클릭해 엽니다.

## Work types

| 유형 | 작업 파일 |
|---|---|
| Image Work | `.imagework` |
| Illust Work | `.illustwork` |
| Writing Work | `.writingwork` |
| PDF Work | `.pdfwork` |
| Data Work | `.datawork` |
| Design Work | `.designwork` |

트리는 실제 디렉토리 구조를 표시합니다. 파일과 폴더 생성, 이름 변경, Workgroup 휴지통으로 이동, 마지막 삭제 복원을 지원합니다. 미저장 문서가 있으면 Workgroup 전환을 막고 현재 편집 내용을 유지합니다. 문서와 폴더를 자동으로 이동하거나 같은 이름의 항목을 덮어쓰지 않습니다.

Studio Dark·Light는 모든 Work에 적용되며 재시작 후에도 유지됩니다. 문서 자체의 색상과 기존 편집 도구 배치는 유지합니다. 마지막 Workgroup도 다음 실행 때 복원됩니다.

## Local data

작업 파일과 `.workgroup/` 메타데이터는 사용자가 선택한 폴더에 있습니다. `.workgroup/`에는 폴더 보기 상태와 휴지통 복원 자료가 있으므로 복원이 필요하면 이 폴더도 보관하세요.

앱 설정은 `~/Library/Application Support/The Mercenary/Workshop/`에 별도로 저장됩니다. 앱 번들 안에는 개인 문서·설정·개발 환경이 포함되지 않습니다. 앱을 교체해 업데이트해도 선택한 Workgroup의 문서 파일은 앱과 별도로 남습니다.

## Updates

현재 알파는 **릴리스 페이지에서 새 버전을 직접 내려받아 앱을 교체**합니다. 자동 업데이트 확인·자동 다운로드·백그라운드 설치는 포함하지 않습니다. 앱 시작 시 업데이트 서버에 접속하지 않습니다.

채널별 다운로드 메타데이터는 [updates/alpha.json](updates/alpha.json)에 있습니다. 이것은 배포 안내용이며 실행 파일을 자동 설치하는 업데이트 피드가 아닙니다. 후속 앱 내 업데이트 방향은 [UPDATE-POLICY.md](UPDATE-POLICY.md)를 참고하세요.

## Alpha scope

여섯 유형의 대표 편집·이력·파일 CRUD·저장·재열기와 전역 테마를 검증한 공개 알파입니다. 모든 원래 메뉴·외부 문서 형식·대형/손상 문서·인쇄 장치를 전수 검증한 정식판은 아닙니다. 파일 트리 탐색 상한은 깊이 16·4,096개 항목입니다. PDF OCR의 별도 모델 파일은 포함하지 않습니다. 여러 Workgroup 동시 표시, AI 에이전트, 온라인 협업과 외부 동시 편집 병합은 후속 범위입니다.

필요한 구성요소 라이선스와 고지는 앱의 `Contents/Resources/Notices/`에 포함됩니다. 이 저장소는 공식 다운로드와 릴리스 메타데이터를 제공하며, 사용자 문서나 개발용 원본 작업 폴더를 포함하지 않습니다.
