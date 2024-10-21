# TrayEvent

`TrayEvent` is an enumeration (Enum) class that represents events related to the system tray icon. This class is mapped to `QSystemTrayIcon.ActivationReason`.

## Enumeration Members

* `DoubleClick`: Event that occurs when the tray icon is double-clicked
* `MiddleClick`: Event that occurs when the tray icon is clicked with the middle button
* `RightClick`: Event that occurs when the tray icon is clicked with the right button (context menu)
* `LeftClick`: Event that occurs when the tray icon is clicked with the left button
* `Unknown`: Unknown event

## Usage Example

```python
from Pyloid import Pyloid, TrayEvent

app.set_tray_actions(
    {
        TrayEvent.DoubleClick: lambda: print("Tray icon was double-clicked."),
        TrayEvent.MiddleClick: lambda: print("Tray icon was middle-clicked."),
        TrayEvent.RightClick: lambda: print("Tray icon was right-clicked."),
        TrayEvent.LeftClick: lambda: print("Tray icon was left-clicked."),
    }
)
```
