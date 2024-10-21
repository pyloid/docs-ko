# Autostart

You can use the `app.set_auto_start()` function to set whether the application should start automatically when the user logs in. The `app_name` of the Pyloid class is used as the key name for auto-start.

```python
app.set_auto_start(True)  # Enable auto-start
app.set_auto_start(False)  # Disable auto-start
```

This function takes a boolean value as an argument. If the value is `True`, the application will start automatically when the user logs in. If the value is `False`, the application will not start automatically.

## Notes

* `set_auto_start(True)` only works in production environments.
* `set_auto_start(False)` works in all environments.
* Calling `set_auto_start(True)` in a non-production environment will print a warning message and return `None`.

## Checking Auto-start Status

You can use the `app.is_auto_start()` function to check the current auto-start setting status.

```python
is_auto_start = app.is_auto_start()
print(is_auto_start)  # Prints True or False
```

This function returns `True` if auto-start is enabled, and `False` otherwise.

## Using app\_name from the Pyloid class

The `app_name` defined in the Pyloid class plays an important role in the auto-start feature. This `app_name` is used as a key to identify the application in the operating system's auto-start registry or settings. Therefore, it's important to set the `app_name` to something unique and meaningful.

For example:

```python
from pyloid import Pyloid

app = Pyloid(app_name="MyUniqueApp")
app.set_auto_start(True)
```

In this case, the name "MyUniqueApp" is used as the key in the auto-start settings. This allows you to distinguish between multiple applications and manage auto-start individually for each one.
