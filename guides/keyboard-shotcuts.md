# Keyboard Shotcuts

## Adding and Managing Shortcuts

This section explains how to add and manage keyboard shortcuts in a Tauri application.

### Adding Shortcuts

You can add new shortcuts using the `window.add_shortcut()` method.

```python
window.add_shortcut("shortcut", lambda: (action1, action2, ...))
```

Example:

```python
window.add_shortcut("Ctrl+Shift+S", lambda: (
    print("Ctrl+Shift+S shortcut was pressed."),
))
```

Example using a regular function:

```python
def handle_shortcut():
    print("Ctrl+Shift+F shortcut was pressed.")
    print("Current time:", datetime.now())

window.add_shortcut("Ctrl+Shift+F", handle_shortcut)
```

### Removing Shortcuts

You can remove existing shortcuts using the `window.remove_shortcut()` method.

```python
window.remove_shortcut("<shortcut>")
```

Example:

```python
window.remove_shortcut("Ctrl+Shift+F")
```

### Viewing All Shortcuts

You can view all currently registered shortcuts using the `window.get_all_shortcuts()->Dict` method.

Example:

```python
print(window.get_all_shortcuts())
```

### Triggering Events

You can trigger JavaScript events through shortcuts.

```python
window.add_shortcut("shortcut", lambda: (
    window.emit('eventName', { "data": 'value' })
))
```

Example:

```python
window.add_shortcut("Ctrl+Shift+E", lambda: (
    print("Ctrl+Shift+E shortcut was pressed."),
    window.emit('pythonEvent', { "message": 'Hello from Python!' })
))
```
