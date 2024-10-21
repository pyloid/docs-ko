# PyloidAPI

`PyloidAPI` 클래스는 QObject를 상속받아 구현됩니다.

## Bridge와 함께 사용

`PyloidAPI` 클래스는 JavaScript와 Python 간의 상호 작용을 가능하게 하는 `Bridge` 데코레이터와 함께 사용됩니다. `Bridge` 데코레이터를 사용하면 JavaScript에서 Python 메서드를 호출할 수 있습니다.

### `Bridge` 데코레이터

`Bridge` 데코레이터는 다음과 같은 매개변수를 사용할 수 있습니다:

- `result`: 반환 타입을 지정합니다.
- `args`: 인자 타입을 지정합니다.

## 사용 예시

```python
from Pyloid import PyloidAPI, Bridge

class CustomAPI(PyloidAPI):
    @Bridge(str, int, result=str)
    def echo(self, message, number):
        print(f"메시지: {message}-{number}")
        return f"Python에서 받은 메시지: {message}-{number}"

    @Bridge(result=str)
    def getAppVersion(self):
        return "1.0.0"

    @Bridge(result=str)
    def create_window(self):
        window = app.create_window(
            title="Pyloid 브라우저2",
        )

        window.set_size(800, 600)
        window.set_position(0, 0)
        window.load_url("https://www.google.com")
        window.show()
        window.focus()

        return window.id

window = app.create_window(
    title="Pyloid 브라우저1",
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
