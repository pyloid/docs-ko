# Production Utils

## `get_production_path()`

Returns the path to resource files in a production environment.

### Parameters

None

### Return Value

* `Optional[str]`: Returns the path to resource files in a production environment. Returns `None` if running as a regular Python script.

### Description

This function checks if the current execution environment is a production environment (e.g., an executable built with PyInstaller) and returns the path to resource files if it is. Returns `None` if running as a regular Python script.

### Example Usage

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

Checks if the current environment is a production environment.

### Parameters

None

### Return Value

* `bool`: Returns `True` if it is a production environment, otherwise returns `False`.

### Description

This function checks if the current execution environment is a production environment (e.g., an executable built with PyInstaller) by examining the `sys.frozen` attribute.

### Example Usage

```python
from pyloid import Pyloid, is_production, get_production_path

app = Pyloid(single_instance=True)

if (is_production()):
    window.load_file(os.path.join(get_production_path(), "build/index.html"))
else:
    window.load_url("http://localhost:5173")
```
