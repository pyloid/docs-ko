# 개발자 도구

Pyloid는 두 가지 방법으로 개발자 도구를 구성할 수 있습니다. 창을 만들 때 매개변수로 지정하거나, 창을 만든 후 메서드를 사용하여 설정할 수 있습니다. 개발자 도구가 활성화되면 `F12` 키를 사용하여 열 수 있습니다.

## 1. 창 생성 시 매개변수로 설정하기

창을 만들 때 `dev_tools` 매개변수를 사용하여 개발자 도구를 설정할 수 있습니다. 이 매개변수의 기본값은 `False`입니다.

{% tabs %}
{% tab title="부분 코드" %}

```python
window = app.create_window(
    title="Pylon 브라우저",
    dev_tools=True  # 개발자 도구 활성화 (기본값은 False)
)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
    dev_tools=True  # 개발자 도구 활성화 (기본값은 False)
)

window.load_url("https://www.example.com")
window.show_and_focus()

app.run()
```

{% endtab %}
{% endtabs %}

이 방법은 창 생성 시점에 즉시 개발자 도구의 상태를 설정하고 싶을 때 유용합니다.

## 2. 메서드를 사용하여 설정하기

창을 만든 후 `set_dev_tools()` 메서드를 사용하여 개발자 도구를 설정할 수 있습니다.

{% tabs %}
{% tab title="부분 코드" %}

```python
window = app.create_window(
    title="Pyloid 브라우저",
)
window.set_dev_tools(True)  # 개발자 도구 활성화
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)
window.set_dev_tools(True)  # 개발자 도구 활성화

window.load_url("https://www.example.com")
window.show_and_focus()

app.run()
```

{% endtab %}
{% endtabs %}

이 방법은 창을 만든 후 조건에 따라 개발자 도구의 상태를 동적으로 변경하고 싶을 때 유용합니다.

## F12 키를 통한 개발자 도구 접근

`dev_tools=True`로 설정하면 사용자가 `F12` 키를 눌러 개발자 도구를 열 수 있습니다. 이는 웹 브라우저에서 사용되는 것과 동일한 방법으로, 개발자들에게 친숙한 방식으로 도구에 접근할 수 있게 해줍니다.

## 사용 예시

개발 환경과 프로덕션 환경에서 개발자 도구를 다르게 설정하는 예시:

{% tabs %}
{% tab title="부분 코드" %}

```python
if is_production():
    window = app.create_window(
        title="Pyloid 브라우저-프로덕션",
    )
    window.set_dev_tools(False)  # 프로덕션 환경에서 개발자 도구 비활성화
else:
    window = app.create_window(
        title="Pyloid 브라우저-개발",
        dev_tools=True  # 개발 환경에서 개발자 도구 활성화
    )
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

if is_production():
    window = app.create_window(
        title="Pyloid 브라우저-프로덕션",
    )
    window.set_dev_tools(False)  # 프로덕션 환경에서 개발자 도구 비활성화
else:
    window = app.create_window(
        title="Pyloid 브라우저-개발",
        dev_tools=True  # 개발 환경에서 개발자 도구 활성화
    )

window.load_url("https://www.example.com")
window.show_and_focus()

app.run()
```

{% endtab %}
{% endtabs %}

두 방법 모두 동일한 결과를 제공하므로, 프로젝트 요구사항과 코드 구조에 따라 적절한 방법을 선택할 수 있습니다.
