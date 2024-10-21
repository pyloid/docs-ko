---
icon: file-code
---

# Pyloid-React-Vite

Pyloid-React-Boilerplate는 React 프론트엔드와 Python 백엔드를 결합한 프로젝트를 위한 템플릿입니다. 여기서는 프로젝트 설정, 개발, 그리고 빌드 과정을 자세히 설명하겠습니다.

### 사전 요구사항

- [사전 요구사항](../../getting-started/prerequisites.md)

## 1. 프로젝트 초기화

프로젝트를 시작하기 전에 필요한 모든 의존성을 설치해야 합니다.

```bash
npm run init
```

이 명령은 다음 작업을 수행합니다:

1. npm 패키지 설치
2. Python 가상 환경 생성 (venv-pyloid)
3. Python 의존성 설치 (requirements.txt 기반)

운영 체제에 따라 적절한 스크립트가 실행됩니다.

## 2. 개발 서버 실행

개발 중에는 다음 명령으로 프론트엔드와 백엔드 서버를 동시에 실행할 수 있습니다:

```bash
npm run dev
```

이 명령은 다음 작업을 수행합니다:

1. Vite를 사용하여 React 프론트엔드 개발 서버 실행
2. Python 백엔드 서버 실행 (src-pyloid/main.py)

concurrently 패키지를 사용하여 두 프로세스를 병렬로 실행합니다.

## 3. 프로젝트 빌드

프로덕션 배포를 위해 프로젝트를 빌드하려면 다음 명령을 사용하세요:

```bash
npm run build
```

이 명령은 다음 작업을 수행합니다:

1. TypeScript 컴파일 (tsc -b)
2. Vite를 사용한 프론트엔드 빌드
3. PyInstaller를 사용하여 Python 백엔드를 실행 파일로 패키징

### PyInstaller를 사용한 백엔드 패키징

PyInstaller는 Python 애플리케이션을 독립 실행 파일로 변환하는 도구입니다. Pyloid Boilerplate는 각 운영 체제에 대해 다른 spec 파일을 사용합니다:

- Windows: `build-windows.spec`
- Linux: `build-linux.spec`
- MacOS: `build-macos.spec`

이 spec 파일들은 PyInstaller에 포함할 파일과 사용할 옵션을 지정합니다.

### PyInstaller 작동 방식

1. 의존성 분석: PyInstaller는 Python 스크립트와 그 의존성을 분석합니다.
2. 파일 수집: 필요한 모든 Python 모듈, 라이브러리, 데이터 파일을 수집합니다.
3. 바이너리 생성: 수집된 파일들을 단일 디렉토리나 단일 실행 파일로 패키징합니다.

### 사용자 정의 빌드 프로세스

프로젝트의 특정 요구사항에 맞게 빌드 프로세스를 수정할 수 있습니다:

1. `package.json`의 scripts 섹션 수정
2. PyInstaller spec 파일 수정 (예: `build-windows.spec`, `build-linux.spec`, `build-macos.spec`)
3. 필요한 경우 추가 빌드 스크립트 작성

### 중요 참고사항

- 크로스 플랫폼 빌드: 각 플랫폼에 대한 빌드는 해당 운영 체제에서 수행해야 합니다.
- 환경 변수: 프로덕션 환경에 따라 환경 변수를 적절히 설정해야 할 수 있습니다.

이 가이드는 Pyloid Boilerplate를 사용하여 프로젝트를 초기화, 개발, 빌드하는 과정을 이해하는 데 도움이 될 것입니다. PyInstaller를 사용한 백엔드 패키징은 배포를 단순화하고 의존성 관리를 용이하게 합니다.
