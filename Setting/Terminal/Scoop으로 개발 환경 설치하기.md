# Scoop으로 개발 환경 설치하기

> 작성일: 2025-04-08

## JDK(Java Development Kit) 설치하기

Scoop을 통해 다양한 버전의 JDK를 쉽게 설치하고 관리할 수 있습니다.

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

### JDK 설치 확인

설치가 완료되면 다음 명령어로 확인할 수 있습니다:

```powershell
java -version
javac -version
```

### JAVA_HOME 환경 변수

Scoop은 자동으로 환경 변수를 설정하므로 별도로 JAVA_HOME을 설정할 필요가 없습니다. 하지만 확인하고 싶다면:

```powershell
echo $env:JAVA_HOME
```

## Python 설치하기

Python도 Scoop을 사용하여 다양한 버전을 설치할 수 있습니다.

### Python 설치 명령어

```powershell
# 최신 Python 설치
scoop install python

# 특정 버전 설치
scoop install python39  # Python 3.9
scoop install python310 # Python 3.10
scoop install python311 # Python 3.11
```

### Python 설치 확인

설치 후 다음 명령어로 확인할 수 있습니다:

```powershell
python --version
pip --version
```

### pip 패키지 관리

Python 패키지 설치 예시:

```powershell
pip install pandas numpy matplotlib
```

## 여러 버전 관리하기

Scoop의 장점 중 하나는 여러 버전의 같은 프로그램을 쉽게 전환할 수 있다는 것입니다.

### Java 버전 전환

```powershell
# Java 11로 전환
scoop reset openjdk11

# Java 17로 전환
scoop reset openjdk17
```

### Python 버전 전환

```powershell
# Python 3.9로 전환
scoop reset python39

# Python 3.11로 전환
scoop reset python311
```

## 설치된 패키지 관리

### 설치된 패키지 목록 확인

```powershell
scoop list
```

### 패키지 업데이트

```powershell
# 특정 패키지 업데이트
scoop update python

# 모든 패키지 업데이트
scoop update *
```

### 패키지 제거

```powershell
scoop uninstall python39
```

## 주의사항 및 팁

1. 여러 버전의 Java나 Python을 설치할 때는 각각 다른 이름으로 설치해야 합니다 (예: openjdk11, openjdk17).

2. Python 가상 환경 사용 권장:
   ```powershell
   python -m venv myenv
   .\myenv\Scripts\Activate.ps1
   ```

3. JDK 버전을 전환할 때는 IDE나 빌드 도구의 설정도 함께 확인해야 합니다.

4. 최신 패키지 목록 업데이트:
   ```powershell
   scoop update
   ```

## 참고 자료

- OpenJDK 공식 사이트: https://openjdk.java.net/
- Python 공식 사이트: https://www.python.org/
- Scoop 버킷 검색: https://scoop.sh/
