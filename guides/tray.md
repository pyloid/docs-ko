# Tray

Pyloid makes it easy to implement system tray functionality. This guide explains how to set up a tray icon, handle events, add menu items, animate the icon, and set tooltips. All tray-related features work dynamically, allowing real-time changes even while the app is running.

## Setting the Tray Icon

Use the `set_tray_icon` method to set the tray icon. This method can be called at any time to change the icon:

```python
app.set_tray_icon("assets/icon.ico")
```

Note: This method can be called while the app is running, allowing you to change the icon dynamically based on different conditions.

## Animating the Tray Icon

You can apply animations to the tray icon. Use the `set_tray_icon_animation` method to display multiple icon frames sequentially:

```python
app.set_tray_icon_animation(
    [
        "assets/frame1.png",
        "assets/frame2.png",
        "assets/frame3.png",
        "assets/frame4.png",
    ],
    interval=500,
)
```

This setting can be changed during runtime, and you can revert to a regular icon at any time.

## Setting the Tray Icon Tooltip

You can set a tooltip that appears when hovering over the tray icon. Use the `set_tray_tooltip` method:

```python
app.set_tray_tooltip("This is a Pyloid application.")
```

The tooltip can also be dynamically changed at any time during app execution.

## Handling Tray Events

You can handle various click events on the tray icon. Use the `set_tray_actions` method to set event handlers. This setting can also be changed at any time:

```python
app.set_tray_actions(
    {
        TrayEvent.DoubleClick: lambda: print("Tray icon was double-clicked."),
        TrayEvent.MiddleClick: lambda: print("Tray icon was middle-clicked."),
        TrayEvent.RightClick: lambda: print("Tray icon was right-clicked."),
        TrayEvent.LeftClick: lambda: print("Tray icon was left-clicked."),
    }
)
```

Note: Event handlers can be dynamically added, modified, or removed during app execution.

## Adding and Dynamically Updating Tray Menu Items

You can add items to the context menu that appears when right-clicking the tray icon. Use the `set_tray_menu_items` method to set menu items. This menu configuration can also be changed in real-time:

```python
app.set_tray_menu_items(
    [
        {"label": "Show Window", "callback": lambda: app.show_and_focus_main_window()},
        {"label": "Exit", "callback": lambda: app.quit()},
    ]
)
```

Each menu item is defined as a dictionary with `label` and `callback` keys. Menu items can be dynamically added, modified, or removed while the app is running.

Example of dynamically updating the menu:

```python
def update_menu():
    app.set_tray_menu_items(
        [
            {
                "label": "New Menu 1",
                "callback": lambda: print("New Menu 1 clicked"),
            },
            {
                "label": "New Menu 2",
                "callback": lambda: print("New Menu 2 clicked"),
            },
            {"label": "Exit", "callback": lambda: app.quit()},
        ]
    )

# Update tray menu after 5 seconds
timer.start_single_shot_timer(5000, update_menu)
```

## Complete Example

Here's a complete example implementing tray functionality. It demonstrates that all settings can be changed dynamically:

```python
import os
from pyloid import PyloidApp, TrayEvent, is_production, get_production_path, PyloidTimer


app = PyloidApp("Pyloid-App", single_instance=True)
timer = PyloidTimer()

if (is_production()):
    app.set_icon(os.path.join(get_production_path(), "icon.ico"))
    app.set_tray_icon(os.path.join(get_production_path(), "icon.ico"))
else:
    app.set_icon("assets/icon.ico")
    app.set_tray_icon("assets/icon.ico")

app.set_tray_actions(
    {
        TrayEvent.DoubleClick: lambda: print("Tray icon was double-clicked."),
        TrayEvent.MiddleClick: lambda: print("Tray icon was middle-clicked."),
        TrayEvent.RightClick: lambda: print("Tray icon was right-clicked."),
        TrayEvent.LeftClick: lambda: print("Tray icon was left-clicked."),
    }
)

app.set_tray_menu_items(
    [
        {"label": "Show Window", "callback": lambda: app.show_and_focus_main_window()},
        {"label": "Exit", "callback": lambda: app.quit()},
    ]
)

# Set tray icon tooltip
app.set_tray_tooltip("This is a Pyloid application.")

def update_menu():
    app.set_tray_menu_items(
        [
            {
                "label": "New Menu 1",
                "callback": lambda: print("New Menu 1 clicked"),
            },
            {
                "label": "New Menu 2",
                "callback": lambda: print("New Menu 2 clicked"),
            },
            {"label": "Exit", "callback": lambda: app.quit()},
        ]
    )

def update_tray_icon():
    # Set tray icon animation
    app.set_tray_icon_animation(
        [
            "assets/frame1.png",
            "assets/frame2.png",
            "assets/frame3.png",
            "assets/frame4.png",
        ],
        interval=500,
    )

# Update tray menu after 5 seconds
timer.start_single_shot_timer(5000, update_menu)

# Start tray icon animation after 3 seconds
timer.start_single_shot_timer(3000, update_tray_icon)

# Change tray icon to static icon after 6 seconds
timer.start_single_shot_timer(6000, lambda: app.set_tray_icon("assets/icon.ico"))

# Change tray icon tooltip after 10 seconds
timer.start_single_shot_timer(10000, lambda: app.set_tray_tooltip("New tooltip!"))
```

This example demonstrates setting the tray icon, handling events, adding menu items, animating the icon, and setting tooltips. All settings can be changed dynamically while the app is running, allowing you to update tray functionality in real-time as needed.
