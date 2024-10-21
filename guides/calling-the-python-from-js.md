# JS에서 Python 호출하기

## PylonAPI 소개

`PyloidAPI` 클래스는 JavaScript와 Python 간의 상호 작용을 가능하게 하는 핵심 구성 요소입니다.

## Bridge 데코레이터 사용하기

`PyloidAPI` 클래스는 `Bridge` 데코레이터와 함께 사용되어 Python 메서드를 JavaScript에서 호출할 수 있게 합니다.

### Bridge 데코레이터 매개변수

`Bridge` 데코레이터는 다음 매개변수를 사용할 수 있습니다:

* `result`: 반환 타입을 지정합니다.
* `args`: 인수 타입을 지정합니다.

## Python에서 JavaScript API 설정하기

{% tabs %}
{% tab title="main.py" %}
```python
from pyloid import Pyloid, PyloidAPI, Bridge

app = Pyloid("Pyloid-App")

class CustomAPI(PyloidAPI):
    @Bridge(str, result=str)
    def echo(self, message):
        return f"Python에서 받은 메시지: {message}"

# 메인 윈도우 생성
window = app.create_window(
    title="Pyloid 브라우저",
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
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Pyloid</title>
    <script src="qrc:///qtwebchannel/qwebchannel.js"></script>
    <script>
      document.addEventListener('pyloidReady', async function () {
        console.log('Pyloid가 준비되었습니다');

        let result = await window.pyloid.CustomAPI.echo('안녕, Pyloid!');
        document.querySelector('p').textContent = result;
      });
    </script>
  </head>
  <body>
    <h1>안녕하세요!</h1>
    <p>없음</p>
  </body>
</html>
```
{% endtab %}
{% endtabs %}