# 데스크탑 모니터

## 개요

`app.get_primary_monitor()` 또는 `app.get_all_monitors()` 메서드를 사용하여 모니터 객체를 얻을 수 있습니다. 이 모니터 객체를 통해 다양한 기능을 수행할 수 있으며, `Monitor` 객체의 여러 메서드를 활용하여 모니터의 속성 및 상태를 조회하거나 변경할 수 있습니다.

## 메서드

#### `capture(save_path: str, x: Optional[int] = None, y: Optional[int] = None, width: Optional[int] = None, height: Optional[int] = None)`

- **설명**: 전체 데스크탑 화면을 캡처합니다.
- **매개변수**:
  - `save_path` (str): 캡처된 이미지를 저장할 경로.
  - `x`, `y`, `width`, `height` (int, optional): 캡처할 영역의 좌표 및 크기.
- **반환값**: 저장된 이미지의 경로를 반환합니다. 오류 발생 시 `None`을 반환합니다.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  save_path = monitor.capture("screenshot.png")
  print(f"Screenshot saved at: {save_path}")
  ```

#### `info() -> dict[str, Any]`

- **설명**: 모니터에 대한 모든 정보를 반환합니다.
- **반환값**: 모니터 모든 정보가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  info = monitor.info()
  print("Monitor Info:", info)
  ```

#### `is_primary() -> bool`

- **설명**: 모니터가 기본 모니터인지 확인합니다.
- **반환값**: 기본 모니터이면 `True`, 아니면 `False`.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_all_monitors()[1]
  is_primary = monitor.is_primary()
  print(f"Is primary monitor: {is_primary}") # False
  ```

#### `size() -> dict[str, int]`

- **설명**: 모니터의 크기를 반환합니다.
- **반환값**: 모니터의 너비와 높이가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  size = monitor.size()
  print("Monitor Size:", size)
  ```

#### `geometry() -> dict[str, int]`

- **설명**: 모니터의 x, y, width, height 정보를 반환합니다.
- **반환값**: 모니터의 x, y, width, height 정보가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  geometry = monitor.geometry()
  print("Monitor Geometry:", geometry)
  ```

#### `available_geometry() -> dict[str, int]`

- **설명**: 모니터의 사용 가능한 x, y, width, height 정보를 반환합니다.
- **반환값**: 시스템 UI 요소를 제외한 모니터의 x, y, width, height 정보가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  available_geometry = monitor.available_geometry()
  print("Available Geometry:", available_geometry)
  ```

#### `available_size() -> dict[str, int]`

- **설명**: 모니터의 사용 가능한 크기를 반환합니다.
- **반환값**: 시스템 UI 요소를 제외한 모니터의 너비와 높이가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  available_size = monitor.available_size()
  print("Available Size:", available_size)
  ```

#### `virtual_geometry() -> dict[str, int]`

- **설명**: 모니터의 가상 x, y, width, height 정보를 반환합니다.
- **반환값**: 다중 모니터 설정에서 모든 모니터의 결합된 x, y, width, height 정보가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  virtual_geometry = monitor.virtual_geometry()
  print("Virtual Geometry:", virtual_geometry)
  ```

#### `virtual_size() -> dict[str, int]`

- **설명**: 모니터의 가상 크기를 반환합니다.
- **반환값**: 다중 모니터 설정에서 모든 모니터의 결합된 너비와 높이가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  virtual_size = monitor.virtual_size()
  print("Virtual Size:", virtual_size)
  ```

#### `available_virtual_geometry() -> dict[str, int]`

- **설명**: 모니터의 사용 가능한 가상 x, y, width, height 정보를 반환합니다.
- **반환값**: 시스템 UI 요소를 제외한 가상 x, y, width, height 정보가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  available_virtual_geometry = monitor.available_virtual_geometry()
  print("Available Virtual Geometry:", available_virtual_geometry)
  ```

#### `available_virtual_size() -> dict[str, int]`

- **설명**: 모니터의 사용 가능한 가상 크기를 반환합니다.
- **반환값**: 시스템 UI 요소를 제외한 가상 크기가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  available_virtual_size = monitor.available_virtual_size()
  print("Available Virtual Size:", available_virtual_size)
  ```

#### `physical_size() -> dict[str, float]`

- **설명**: 모니터의 물리적 크기를 반환합니다.
- **반환값**: 모니터의 실제 물리적 너비와 높이가 담긴 딕셔너리.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  physical_size = monitor.physical_size()
  print("Physical Size:", physical_size)
  ```

#### `depth() -> int`

- **설명**: 모니터의 색상 깊이를 반환합니다.
- **반환값**: 모니터의 색상 깊이.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  depth = monitor.depth()
  print("Color Depth:", depth)
  ```

#### `device_pixel_ratio() -> float`

- **설명**: 모니터의 장치 픽셀 비율을 반환합니다.
- **반환값**: 모니터의 장치 픽셀 비율.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  device_pixel_ratio = monitor.device_pixel_ratio()
  print("Device Pixel Ratio:", device_pixel_ratio)
  ```

