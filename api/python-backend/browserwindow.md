# BrowserWindow

## Overview

The BrowserWindow class is designed to manage browser windows within a Pyloid application. It extends PySide6's QMainWindow to provide additional functionality for creating and managing browser windows.

## Constructor

```python
def __init__(self, app, title: str = "pylon app", width: int = 800, height: int = 600, x: int = 200, y: int = 200, frame: bool = True, context_menu: bool = False, dev_tools: bool = False, js_apis: List[PylonAPI] = []):
```

Initializes a BrowserWindow object.

* **Parameters**:
  * `app`: Pyloid instance
  * `title` (str): Window title (default: "pylon app")
  * `width` (int): Window width (default: 800)
  * `height` (int): Window height (default: 600)
  * `x` (int): Window x-coordinate (default: 200)
  * `y` (int): Window y-coordinate (default: 200)
  * `frame` (bool): Whether to show window frame (default: True)
  * `context_menu` (bool): Whether to enable context menu (default: False)
  * `dev_tools` (bool): Whether to enable developer tools (default: False)
  * `js_apis` (List\[PyloidAPI]): List of JavaScript APIs to add (default: \[])

## Methods

```python
def load_file(self, file_path: str) -> None:
```

Loads a local HTML file into the web view.

* **Parameters**:
  * `file_path` (str): Path to the HTML file to load

```python
def load_url(self, url: str) -> None:
```

Loads the specified URL into the window.

* **Parameters**:
  * `url` (str): URL to load

```python
def set_title(self, title: str) -> None:
```

Sets the title of the window.

* **Parameters**:
  * `title` (str): New window title

```python
def set_size(self, width: int, height: int) -> None:
```

Sets the size of the window.

* **Parameters**:
  * `width` (int): New window width
  * `height` (int): New window height

```python
def set_position(self, x: int, y: int) -> None:
```

Sets the position of the window.

* **Parameters**:
  * `x` (int): New x-coordinate
  * `y` (int): New y-coordinate

```python
def set_frame(self, frame: bool) -> None:
```

Sets whether to show the window frame.

* **Parameters**:
  * `frame` (bool): Whether to show the frame

```python
def set_context_menu(self, context_menu: bool) -> None:
```

Sets whether to enable the context menu.

* **Parameters**:
  * `context_menu` (bool): Whether to enable the context menu

```python
def set_dev_tools(self, enable: bool) -> None:
```

Sets whether to enable developer tools.

* **Parameters**:
  * `enable` (bool): Whether to enable developer tools

```python
def open_dev_tools(self) -> None:
```

Opens the developer tools window.

```python
def get_window_properties(self) -> dict:
```

Returns the properties of the window.

* **Returns**: dict: A dictionary containing the window properties

```python
def get_id(self) -> str:
```

Returns the ID of the window.

* **Returns**: str: The window ID

```python
def hide(self) -> None:
```

Hides the window.

```python
def show(self) -> None:
```

Shows the window.

```python
def focus(self) -> None:
```

Gives focus to the window.

```python
def show_and_focus(self) -> None:
```

Shows the window and gives it focus.

```python
def close(self) -> None:
```

Closes the window.

```python
def toggle_fullscreen(self) -> None:
```

Toggles fullscreen mode.

```python
def minimize(self) -> None:
```

Minimizes the window.

```python
def maximize(self) -> None:
```

Maximizes the window.

```python
def unmaximize(self) -> None:
```

Restores the window to its previous size.

```python
def capture(self, save_path: str) -> Optional[str]:
```

Captures the current window.

* **Parameters**:
  * `save_path` (str): Path to save the captured image
* **Returns**:
  * Optional\[str]: Path to the saved image or None if failed

```python
def add_shortcut(self, key_sequence: str, callback: Callable) -> QShortcut:
```

Adds a keyboard shortcut to the window.

* **Parameters**:
  * `key_sequence` (str): Shortcut key sequence (e.g., "Ctrl+C")
  * `callback` (Callable): Function to execute when the shortcut is pressed
* **Returns**:
  * QShortcut: The created QShortcut object

```python
def remove_shortcut(self, key_sequence: str) -> None:
```

Removes a keyboard shortcut from the window.

* **Parameters**:
  * `key_sequence` (str): Shortcut key sequence to remove

```python
def get_all_shortcuts(self) -> dict:
```

Returns all shortcuts registered to the window.

* **Returns**:
  * dict: A dictionary containing shortcut sequences and their QShortcut objects

```python
def emit(self, event_name: str, data: Optional[Dict] = None) -> None:
```

Emits an event to the JavaScript side.

* **Parameters**:
  * `event_name` (str): Name of the event
  * `data` (Optional\[Dict]): Data to be sent with the event (default: None)
