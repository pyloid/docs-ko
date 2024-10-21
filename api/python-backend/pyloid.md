# Pyloid

PylonApp is an application class that extends PySide6's QApplication, providing various features for desktop application development.

## Initialization

```python
class Pyloid(QApplication):
    def __init__(self, app_name: str, single_instance: bool = True, icon_path: str = None, tray_icon_path: str = None):
        # ...
```

**app\_name** is used as the key name when auto-starting.

### Parameters

* `single_instance` (bool): Activate single instance mode. Default is True.
* `icon_path` (str, optional): Application icon file path.
* `tray_icon_path` (str, optional): System tray icon file path.

## Main Methods

### Window Management

#### create\_window

```python
def create_window(self, title: str = "pylon app", width: int = 800, height: int = 600, x: int = 200, y: int = 200, frame: bool = True, context_menu: bool = False, dev_tools: bool = False, js_apis: List[PylonAPI] = []) -> BrowserWindow:
```

Creates a new browser window.

**Parameters**

* `title` (str): Window title. Default is "pylon app".
* `width` (int): Window width. Default is 800.
* `height` (int): Window height. Default is 600.
* `x` (int): Window x coordinate. Default is 200.
* `y` (int): Window y coordinate. Default is 200.
* `frame` (bool): Show window frame. Default is True.
* `context_menu` (bool): Enable context menu. Default is False.
* `dev_tools` (bool): Enable developer tools. Default is False.
* `js_apis` (List\[PylonAPI]): List of JavaScript APIs. Default is an empty list.

**Returns**

* `BrowserWindow`: Created browser window object.

#### get\_windows

```python
def get_windows(self) -> List[BrowserWindow]:
```

Returns a list of all browser windows.

**Returns**

* `List[BrowserWindow]`: List of browser window objects.

#### show\_main\_window

```python
def show_main_window(self):
```

Shows the main window.

#### focus\_main\_window

```python
def focus_main_window(self):
```

Focuses the main window.

#### show\_and\_focus\_main\_window

```python
def show_and_focus_main_window(self):
```

Shows and focuses the main window.

#### close\_all\_windows

```python
def close_all_windows(self):
```

Closes all windows.

#### quit

```python
def quit(self):
```

Quits the application.

### Window Management by ID

#### get\_window\_by\_id

```python
def get_window_by_id(self, window_id: str) -> Optional[BrowserWindow]:
```

Searches for a window by ID.

**Parameters**

* `window_id` (str): ID of the window to search for.

**Returns**

* `Optional[BrowserWindow]`: Found window object or None.

#### hide\_window\_by\_id

```python
def hide_window_by_id(self, window_id: str):
```

Hides a window by ID.

**Parameters**

* `window_id` (str): ID of the window to hide.

#### show\_window\_by\_id

```python
def show_window_by_id(self, window_id: str):
```

Shows and focuses a window by ID.

**Parameters**

* `window_id` (str): ID of the window to show.

#### close\_window\_by\_id

```python
def close_window_by_id(self, window_id: str):
```

Closes a window by ID.

**Parameters**

* `window_id` (str): ID of the window to close.

#### toggle\_fullscreen\_by\_id

```python
def toggle_fullscreen_by_id(self, window_id: str):
```

Toggles fullscreen mode for a window by ID.

**Parameters**

* `window_id` (str): ID of the window to toggle fullscreen.

#### minimize\_window\_by\_id

```python
def minimize_window_by_id(self, window_id: str):
```

Minimizes a window by ID.

**Parameters**

* `window_id` (str): ID of the window to minimize.

#### maximize\_window\_by\_id

```python
def maximize_window_by_id(self, window_id: str):
```

Maximizes a window by ID.

**Parameters**

* `window_id` (str): ID of the window to maximize.

#### unmaximize\_window\_by\_id

```python
def unmaximize_window_by_id(self, window_id: str):
```

Unmaximizes a window by ID.

**Parameters**

* `window_id` (str): ID of the window to unmaximize.

#### capture\_window\_by\_id

```python
def capture_window_by_id(self, window_id: str, save_path: str) -> Optional[str]:
```

Captures a window by ID and saves the image.

**Parameters**

* `window_id` (str): ID of the window to capture.
* `save_path` (str): Path to save the captured image.

**Returns**

* `Optional[str]`: Saved image file path or None (if failed).

### System Tray

#### run\_tray

```python
def run_tray(self):
```

Sets up the system tray icon and menu.

#### set\_tray\_actions

```python
def set_tray_actions(self, actions):
```

Sets the tray icon activation actions.

**Parameters**

* `actions` (Dict\[QSystemTrayIcon.ActivationReason, Callable]): Dictionary of activation reasons and callback functions.

#### show\_notification

```python
def show_notification(self, title: str, message: str):
```

Displays a system tray notification.

**Parameters**

* `title` (str): Notification title.
* `message` (str): Notification content.

### Monitor Information

#### get\_all\_monitors

```python
def get_all_monitors(self) -> List[Monitor]:
```

Returns information for all connected monitors.

**Returns**

* `List[Monitor]`: List of Monitor objects.

#### get\_primary\_monitor

```python
def get_primary_monitor(self) -> Monitor:
```

Returns information for the primary monitor.

**Returns**

* `Monitor`: Monitor object for the primary monitor.

### Clipboard

#### copy\_to\_clipboard

```python
def copy_to_clipboard(self, text: str):
```

Copies text to the clipboard.

**Parameters**

* `text` (str): Text to copy.

#### get\_clipboard\_text

```python
def get_clipboard_text(self) -> str:
```

Retrieves text from the clipboard.

**Returns**

* `str`: Text from the clipboard.

#### set\_clipboard\_image

```python
def set_clipboard_image(self, image: Union[str, bytes, os.PathLike]):
```

Copies an image to the clipboard.

**Parameters**

* `image` (Union\[str, bytes, os.PathLike]): Image file path or byte data to copy.

#### get\_clipboard\_image

```python
def get_clipboard_image(self) -> Optional[QImage]:
```

Retrieves an image from the clipboard.

**Returns**

* `Optional[QImage]`: Image from the clipboard or None (if no image).

### Autostart

#### set\_auto\_start

```python
def set_auto_start(self, enable: bool):
```

Sets the application to start automatically with the system.

**Parameters**

* `enable` (bool): True to enable auto-start, False to disable.

**Notes**

* `set_auto_start(True)` only works in production environment.
* `set_auto_start(False)` works in both production and non-production environments.
* In non-production environment, calling `set_auto_start(True)` will print a warning message and return None.

**Returns**

* `bool`: True if auto-start is successfully enabled, False if disabled, None if not supported in the current environment.

#### is\_auto\_start

```python
def is_auto_start(self):
```

Checks if the application is set to start automatically with the system.

**Returns**

* `bool`: True if auto-start is enabled, False otherwise.

### Miscellaneous

#### set\_icon

```python
def set_icon(self, icon_path: str):
```

Sets the application icon.

**Parameters**

* `icon_path` (str): Icon file path.

#### set\_tray\_icon

```python
def set_tray_icon(self, tray_icon_path: str):
```

Sets the tray icon.

**Parameters**

* `tray_icon_path` (str): Tray icon file path.

#### set\_tray\_menu\_items

```python
def set_tray_menu_items(self, tray_menu_items: Dict[str, Callable]):
```

Sets the tray menu items.

**Parameters**

* `tray_menu_items` (Dict\[str, Callable]): Dictionary of menu item labels and callback functions.

#### run

```python
def run(self):
```

Runs the application event loop. This must be executed at the end of your script.
