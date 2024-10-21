# Monitor

## Overview

The Monitor class provides functionality to manage and manipulate information about computer monitors. This class uses PySide6's QScreen object to access various properties and functions of the monitor.

## Constructor

```python
def __init__(self, index: int, screen: QScreen):
```

Initializes a Monitor object.

* **Parameters**:
  * `index` (int): Index of the monitor
  * `screen` (QScreen): QScreen object corresponding to the monitor

## Methods

```python
def capture(self, save_path: str, x: Optional[int] = None, y: Optional[int] = None, width: Optional[int] = None, height: Optional[int] = None) -> Optional[str]:
```

Captures the monitor screen.

* **Parameters**:
  * `save_path` (str): Path to save the captured image
  * `x` (Optional\[int]): Starting x-coordinate for capture (default: None)
  * `y` (Optional\[int]): Starting y-coordinate for capture (default: None)
  * `width` (Optional\[int]): Width of the area to capture (default: None)
  * `height` (Optional\[int]): Height of the area to capture (default: None)
* **Returns**:
  * str: Path of the saved image
  * None: If capture fails

```python
def info(self) -> dict:
```

Returns a dictionary containing all information about the monitor.

* **Returns**: dict: Dictionary containing monitor information

```python
def is_primary(self) -> bool:
```

Checks if the current monitor is the primary monitor.

* **Returns**: bool: True if primary monitor, False otherwise

```python
def size(self) -> dict:
```

Returns the size of the monitor.

* **Returns**: dict: Dictionary with 'width' and 'height' keys

```python
def geometry(self) -> dict:
```

Returns the geometry information of the monitor.

* **Returns**: dict: Dictionary with 'x', 'y', 'width', 'height' keys

```python
def available_geometry(self) -> dict:
```

Returns the geometry information of the available monitor area.

* **Returns**: dict: Dictionary with 'x', 'y', 'width', 'height' keys

```python
def available_size(self) -> dict:
```

Returns the size of the available monitor area.

* **Returns**: dict: Dictionary with 'width' and 'height' keys

```python
def virtual_geometry(self) -> dict:
```

Returns the geometry information of the monitor in virtual desktop.

* **Returns**: dict: Dictionary with 'x', 'y', 'width', 'height' keys

```python
def virtual_size(self) -> dict:
```

Returns the size of the monitor in virtual desktop.

* **Returns**: dict: Dictionary with 'width' and 'height' keys

```python
def available_virtual_geometry(self) -> dict:
```

Returns the geometry information of the available virtual desktop area.

* **Returns**: dict: Dictionary with 'x', 'y', 'width', 'height' keys

```python
def available_virtual_size(self) -> dict:
```

Returns the size of the available virtual desktop area.

* **Returns**: dict: Dictionary with 'width' and 'height' keys

```python
def physical_size(self) -> dict:
```

Returns the physical size of the monitor.

* **Returns**: dict: Dictionary with 'width' and 'height' keys

```python
def depth(self) -> int:
```

Returns the color depth of the monitor.

* **Returns**: int: Color depth of the monitor

```python
def device_pixel_ratio(self) -> float:
```

Returns the device pixel ratio of the monitor.

* **Returns**: float: Device pixel ratio

```python
def logical_dots_per_inch(self) -> float:
```

Returns the logical DPI of the monitor.

* **Returns**: float: Logical DPI

```python
def logical_dots_per_inch_x(self) -> float:
```

Returns the horizontal logical DPI of the monitor.

* **Returns**: float: Horizontal logical DPI

```python
def logical_dots_per_inch_y(self) -> float:
```

Returns the vertical logical DPI of the monitor.

* **Returns**: float: Vertical logical DPI

```python
def orientation(self) -> str:
```

Returns the orientation of the monitor.

* **Returns**: str: Monitor orientation ('Portrait', 'Landscape', etc.)

```python
def physical_dots_per_inch(self) -> float:
```

Returns the physical DPI of the monitor.

* **Returns**: float: Physical DPI

```python
def physical_dots_per_inch_x(self) -> float:
```

Returns the horizontal physical DPI of the monitor.

* **Returns**: float: Horizontal physical DPI

```python
def physical_dots_per_inch_y(self) -> float:
```

Returns the vertical physical DPI of the monitor.

* **Returns**: float: Vertical physical DPI

```python
def refresh_rate(self) -> float:
```

Returns the refresh rate of the monitor.

* **Returns**: float: Monitor refresh rate (Hz)

```python
def manufacturer(self) -> str:
```

Returns the manufacturer of the monitor.

* **Returns**: str: Monitor manufacturer name

```python
def model(self) -> str:
```

Returns the model of the monitor.

* **Returns**: str: Monitor model name

```python
def name(self) -> str:
```

Returns the name of the monitor.

* **Returns**: str: Monitor name

```python
def serial_number(self) -> str:
```

Returns the serial number of the monitor.

* **Returns**: str: Monitor serial number

```python
def geometry_changed(self, callback: Callable):
```

Sets a callback for monitor geometry change events.

* **Parameters**:
  * `callback` (Callable): Function to be called when geometry changes

```python
def orientation_changed(self, callback: Callable):
```

Sets a callback for monitor orientation change events.

* **Parameters**:
  * `callback` (Callable): Function to be called when orientation changes

```python
def refresh_rate_changed(self, callback: Callable):
```

Sets a callback for monitor refresh rate change events.

* **Parameters**:
  * `callback` (Callable): Function to be called when refresh rate changes
