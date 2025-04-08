# Windows에서 Scoop 설치 가이드

> 작성일: 2025-04-08

## Scoop이란?
Scoop은 Windows용 커맨드 라인 설치 프로그램(패키지 매니저)입니다. Linux의 apt나 macOS의 Homebrew와 유사한 역할을 합니다. 필요한 소프트웨어를 쉽게 설치, 업데이트, 제거할 수 있게 해줍니다.

## 사전 요구 사항
- Windows 7 SP1+ / Windows Server 2008+
- PowerShell 5.1 이상 (Windows 10에 기본 탑재)
- .NET Framework 4.5 이상

## 설치 과정

### 1. PowerShell 정책 설정하기
Windows에서 Scoop을 설치하기 위해 먼저 PowerShell 실행 정책을 변경해야 합니다. PowerShell을 관리자 권한으로 실행하고 다음 명령어를 입력합니다:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

이후 'Y'를 입력해 변경을 확인합니다.

### 2. Scoop 설치하기
PowerShell(관리자 권한 불필요)에서 다음 명령어를 실행합니다:

```powershell
irm get.scoop.sh | iex
```

또는 긴 버전의 명령어를 사용할 수도 있습니다:

```powershell
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
```

### 3. 설치 확인하기
설치가 완료되면 다음 명령어로 Scoop이 제대로 설치되었는지 확인할 수 있습니다:

```powershell
scoop --version
```

## 기본 사용법

### 앱 검색하기
```powershell
scoop search <앱이름>
```

### 앱 설치하기
```powershell
scoop install <앱이름>
```

### 앱 업데이트하기
```powershell
scoop update <앱이름>
```

모든 앱 업데이트:
```powershell
scoop update *
```

### 앱 제거하기
```powershell
scoop uninstall <앱이름>
```

### 저장소(bucket) 추가하기
기본 저장소 외에 추가 저장소를 사용할 수 있습니다:

```powershell
scoop bucket add extras
scoop bucket add versions
scoop bucket add nerd-fonts
```

## 주의사항
- Scoop은 기본적으로 사용자 프로필 폴더 아래에 설치됩니다 (`%USERPROFILE%\scoop`).
- 시스템 전체에 설치하려면 추가 설정이 필요합니다.
- 일부 앱은 관리자 권한이 필요할 수 있습니다.

## 팁
1. `scoop bucket known` 명령어로 공식 지원 저장소 목록을 확인할 수 있습니다.
2. `scoop help` 명령어로 추가 도움말을 확인할 수 있습니다.
3. 설치된 앱 목록 확인: `scoop list`

## 문제 해결
문제가 발생한 경우:
1. `scoop checkup`으로 일반적인 문제를 확인
2. GitHub 이슈 페이지 확인: https://github.com/ScoopInstaller/Scoop/issues

## 참고 자료
- 공식 웹사이트: https://scoop.sh/
- GitHub 저장소: https://github.com/ScoopInstaller/Scoop
