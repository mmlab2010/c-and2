# 계산기 & 환율 계산기 안드로이드 웹뷰 앱 (CalcExchangeApp)

`https://mmlab2010.github.io/calc/` 사이트(복합 계산기 & 실시간 환율 계산기)를 **전체화면(Immersive Fullscreen)** 안드로이드 앱으로 패키징한 프로젝트입니다.  
로컬 PC에 안드로이드 스튜디오(Android Studio)가 없어도 **GitHub Actions**를 통해 클라우드에서 자동으로 APK 파일을 빌드하고 다운로드할 수 있도록 구성되어 있습니다.

---

## 주요 특징

1. **완전한 전체화면(Immersive Mode) 웹뷰**
   - 상단 상태바(Status Bar), 액션바(Action Bar), 하단 내비게이션 바(Navigation Bar)를 숨기고 노치 영역까지 확장하여 네이티브 앱처럼 화면 전체를 꽉 채워 보여줍니다.
   - `JavaScript`, `DOM Storage(localStorage)` 및 쿠키를 활성화하여 계산 기록 및 환율 데이터가 정상 동작합니다.
   - 안드로이드 물리/제스처 **뒤로가기 버튼**을 누르면 웹뷰 내 이전 기록으로 이동하며, 더 이상 뒤로 갈 페이지가 없을 때 앱이 종료됩니다.
   - 네트워크 연결이 끊어졌을 때 안내 화면과 **다시 시도** 버튼을 제공합니다.

2. **맞춤형 고해상도 앱 아이콘**
   - 계산기 기호(`+`, `-`, `×`, `÷`, `=`, `%`)와 글로벌 통화 기호(`$`, `€`, `£`, `¥`, `₩`) 및 환율 교환 화살표가 조화를 이루는 밝고 세련된 3D 글래스모피즘 디자인 아이콘을 제작하여 적용했습니다.
   - 원본 아이콘: 프로젝트 루트의 [`app_icon.png`](./app_icon.png) (1024×1024)
   - 안드로이드 해상도별(`mdpi` ~ `xxxhdpi`) 일반 아이콘, 원형 아이콘, Adaptive Icon(`mipmap-anydpi-v26`)에 모두 반영되어 있습니다.

3. **안드로이드 스튜디오 없이 GitHub Actions 자동 빌드**
   - [`.github/workflows/android-build.yml`](./.github/workflows/android-build.yml) 워크플로우가 포함되어 있어 GitHub 저장소에 코드를 올리기만 하면 자동으로 APK를 빌드합니다.

---

## GitHub Actions로 APK 빌드 및 다운로드 방법

컴퓨터에 안드로이드 스튜디오를 설치할 필요 없이 아래 순서대로 진행하면 APK를 바로 얻을 수 있습니다.

### 1단계: GitHub 저장소 생성 및 코드 업로드
1. [GitHub](https://github.com/)에 로그인한 뒤 새 저장소(Repository)를 생성합니다.
2. 현재 폴더에서 터미널(PowerShell 또는 명령 프롬프트)을 열고 아래 명령어를 실행하여 GitHub에 푸시합니다:
   ```powershell
   git init
   git add .
   git commit -m "Initial commit: Calculator & Currency WebView Android App"
   git branch -M main
   git remote add origin https://github.com/<본인계정>/<저장소이름>.git
   git push -u origin main
   ```
   *(또는 GitHub 웹페이지에서 파일 업로드 기능을 이용해 프로젝트 파일들을 그대로 업로드해도 됩니다. 단, 숨김 폴더인 `.github` 폴더가 함께 올라가야 합니다.)*

### 2단계: GitHub Actions에서 빌드 확인 및 APK 다운로드
1. GitHub 저장소 상단 탭에서 **Actions** 메뉴로 이동합니다.
2. `Android APK Build` 워크플로우가 자동으로 실행 중이거나 완료(초록색 체크 표시)된 것을 확인합니다.
   - 만약 수동으로 다시 빌드하고 싶다면 좌측의 **Android APK Build** 클릭 → 우측 **Run workflow** 버튼을 누르면 언제든 빌드됩니다.
3. 완료된 워크플로우 항목을 클릭한 뒤 페이지 하단의 **Artifacts** 섹션으로 스크롤합니다.
4. 아래 두 가지 APK 중 원하는 파일을 다운로드(ZIP 압축 해제 시 `.apk` 파일 확인)하여 스마트폰에 설치합니다:
   - **`CalcExchange-Debug-APK`**: 테스트용 디버그 APK (`CalcExchange-debug.apk`)
   - **`CalcExchange-Release-APK`**: 기본 서명이 완료되어 스마트폰에 바로 설치 가능한 릴리즈 APK (`CalcExchange-release.apk`)

