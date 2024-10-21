# Pyloid

Pyloid는 PySide6의 QApplication을 확장한 애플리케이션 클래스로, 데스크톱 애플리케이션 개발을 위한 다양한 기능을 제공합니다.

## 초기화

```python
class Pyloid(QApplication):
    def __init__(self, app_name: str, single_instance: bool = True):
        # ...
```

**app_name**은 자동 시작 / 단일 인스턴스의 키 이름으로 사용됩니다.

### 매개변수

- `app_name` (str): 애플리케이션 이름 (자동 시작 / 단일 인스턴스의 키 이름으로 사용됩니다.)
- `single_instance` (bool): 단일 인스턴스 모드를 활성화합니다. 기본값은 True입니다.

## 주요 메서드

### 창 관리

#### create_window

```python
def create_window(self, title: str = "pylon app", width: int = 800, height: int = 600, x: int = 200, y: int = 200, frame: bool = True, context_menu: bool = False, dev_tools: bool = False, js_apis: List[PylonAPI] = []) -> BrowserWindow:
```

새 브라우저 창을 생성합니다.

**매개변수**

- `title` (str): 창 제목. 기본값은 "pylon app"입니다.
- `width` (int): 창 너비. 기본값은 800입니다.
- `height` (int): 창 높이. 기본값은 600입니다.
- `x` (int): 창의 x 좌표. 기본값은 200입니다.
- `y` (int): 창의 y 좌표. 기본값은 200입니다.
- `frame` (bool): 창 프레임 표시 여부. 기본값은 True입니다.
- `context_menu` (bool): 컨텍스트 메뉴 활성화 여부. 기본값은 False입니다.
- `dev_tools` (bool): 개발자 도구 활성화 여부. 기본값은 False입니다.
- `js_apis` (List[PylonAPI]): JavaScript API 목록. 기본값은 빈 리스트입니다.

**반환값**

- `BrowserWindow`: 생성된 브라우저 창 객체.

#### get_windows

```python
def get_windows(self) -> List[BrowserWindow]:
```

모든 브라우저 창의 목록을 반환합니다.

**반환값**

- `List[BrowserWindow]`: 브라우저 창 객체 목록.

#### show_main_window

```python
def show_main_window(self):
```

메인 창을 표시합니다.

#### focus_main_window

```python
def focus_main_window(self):
```

메인 창에 포커스를 맞춥니다.

#### show_and_focus_main_window

```python
def show_and_focus_main_window(self):
```

메인 창을 표시하고 포커스를 맞춥니다.

#### close_all_windows

```python
def close_all_windows(self):
```

모든 창을 닫습니다.

#### quit

```python
def quit(self):
```

애플리케이션을 종료합니다.

### ID별 창 관리

#### get_window_by_id

```python
def get_window_by_id(self, window_id: str) -> Optional[BrowserWindow]:
```

ID로 창을 검색합니다.

**매개변수**

- `window_id` (str): 검색할 창의 ID.

**반환값**

- `Optional[BrowserWindow]`: 찾은 창 객체 또는 None.

#### hide_window_by_id

```python
def hide_window_by_id(self, window_id: str):
```

ID로 창을 숨깁니다.

**매개변수**

- `window_id` (str): 숨길 창의 ID.

#### show_window_by_id

```python
def show_window_by_id(self, window_id: str):
```

ID로 창을 표시하고 포커스를 맞춥니다.

**매개변수**

- `window_id` (str): 표시할 창의 ID.

#### close_window_by_id

```python
def close_window_by_id(self, window_id: str):
```

ID로 창을 닫습니다.

**매개변수**

- `window_id` (str): 닫을 창의 ID.

#### toggle_fullscreen_by_id

```python
def toggle_fullscreen_by_id(self, window_id: str):
```

ID로 창의 전체 화면 모드를 전환합니다.

**매개변수**

- `window_id` (str): 전체 화면 모드를 전환할 창의 ID.

#### minimize_window_by_id

```python
def minimize_window_by_id(self, window_id: str):
```

ID로 창을 최소화합니다.

**매개변수**

- `window_id` (str): 최소화할 창의 ID.

#### maximize_window_by_id

```python
def maximize_window_by_id(self, window_id: str):
```

ID로 창을 최대화합니다.

**매개변수**

- `window_id` (str): 최대화할 창의 ID.

#### unmaximize_window_by_id

```python
def unmaximize_window_by_id(self, window_id: str):
```

ID로 창의 최대화를 해제합니다.

**매개변수**

- `window_id` (str): 최대화를 해제할 창의 ID.

#### capture_window_by_id

