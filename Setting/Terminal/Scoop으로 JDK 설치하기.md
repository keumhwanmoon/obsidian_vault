# Scoop으로 JDK 설치하기

> 작성일: 2025-04-08

## 개요
Java Development Kit(JDK)는 Java 애플리케이션을 개발하고 실행하는 데 필요한 도구와 라이브러리의 모음입니다. Scoop 패키지 관리자를 사용하면 Windows에서 쉽게 다양한 버전의 JDK를 설치하고 관리할 수 있습니다.

## JDK 설치 방법

### 대표적인 JDK 설치 명령어

```powershell
# OpenJDK 17 설치 (LTS 버전)
scoop install openjdk17

# 최신 OpenJDK 설치
scoop install openjdk

# 특정 버전의 OpenJDK 설치
scoop install openjdk11
scoop install openjdk8

# Oracle JDK 설치
scoop install java
```

### 설치된 JDK 확인

설치가 완료되면 다음 명령어로 확인할 수 있습니다:

```powershell
java -version   # Java Runtime Environment 버전 확인
javac -version  # Java Compiler 버전 확인
```

## 설치 위치

Scoop으로 설치한 JDK는 다음 경로에 설치됩니다:

```
%USERPROFILE%\scoop\apps\[패키지명]\[버전]
```

예를 들면:
```
C:\Users\[사용자이름]\scoop\apps\openjdk17\current\
```

## 환경 변수 설정

### JAVA_HOME 환경 변수

Scoop은 자동으로 환경 변수를 설정하므로 별도로 JAVA_HOME을 설정할 필요가 없습니다. 현재 설정된 JAVA_HOME을 확인하려면:

```powershell
echo $env:JAVA_HOME
```

### PATH 환경 변수

Scoop은 자동으로 Java 실행 파일의 경로를 PATH에 추가합니다. 이는 `scoop\shims` 디렉토리를 통해 관리됩니다.

## 여러 JDK 버전 관리하기

### 여러 버전 설치

다양한 버전의 JDK를 동시에 설치할 수 있습니다:

```powershell
scoop install openjdk8
scoop install openjdk11
scoop install openjdk17
```

### 버전 전환

설치된 JDK 버전 간에 쉽게 전환할 수 있습니다:

```powershell
# Java 8로 전환
scoop reset openjdk8

# Java 11로 전환
scoop reset openjdk11

# Java 17로 전환
scoop reset openjdk17
```

전환 후 다음 명령으로 현재 활성화된 버전을 확인할 수 있습니다:
```powershell
java -version
```

## JDK 업데이트 및 관리

### 업데이트 확인

사용 가능한 업데이트 확인:

```powershell
scoop status
```

### JDK 업데이트

특정 JDK 버전 업데이트:

```powershell
scoop update openjdk17
```

### JDK 제거

더 이상 필요하지 않은 JDK 버전 제거:

```powershell
scoop uninstall openjdk8
```

## 주의사항 및 팁

1. 여러 JDK 버전을 설치할 때는 각각 다른 패키지 이름으로 설치해야 합니다(openjdk8, openjdk11 등).

2. IDE에서 JDK 설정:
   - IntelliJ IDEA: File > Project Structure > Project > SDK
   - Eclipse: Window > Preferences > Java > Installed JREs
   - VS Code: settings.json에 "java.home" 설정

3. 빌드 도구 설정:
   - Maven: JAVA_HOME 환경 변수 또는 Maven 설정 파일
   - Gradle: gradle.properties 파일에 org.gradle.java.home 설정

4. 특정 프로젝트에 사용할 JDK 버전을 명시적으로 지정하는 것이 좋습니다.

## 문제 해결

### JDK 설치 후 java 명령이 작동하지 않는 경우

```powershell
# Scoop shims 경로 확인
echo $env:PATH

# 필요한 경우 수동으로 경로 추가
$env:PATH += ";$env:USERPROFILE\scoop\shims"
```

### 여러 JDK 버전 간 충돌 발생 시

```powershell
# 현재 활성화된 JDK 확인
scoop list

# 특정 버전으로 명시적 재설정
scoop reset openjdk17
```

## 참고 자료

- OpenJDK 공식 사이트: https://openjdk.java.net/
- Oracle JDK 다운로드: https://www.oracle.com/java/technologies/downloads/
- Java 버전별 특징: https://www.oracle.com/java/technologies/java-se-glance.html
- Scoop 버킷 검색: https://scoop.sh/
