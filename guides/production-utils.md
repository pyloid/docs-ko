# 프로덕션 유틸리티

## `get_production_path()`

프로덕션 환경에서 리소스 파일의 경로를 반환합니다.

### 매개변수

없음

### 반환값

- `Optional[str]`: 프로덕션 환경에서 리소스 파일의 경로를 반환합니다. 일반 Python 스크립트로 실행 중인 경우 `None`을 반환합니다.

### 설명

이 함수는 현재 실행 환경이 프로덕션 환경(예: PyInstaller로 빌드된 실행 파일)인지 확인하고, 그렇다면 리소스 파일의 경로를 반환합니다. 일반 Python 스크립트로 실행 중인 경우 `None`을 반환합니다.

### 사용 예시

```python
from pyloid import Pyloid, is_production, get_production_path

app = Pyloid(single_instance=True)

if (is_production()):
    app.set_icon(os.path.join(get_production_path(), "icons/icon.ico"))
else:
    app.set_icon("icons/icon.ico")
    app.set_tray_icon("icons/icon.ico")
```

## `is_production()`

현재 환경이 프로덕션 환경인지 확인합니다.

### 매개변수

없음

### 반환값

- `bool`: 프로덕션 환경이면 `True`를 반환하고, 그렇지 않으면 `False`를 반환합니다.

### 설명

이 함수는 `sys.frozen` 속성을 검사하여 현재 실행 환경이 프로덕션 환경(예: PyInstaller로 빌드된 실행 파일)인지 확인합니다.

### 사용 예시

```python
from pyloid import Pyloid, is_production, get_production_path

app = Pyloid(single_instance=True)

if (is_production()):
    window.load_file(os.path.join(get_production_path(), "build/index.html"))
else:
    window.load_url("http://localhost:5173")
```
