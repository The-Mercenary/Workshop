# Workshop

The Mercenary의 로컬 멀티 타입 작업 앱입니다. 하나의 Workgroup 폴더에서 이미지·일러스트·글·PDF·데이터·디자인을 만들고 편집합니다. 작업 파일은 선택한 로컬 폴더에 저장하며 계정이나 문서 업로드가 필요하지 않습니다.

현재 공개 알파는 **0.1.0-alpha.2**입니다. 아래에서 운영체제와 CPU에 맞는 파일을 받으세요.

| 환경 | 최소 기준 | 설치 파일 |
|---|---|---|
| macOS Apple Silicon | macOS 14+ | [다운로드](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.2/Workshop-0.1.0-alpha.2-macos-arm64.dmg) |
| macOS Intel | macOS 14+ | [다운로드](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.2/Workshop-0.1.0-alpha.2-macos-x64.dmg) |
| Windows x64 | Windows 11+ | [다운로드](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.2/studio.themercenary.workshop.suite-win-x64-alpha-Setup.exe) |
| Windows ARM64 | Windows 11 ARM64+ | [다운로드](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.2/studio.themercenary.workshop.suite-win-arm64-alpha-Setup.exe) |
| Linux x64 | Ubuntu 22.04 / glibc 2.35+ | [다운로드](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.2/Workshop-0.1.0-alpha.2-linux-x64.tar.gz) |
| Linux ARM64 | Ubuntu 24.04 / glibc 2.39+ | [다운로드](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.2/Workshop-0.1.0-alpha.2-linux-arm64.tar.gz) |

[전체 파일·ZIP·이전 버전](https://github.com/The-Mercenary/Workshop/releases) · [SHA-256 확인](https://github.com/The-Mercenary/Workshop/releases/download/v0.1.0-alpha.2/SHA256SUMS.txt)

- **Mac:** DMG에서 Workshop.app을 Applications로 복사합니다. Developer ID 서명·Apple 공증·티켓 첨부를 완료했습니다.
- **Windows:** Setup.exe를 실행해 사용자 계정에 설치합니다. ZIP은 압축을 푼 폴더에서 실행하는 대안입니다. 현재 Windows 파일에는 Authenticode 서명이 없어 SmartScreen 경고가 나타날 수 있으며, 조직의 실행 정책이 설치를 제한할 수 있습니다.
- **Linux:** tar.gz 전체를 쓰기 가능한 로컬 폴더에 풀고 `Workshop`을 실행합니다. `Workshop.AppImage`를 같은 폴더에 두세요. 제공 런처는 FUSE와 관리자 권한 없이 추출 후 실행합니다. GUI 세션과 호환되는 그래픽 드라이버·시스템 라이브러리가 필요합니다.

이전 **0.1.0-alpha.1에는 앱 내 업데이터가 없습니다.** 이번 버전을 한 번 직접 설치하면 이후부터 앱 내 업데이트를 사용할 수 있습니다. 기존 Workshop 에디션과 Workgroup 폴더는 별도로 보관할 수 있습니다.

## 로컬 작업

**Open Folder…**로 원하는 로컬 폴더를 열거나 **New Workgroup…**로 새 폴더를 만듭니다. Workgroup은 앱 설치 폴더 밖의 문서용 폴더에 두세요. 왼쪽 파일 트리는 실제 폴더 구조를 표시하며 파일·폴더 생성, 편집·저장, 이름 변경, Workgroup 휴지통 이동과 마지막 삭제 복원을 지원합니다.

| 유형 | 파일 |
|---|---|
| Image Work | `.imagework` |
| Illust Work | `.illustwork` |
| Writing Work | `.writingwork` |
| PDF Work | `.pdfwork` |
| Data Work | `.datawork` |
| Design Work | `.designwork` |

Studio Dark·Light와 마지막 Workgroup은 앱 재실행·업데이트 후 복원됩니다. 문서 자체의 색상과 각 편집기의 원래 도구 배치를 유지합니다.

## 업데이트와 데이터

상단 **Updates**에서 새 버전을 확인합니다. 기본값은 **하루 한 번 자동 확인**이며 같은 창에서 끌 수 있습니다. 사용자가 다운로드를 선택하고, 편집 내용을 저장한 뒤 **Install and restart**를 누르면 새 버전으로 교체합니다. 미저장 문서가 있으면 설치·재시작을 막습니다. 네트워크 오류가 나도 로컬 편집을 계속할 수 있습니다.

업데이트 통신은 공식 GitHub 릴리스 정보와 앱 패키지 요청에 한정합니다. 문서 내용·작업 파일명·폴더 경로를 업로드하지 않습니다. 다운로드 패키지의 제품 ID·버전·SHA-256을 검사합니다. 자세한 신뢰 경계와 복구 방법은 [UPDATE-POLICY.md](UPDATE-POLICY.md)에 있습니다.

문서와 `.workgroup/` 메타데이터는 선택한 폴더에 남습니다. 휴지통 복원 자료가 필요하면 `.workgroup/`도 보관하세요. 앱 설정·업데이트 캐시는 다음 사용자 경로에 따로 있습니다.

| OS | 설정·캐시 루트 |
|---|---|
| macOS | `~/Library/Application Support/The Mercenary/Workshop/` |
| Windows | `%LOCALAPPDATA%\The Mercenary\Workshop\` |
| Linux | `${XDG_DATA_HOME:-$HOME/.local/share}/the-mercenary/workshop/` |

## 알파 검증 범위

대상 OS·CPU의 실제 네이티브 앱으로 여섯 유형의 생성·편집·저장·재열기, 전역 테마, 손상된 다운로드 거부와 이전 검증 버전에서 새 버전으로의 교체·재실행을 확인했습니다. 이는 모든 PC·외부 파일 형식·메뉴·프린터·그래픽 장치의 호환성을 보장하는 정식판은 아닙니다. 오래된 OS·32비트 CPU·기업의 보안 정책은 지원 범위 밖일 수 있습니다.

파일 트리는 깊이 16·4,096개 항목까지 탐색합니다. PDF OCR의 별도 모델, AI 에이전트, 온라인 협업, 외부 동시 편집 병합은 포함하지 않습니다. 필요한 구성요소 고지는 각 설치 파일의 `Notices`에 포함됩니다. 이 저장소에는 공개 다운로드·배포 메타데이터만 보관합니다.