#### `logical_dots_per_inch() -> float`

- **설명**: 모니터의 논리적 DPI를 반환합니다.
- **반환값**: 모니터의 논리적 DPI.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  logical_dpi = monitor.logical_dots_per_inch()
  print("Logical DPI:", logical_dpi)
  ```

#### `logical_dots_per_inch_x() -> float`

- **설명**: 모니터의 X축 논리적 DPI를 반환합니다.
- **반환값**: 모니터의 X축 논리적 DPI.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  logical_dpi_x = monitor.logical_dots_per_inch_x()
  print("Logical DPI X:", logical_dpi_x)
  ```

#### `logical_dots_per_inch_y() -> float`

- **설명**: 모니터의 Y축 논리적 DPI를 반환합니다.
- **반환값**: 모니터의 Y축 논리적 DPI.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  logical_dpi_y = monitor.logical_dots_per_inch_y()
  print("Logical DPI Y:", logical_dpi_y)
  ```

#### `orientation() -> str`

- **설명**: 모니터의 방향을 반환합니다.
- **반환값**: 모니터의 방향.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  orientation = monitor.orientation()
  print("Orientation:", orientation)
  ```

#### `physical_dots_per_inch() -> float`

- **설명**: 모니터의 물리적 DPI를 반환합니다.
- **반환값**: 모니터의 물리적 DPI.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  physical_dpi = monitor.physical_dots_per_inch()
  print("Physical DPI:", physical_dpi)
  ```

#### `physical_dots_per_inch_x() -> float`

- **설명**: 모니터의 X축 물리적 DPI를 반환합니다.
- **반환값**: 모니터의 X축 물리적 DPI.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  physical_dpi_x = monitor.physical_dots_per_inch_x()
  print("Physical DPI X:", physical_dpi_x)
  ```

#### `physical_dots_per_inch_y() -> float`

- **설명**: 모니터의 Y축 물리적 DPI를 반환합니다.
- **반환값**: 모니터의 Y축 물리적 DPI.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  physical_dpi_y = monitor.physical_dots_per_inch_y()
  print("Physical DPI Y:", physical_dpi_y)
  ```

#### `refresh_rate() -> float`

- **설명**: 모니터의 새로 고침 빈도를 반환합니다.
- **반환값**: 모니터의 새로 고침 빈도.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  refresh_rate = monitor.refresh_rate()
  print("Refresh Rate:", refresh_rate)
  ```

#### `manufacturer() -> str`

- **설명**: 모니터의 제조사를 반환합니다.
- **반환값**: 모니터의 제조사.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  manufacturer = monitor.manufacturer()
  print("Manufacturer:", manufacturer)
  ```

#### `model() -> str`

- **설명**: 모니터의 모델을 반환합니다.
- **반환값**: 모니터의 모델.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  model = monitor.model()
  print("Model:", model)
  ```

#### `name() -> str`

- **설명**: 모니터의 이름을 반환합니다.
- **반환값**: 모니터의 이름.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  name = monitor.name()
  print("Name:", name)
  ```

#### `serial_number() -> str`

- **설명**: 모니터의 일련 번호를 반환합니다.
- **반환값**: 모니터의 일련 번호.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  monitor = app.get_primary_monitor()
  serial_number = monitor.serial_number()
  print("Serial Number:", serial_number)
  ```

#### `geometry_changed(callback: Callable)`

- **설명**: 모니터의 기하학적 정보가 변경될 때 호출되는 콜백을 등록합니다.
- **매개변수**:
  - `callback` (Callable): 기하학적 정보 변경 시 호출될 함수.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  def on_geometry_changed():
      print("Geometry changed!")
  monitor = app.get_primary_monitor()
  monitor.geometry_changed(on_geometry_changed)
  ```

#### `orientation_changed(callback: Callable)`

- **설명**: 모니터의 방향이 변경될 때 호출되는 콜백을 등록합니다.
- **매개변수**:
  - `callback` (Callable): 방향 변경 시 호출될 함수.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  def on_orientation_changed():
      print("Orientation changed!")
  monitor = app.get_primary_monitor()
  monitor.orientation_changed(on_orientation_changed)
  ```

#### `refresh_rate_changed(callback: Callable)`

- **설명**: 모니터의 새로 고침 빈도가 변경될 때 호출되는 콜백을 등록합니다.
- **매개변수**:
  - `callback` (Callable): 새로 고침 빈도 변경 시 호출될 함수.
- **예제**:
  ```python
  app = Pyloid("Pyloid-App")
  def on_refresh_rate_changed():
      print("Refresh rate changed!")
  monitor = app.get_primary_monitor()
  monitor.refresh_rate_changed(on_refresh_rate_changed)
  ```

이 외에도 `Monitor` 클래스는 다양한 모니터 속성 조회 메서드를 제공합니다. 각 메서드는 모니터의 특정 속성을 반환하며, 사용 예제는 위와 유사합니다.
