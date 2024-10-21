# Calling the Python from JS

## Introduction to PylonAPI

The `PyloidAPI` class is a key component that enables interaction between JavaScript and Python.

## Using the Bridge Decorator

The `PyloidAPI` class is used in conjunction with the `Bridge` decorator to allow Python methods to be called from JavaScript.

### Bridge Decorator Parameters

The `Bridge` decorator can use the following parameters:

* `result`: Specifies the return type.
* `args`: Specifies the argument types.

## Setting up JavaScript API in Python

{% tabs %}
{% tab title="main.py" %}
```python
from pyloid import Pyloid, PyloidAPI, Bridge

app = Pyloid("Pyloid-App")

class CustomAPI(PyloidAPI):
    @Bridge(str, result=str)
    def echo(self, message):
        return f"Message received in Python: {message}"

# Create main window
window = app.create_window(
    title="Pyloid Browser",
    js_apis=[CustomAPI()],
)

window.load_file("index.html")

window.show()
window.focus()

app.run()
```
{% endtab %}

{% tab title="index.html" %}
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Pyloid</title>
    <script src="qrc:///qtwebchannel/qwebchannel.js"></script>
    <script>
      document.addEventListener('pyloidReady', async function () {
        console.log('Pyloid is ready');

        let result = await window.pyloid.CustomAPI.echo('Hello, Pyloid!');
        document.querySelector('p').textContent = result;
      });
    </script>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>None</p>
  </body>
</html>
```
{% endtab %}
{% endtabs %}
