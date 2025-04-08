# Windows에서 Oh My Posh 설치 가이드

> 작성일: 2025-04-08

## Oh My Posh란?
Oh My Posh는 모든 쉘을 위한 프롬프트 테마 엔진으로, 터미널에서 아름답고 기능적인 프롬프트를 구성할 수 있게 해줍니다. PowerShell, Bash, Zsh 등 다양한 쉘에서 사용할 수 있습니다.

## 설치 방법

### 1. Scoop을 통한 설치 (권장)
이미 Scoop이 설치되어 있다면, 다음 명령어로 쉽게 Oh My Posh를 설치할 수 있습니다:

```powershell
scoop install oh-my-posh
```

### 2. 직접 설치 (winget 사용)
Scoop 없이 winget을 사용하여 설치할 수도 있습니다:

```powershell
winget install JanDeDobbeleer.OhMyPosh
```

### 3. PowerShell 갤러리를 통한 모듈 설치
PowerShell 모듈로 설치하려면:

```powershell
Install-Module oh-my-posh -Scope CurrentUser
```

## 필요한 폰트 설치

Oh My Posh의 모든 아이콘과 글리프를 제대로 표시하려면 Nerd Font를 설치해야 합니다:

### Scoop으로 폰트 설치하기:
```powershell
# 먼저 nerd-fonts 버킷 추가
scoop bucket add nerd-fonts

# 원하는 폰트 설치 (예: JetBrains Mono)
scoop install JetBrainsMono-NF
```

### 또는 직접 다운로드:
1. [Nerd Fonts 웹사이트](https://www.nerdfonts.com/font-downloads)에서 원하는 폰트 다운로드
2. 다운로드한 폰트 파일 설치
3. 터미널 설정에서 설치한 폰트로 변경

## PowerShell 프로필에 Oh My Posh 설정하기

### 1. PowerShell 프로필 생성/편집
PowerShell 프로필이 없다면 다음 명령어로 생성합니다:

```powershell
if (!(Test-Path -Path $PROFILE)) {
    New-Item -ItemType File -Path $PROFILE -Force
}
notepad $PROFILE
```

### 2. 프로필에 Oh My Posh 초기화 코드 추가
프로필 파일에 다음 코드를 추가합니다:

```powershell
# Oh My Posh 초기화
oh-my-posh init pwsh | Invoke-Expression
```

### 3. 테마 지정 (선택 사항)
특정 테마를 사용하려면:

```powershell
# 특정 테마 사용
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\paradox.omp.json" | Invoke-Expression
```

## 테마 미리보기 및 변경

### 사용 가능한 테마 목록 보기:
```powershell
Get-PoshThemes
```

### 테마 변경:
프로필에서 `--config` 뒤의 테마 경로를 원하는 테마로 변경하세요.

## 커스텀 테마 만들기

1. 기존 테마를 복사하여 시작:
```powershell
Copy-Item "$env:POSH_THEMES_PATH\paradox.omp.json" ~\custom-theme.omp.json
```

2. 복사한 테마 편집:
```powershell
notepad ~\custom-theme.omp.json
```

3. 커스텀 테마 적용:
```powershell
oh-my-posh init pwsh --config "~\custom-theme.omp.json" | Invoke-Expression
```

## 문제 해결

### 아이콘이 제대로 표시되지 않는 경우:
- Nerd Font가 제대로 설치되었는지 확인
- 터미널 설정에서 폰트가 Nerd Font로 설정되었는지 확인

### 성능 이슈가 있는 경우:
- 더 가벼운 테마로 변경 시도
- 특정 모듈 비활성화 (Git 상태 등)

## 추가 팁

1. Windows Terminal에서 설정:
   - 설정 -> 프로필 -> PowerShell -> 모양 -> 글꼴 변경

2. VSCode 터미널에서 설정:
   - settings.json에 `"terminal.integrated.fontFamily": "JetBrainsMono NF"` 추가

3. 테마 미리보기:
   - [Oh My Posh 웹사이트](https://ohmyposh.dev/docs/themes)에서 테마 갤러리 확인

## 참고 자료
- 공식 웹사이트: https://ohmyposh.dev/
- GitHub 저장소: https://github.com/JanDeDobbeleer/oh-my-posh
- 문서: https://ohmyposh.dev/docs/