```python
def capture_window_by_id(self, window_id: str, save_path: str) -> Optional[str]:
```

ID로 창을 캡처하고 이미지를 저장합니다.

**매개변수**

- `window_id` (str): 캡처할 창의 ID.
- `save_path` (str): 캡처한 이미지를 저장할 경로.

**반환값**

- `Optional[str]`: 저장된 이미지 파일 경로 또는 None (실패 시).

### 시스템 트레이

#### run_tray

```python
def run_tray(self):
```

시스템 트레이 아이콘과 메뉴를 설정합니다.

#### set_tray_actions

```python
def set_tray_actions(self, actions):
```

트레이 아이콘 활성화 동작을 설정합니다.

**매개변수**

- `actions` (Dict[QSystemTrayIcon.ActivationReason, Callable]): 활성화 이유와 콜백 함수의 딕셔너리.

#### show_notification

```python
def show_notification(self, title: str, message: str):
```

시스템 트레이 알림을 표시합니다.

**매개변수**

- `title` (str): 알림 제목.
- `message` (str): 알림 내용.

### 모니터 정보

#### get_all_monitors

```python
def get_all_monitors(self) -> List[Monitor]:
```

연결된 모든 모니터의 정보를 반환합니다.

**반환값**

- `List[Monitor]`: Monitor 객체 목록.

#### get_primary_monitor

```python
def get_primary_monitor(self) -> Monitor:
```

주 모니터의 정보를 반환합니다.

**반환값**

- `Monitor`: 주 모니터의 Monitor 객체.

### 클립보드

#### copy_to_clipboard

```python
def copy_to_clipboard(self, text: str):
```

텍스트를 클립보드에 복사합니다.

**매개변수**

- `text` (str): 복사할 텍스트.

#### get_clipboard_text

```python
def get_clipboard_text(self) -> str:
```

클립보드에서 텍스트를 가져옵니다.

**반환값**

- `str`: 클립보드의 텍스트.

#### set_clipboard_image

```python
def set_clipboard_image(self, image: Union[str, bytes, os.PathLike]):
```

이미지를 클립보드에 복사합니다.

**매개변수**

- `image` (Union[str, bytes, os.PathLike]): 복사할 이미지 파일 경로 또는 바이트 데이터.

#### get_clipboard_image

```python
def get_clipboard_image(self) -> Optional[QImage]:
```

클립보드에서 이미지를 가져옵니다.

**반환값**

- `Optional[QImage]`: 클립보드의 이미지 또는 None (이미지가 없는 경우).

### 자동 시작

#### set_auto_start

```python
def set_auto_start(self, enable: bool):
```

시스템 시작 시 애플리케이션을 자동으로 시작하도록 설정합니다.

**매개변수**

- `enable` (bool): True로 설정하면 자동 시작을 활성화하고, False로 설정하면 비활성화합니다.

**참고**

- `set_auto_start(True)`는 프로덕션 환경에서만 작동합니다.
- `set_auto_start(False)`는 프로덕션 및 비프로덕션 환경 모두에서 작동합니다.
- 비프로덕션 환경에서 `set_auto_start(True)`를 호출하면 경고 메시지가 출력되고 None을 반환합니다.

**반환값**

- `bool`: 자동 시작이 성공적으로 활성화되면 True, 비활성화되면 False, 현재 환경에서 지원되지 않으면 None.

#### is_auto_start

```python
def is_auto_start(self):
```

애플리케이션이 시스템 시작 시 자동으로 시작되도록 설정되어 있는지 확인합니다.

**반환값**

- `bool`: 자동 시작이 활성화되어 있으면 True, 그렇지 않으면 False.

### 기타

#### set_icon

```python
def set_icon(self, icon_path: str):
```

애플리케이션 아이콘을 설정합니다.

**매개변수**

- `icon_path` (str): 아이콘 파일 경로.

#### set_tray_icon

```python
def set_tray_icon(self, tray_icon_path: str):
```

트레이 아이콘을 설정합니다.

**매개변수**

- `tray_icon_path` (str): 트레이 아이콘 파일 경로.

#### set_tray_menu_items

```python
def set_tray_menu_items(self, tray_menu_items: Dict[str, Callable]):
```

트레이 메뉴 항목을 설정합니다.

**매개변수**

- `tray_menu_items` (Dict[str, Callable]): 메뉴 항목 레이블과 콜백 함수의 딕셔너리.

#### run

```python
def run(self):
```

애플리케이션 이벤트 루프를 실행합니다. 이 메서드는 스크립트의 마지막에 실행되어야 합니다.
