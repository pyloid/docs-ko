# PyloidAPI

The `PyloidAPI` class is implemented by inheriting from QObject.

## Used with Bridge

The `PyloidAPI` class is used in conjunction with the `Bridge` decorator to enable interaction between JavaScript and Python. The `Bridge` decorator allows Python methods to be called from JavaScript.

### `Bridge` Decorator

The `Bridge` decorator can take the following parameters:

* `result`: Specifies the return type.
* `args`: Specifies the argument types.

## Usage Example

```python
from Pyloid import PyloidAPI, Bridge

class CustomAPI(PyloidAPI):
    @Bridge(str, int, result=str)
    def echo(self, message, number):
        print(f"Message: {message}-{number}")
        return f"Message received in Python: {message}-{number}"

    @Bridge(result=str)
    def getAppVersion(self):
        return "1.0.0"

    @Bridge(result=str)
    def create_window(self):
        window = app.create_window(
            title="Pyloid Browser2",
        )

        window.set_size(800, 600)
        window.set_position(0, 0)
        window.load_url("https://www.google.com")
        window.show()
        window.focus()

        return window.id

window = app.create_window(
    title="Pyloid Browser1",
    js_apis=[CustomAPI()],
    dev_tools=True
)

if (is_production()):
    window.load_file(os.path.join(get_production_path() + "/index.html"))
else:
    window.load_file("index.html")

window.show()
window.focus()

app.run()

```
