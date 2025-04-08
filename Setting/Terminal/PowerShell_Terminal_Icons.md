# PowerShell Terminal-Icons 설치 및 임포트

## 간단한 설치 방법

```powershell
Install-Module -Name Terminal-Icons -Repository PSGallery -Force
Import-Module -Name Terminal-Icons
```

## 프로필에 자동 로드 설정

PowerShell 프로필에 추가하여 자동으로 로드되게 하려면:

```powershell
notepad $PROFILE
```

프로필 파일에 다음 줄 추가:

```powershell
Import-Module -Name Terminal-Icons
```

## 작동 확인

```powershell
Get-ChildItem
```

위 명령을 실행하면 파일과 폴더 아이콘이 컬러로 표시됩니다.
