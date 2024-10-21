# BrowserWindow

## 개요

BrowserWindow 클래스는 Pyloid 애플리케이션 내에서 브라우저 창을 관리하도록 설계되었습니다. PySide6의 QMainWindow를 확장하여 브라우저 창을 생성하고 관리하기 위한 추가 기능을 제공합니다.

## 생성자

```python
def __init__(self, app, title: str = "pylon app", width: int = 800, height: int = 600, x: int = 200, y: int = 200, frame: bool = True, context_menu: bool = False, dev_tools: bool = False, js_apis: List[PylonAPI] = []):
```

BrowserWindow 객체를 초기화합니다.

- **매개변수**:
  - `app`: Pyloid 인스턴스
  - `title` (str): 창 제목 (기본값: "pylon app")
  - `width` (int): 창 너비 (기본값: 800)
  - `height` (int): 창 높이 (기본값: 600)
  - `x` (int): 창 x 좌표 (기본값: 200)
  - `y` (int): 창 y 좌표 (기본값: 200)
  - `frame` (bool): 창 프레임 표시 여부 (기본값: True)
  - `context_menu` (bool): 컨텍스트 메뉴 활성화 여부 (기본값: False)
  - `dev_tools` (bool): 개발자 도구 활성화 여부 (기본값: False)
  - `js_apis` (List\[PyloidAPI]): 추가할 JavaScript API 목록 (기본값: \[])

## 메서드

```python
def load_file(self, file_path: str) -> None:
```

로컬 HTML 파일을 웹 뷰에 로드합니다.

- **매개변수**:
  - `file_path` (str): 로드할 HTML 파일 경로

```python
def load_url(self, url: str) -> None:
```

지정된 URL을 창에 로드합니다.

- **매개변수**:
  - `url` (str): 로드할 URL

```python
def set_title(self, title: str) -> None:
```

창의 제목을 설정합니다.

- **매개변수**:
  - `title` (str): 새 창 제목

```python
def set_size(self, width: int, height: int) -> None:
```

창의 크기를 설정합니다.

- **매개변수**:
  - `width` (int): 새 창 너비
  - `height` (int): 새 창 높이

```python
def set_position(self, x: int, y: int) -> None:
```

창의 위치를 설정합니다.

- **매개변수**:
  - `x` (int): 새 x 좌표
  - `y` (int): 새 y 좌표

```python
def set_frame(self, frame: bool) -> None:
```

창 프레임 표시 여부를 설정합니다.

- **매개변수**:
  - `frame` (bool): 프레임 표시 여부

```python
def set_context_menu(self, context_menu: bool) -> None:
```

컨텍스트 메뉴 활성화 여부를 설정합니다.

- **매개변수**:
  - `context_menu` (bool): 컨텍스트 메뉴 활성화 여부

```python
def set_dev_tools(self, enable: bool) -> None:
```

개발자 도구 활성화 여부를 설정합니다.

- **매개변수**:
  - `enable` (bool): 개발자 도구 활성화 여부

```python
def open_dev_tools(self) -> None:
```

개발자 도구 창을 엽니다.

```python
def get_window_properties(self) -> dict:
```

창의 속성을 반환합니다.

- **반환값**: dict: 창 속성을 포함하는 딕셔너리

```python
def get_id(self) -> str:
```

창의 ID를 반환합니다.

- **반환값**: str: 창 ID

```python
def hide(self) -> None:
```

창을 숨깁니다.

```python
def show(self) -> None:
```

창을 표시합니다.

```python
def focus(self) -> None:
```

창에 포커스를 줍니다.

```python
def show_and_focus(self) -> None:
```

창을 표시하고 포커스를 줍니다.

```python
def close(self) -> None:
```

창을 닫습니다.

```python
def toggle_fullscreen(self) -> None:
```

전체 화면 모드를 전환합니다.

```python
def minimize(self) -> None:
```

창을 최소화합니다.

```python
def maximize(self) -> None:
```

창을 최대화합니다.

```python
def unmaximize(self) -> None:
```

창을 이전 크기로 복원합니다.

```python
def capture(self, save_path: str) -> Optional[str]:
```

현재 창을 캡처합니다.

- **매개변수**:
  - `save_path` (str): 캡처한 이미지를 저장할 경로
- **반환값**:
  - Optional\[str]: 저장된 이미지 경로 또는 실패 시 None

```python
def add_shortcut(self, key_sequence: str, callback: Callable) -> QShortcut:
```

창에 키보드 단축키를 추가합니다.

- **매개변수**:
  - `key_sequence` (str): 단축키 시퀀스 (예: "Ctrl+C")
  - `callback` (Callable): 단축키가 눌렸을 때 실행할 함수
- **반환값**:
  - QShortcut: 생성된 QShortcut 객체

```python
def remove_shortcut(self, key_sequence: str) -> None:
```

창에서 키보드 단축키를 제거합니다.

- **매개변수**:
  - `key_sequence` (str): 제거할 단축키 시퀀스

```python
def get_all_shortcuts(self) -> dict:
```

창에 등록된 모든 단축키를 반환합니다.

- **반환값**:
  - dict: 단축키 시퀀스와 해당 QShortcut 객체를 포함하는 딕셔너리

```python
def emit(self, event_name: str, data: Optional[Dict] = None) -> None:
```

JavaScript 측으로 이벤트를 발생시킵니다.

- **매개변수**:
  - `event_name` (str): 이벤트 이름
  - `data` (Optional\[Dict]): 이벤트와 함께 전송할 데이터 (기본값: None)
