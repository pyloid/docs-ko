# Devtools

Pyloid allows you to configure developer tools in two ways. You can specify them as parameters when creating a window, or use a method to set them after the window has been created. When developer tools are activated, you can open them using the `F12` key.

## 1. Setting as a Parameter When Creating a Window

You can set the developer tools using the `dev_tools` parameter when creating a window. The default value for this parameter is `False`.

{% tabs %}
{% tab title="Partial Code" %}
```python
window = app.create_window(
    title="Pylon Browser",
    dev_tools=True  # Activate developer tools (default is False)
)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
    dev_tools=True  # Activate developer tools (default is False)
)

window.load_url("https://www.example.com")
window.show_and_focus()

app.run()
```
{% endtab %}
{% endtabs %}

This method is useful when you want to immediately set the state of the developer tools at the point of window creation.

## 2. Setting Using a Method

You can set the developer tools using the `set_dev_tools()` method after creating a window.

{% tabs %}
{% tab title="Partial Code" %}
```python
window = app.create_window(
    title="Pyloid Browser",
)
window.set_dev_tools(True)  # Activate developer tools
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)
window.set_dev_tools(True)  # Activate developer tools

window.load_url("https://www.example.com")
window.show_and_focus()

app.run()
```
{% endtab %}
{% endtabs %}

This method is useful when you want to dynamically change the state of the developer tools based on conditions after creating the window.

## Accessing Developer Tools via F12 Key

Setting `dev_tools=True` allows users to open the developer tools by pressing the `F12` key. This is the same method as used in web browsers and provides a familiar way for developers to access the tools.

## Usage Example

An example of setting developer tools differently for development and production environments:

{% tabs %}
{% tab title="Partial Code" %}
```python
if is_production():
    window = app.create_window(
        title="Pyloid Browser-production",
    )
    window.set_dev_tools(False)  # Deactivate developer tools in production environment
else:
    window = app.create_window(
        title="Pyloid Browser-dev",
        dev_tools=True  # Activate developer tools in development environment
    )
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

if is_production():
    window = app.create_window(
        title="Pyloid Browser-production",
    )
    window.set_dev_tools(False)  # Deactivate developer tools in production environment
else:
    window = app.create_window(
        title="Pyloid Browser-dev",
        dev_tools=True  # Activate developer tools in development environment
    )

window.load_url("https://www.example.com")
window.show_and_focus()

app.run()
```
{% endtab %}
{% endtabs %}

Both methods provide the same result, so you can choose the appropriate method based on your project requirements and code structure.
