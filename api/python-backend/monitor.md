# Monitor

## 개요

Monitor 클래스는 컴퓨터 모니터에 대한 정보를 관리하고 조작하는 기능을 제공합니다. 이 클래스는 PySide6의 QScreen 객체를 사용하여 모니터의 다양한 속성과 기능에 접근합니다.

## 생성자

```python
def __init__(self, index: int, screen: QScreen):
```

Monitor 객체를 초기화합니다.

- **매개변수**:
  - `index` (int): 모니터의 인덱스
  - `screen` (QScreen): 모니터에 해당하는 QScreen 객체

## 메서드

```python
def capture(self, save_path: str, x: Optional[int] = None, y: Optional[int] = None, width: Optional[int] = None, height: Optional[int] = None) -> Optional[str]:
```

모니터 화면을 캡처합니다.

- **매개변수**:
  - `save_path` (str): 캡처된 이미지를 저장할 경로
  - `x` (Optional\[int]): 캡처 시작 x 좌표 (기본값: None)
  - `y` (Optional\[int]): 캡처 시작 y 좌표 (기본값: None)
  - `width` (Optional\[int]): 캡처할 영역의 너비 (기본값: None)
  - `height` (Optional\[int]): 캡처할 영역의 높이 (기본값: None)
- **반환값**:
  - str: 저장된 이미지의 경로
  - None: 캡처 실패 시

```python
def info(self) -> dict:
```

모니터에 대한 모든 정보를 포함하는 딕셔너리를 반환합니다.

- **반환값**: dict: 모니터 정보를 포함하는 딕셔너리

```python
def is_primary(self) -> bool:
```

현재 모니터가 주 모니터인지 확인합니다.

- **반환값**: bool: 주 모니터인 경우 True, 그렇지 않으면 False

```python
def size(self) -> dict:
```

모니터의 크기를 반환합니다.

- **반환값**: dict: 'width'와 'height' 키를 가진 딕셔너리

```python
def geometry(self) -> dict:
```

모니터의 기하 정보를 반환합니다.

- **반환값**: dict: 'x', 'y', 'width', 'height' 키를 가진 딕셔너리

```python
def available_geometry(self) -> dict:
```

사용 가능한 모니터 영역의 기하 정보를 반환합니다.

- **반환값**: dict: 'x', 'y', 'width', 'height' 키를 가진 딕셔너리

```python
def available_size(self) -> dict:
```

사용 가능한 모니터 영역의 크기를 반환합니다.

- **반환값**: dict: 'width'와 'height' 키를 가진 딕셔너리

```python
def virtual_geometry(self) -> dict:
```

가상 데스크톱에서의 모니터 기하 정보를 반환합니다.

- **반환값**: dict: 'x', 'y', 'width', 'height' 키를 가진 딕셔너리

```python
def virtual_size(self) -> dict:
```

가상 데스크톱에서의 모니터 크기를 반환합니다.

- **반환값**: dict: 'width'와 'height' 키를 가진 딕셔너리

```python
def available_virtual_geometry(self) -> dict:
```

사용 가능한 가상 데스크톱 영역의 기하 정보를 반환합니다.

- **반환값**: dict: 'x', 'y', 'width', 'height' 키를 가진 딕셔너리

```python
def available_virtual_size(self) -> dict:
```

사용 가능한 가상 데스크톱 영역의 크기를 반환합니다.

- **반환값**: dict: 'width'와 'height' 키를 가진 딕셔너리

```python
def physical_size(self) -> dict:
```

모니터의 물리적 크기를 반환합니다.

- **반환값**: dict: 'width'와 'height' 키를 가진 딕셔너리

```python
def depth(self) -> int:
```

모니터의 색 깊이를 반환합니다.

- **반환값**: int: 모니터의 색 깊이

```python
def device_pixel_ratio(self) -> float:
```

모니터의 장치 픽셀 비율을 반환합니다.

- **반환값**: float: 장치 픽셀 비율

```python
def logical_dots_per_inch(self) -> float:
```

모니터의 논리적 DPI를 반환합니다.

- **반환값**: float: 논리적 DPI

```python
def logical_dots_per_inch_x(self) -> float:
```

모니터의 수평 논리적 DPI를 반환합니다.

- **반환값**: float: 수평 논리적 DPI

```python
def logical_dots_per_inch_y(self) -> float:
```

모니터의 수직 논리적 DPI를 반환합니다.

- **반환값**: float: 수직 논리적 DPI

```python
def orientation(self) -> str:
```

모니터의 방향을 반환합니다.

- **반환값**: str: 모니터 방향 ('Portrait', 'Landscape' 등)

```python
def physical_dots_per_inch(self) -> float:
```

모니터의 물리적 DPI를 반환합니다.

- **반환값**: float: 물리적 DPI

```python
def physical_dots_per_inch_x(self) -> float:
```

모니터의 수평 물리적 DPI를 반환합니다.

- **반환값**: float: 수평 물리적 DPI

```python
def physical_dots_per_inch_y(self) -> float:
```

모니터의 수직 물리적 DPI를 반환합니다.

- **반환값**: float: 수직 물리적 DPI

```python
def refresh_rate(self) -> float:
```

모니터의 주사율을 반환합니다.

- **반환값**: float: 모니터 주사율 (Hz)

```python
def manufacturer(self) -> str:
```

모니터의 제조사를 반환합니다.

- **반환값**: str: 모니터 제조사 이름

```python
def model(self) -> str:
```

모니터의 모델을 반환합니다.

- **반환값**: str: 모니터 모델 이름

```python
def name(self) -> str:
```

모니터의 이름을 반환합니다.

- **반환값**: str: 모니터 이름

```python
def serial_number(self) -> str:
```

모니터의 일련번호를 반환합니다.

- **반환값**: str: 모니터 일련번호

```python
def geometry_changed(self, callback: Callable):
```

모니터 기하 변경 이벤트에 대한 콜백을 설정합니다.

- **매개변수**:
  - `callback` (Callable): 기하가 변경될 때 호출될 함수

```python
def orientation_changed(self, callback: Callable):
```

모니터 방향 변경 이벤트에 대한 콜백을 설정합니다.

- **매개변수**:
  - `callback` (Callable): 방향이 변경될 때 호출될 함수

```python
def refresh_rate_changed(self, callback: Callable):
```

모니터 주사율 변경 이벤트에 대한 콜백을 설정합니다.

- **매개변수**:
  - `callback` (Callable): 주사율이 변경될 때 호출될 함수
