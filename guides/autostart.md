# 자동 시작

`app.set_auto_start()` 함수를 사용하여 사용자가 로그인할 때 애플리케이션이 자동으로 시작되도록 설정할 수 있습니다. Pyloid 클래스의 `app_name`이 자동 시작을 위한 키 이름으로 사용됩니다.

```python
app.set_auto_start(True)  # 자동 시작 활성화
app.set_auto_start(False)  # 자동 시작 비활성화
```

이 함수는 부울 값을 인수로 받습니다. 값이 `True`이면 사용자가 로그인할 때 애플리케이션이 자동으로 시작됩니다. 값이 `False`이면 애플리케이션이 자동으로 시작되지 않습니다.

## 참고 사항

* `set_auto_start(True)`는 프로덕션 환경에서만 작동합니다.
* `set_auto_start(False)`는 모든 환경에서 작동합니다.
* 비 프로덕션 환경에서 `set_auto_start(True)`를 호출하면 경고 메시지가 출력되고 `None`을 반환합니다.

## 자동 시작 상태 확인

`app.is_auto_start()` 함수를 사용하여 현재 자동 시작 설정 상태를 확인할 수 있습니다.

```python
is_auto_start = app.is_auto_start()
print(is_auto_start)  # True 또는 False 출력
```

이 함수는 자동 시작이 활성화되어 있으면 `True`를, 그렇지 않으면 `False`를 반환합니다.

## Pyloid 클래스의 app_name 사용

Pyloid 클래스에 정의된 `app_name`은 자동 시작 기능에서 중요한 역할을 합니다. 이 `app_name`은 운영 체제의 자동 시작 레지스트리나 설정에서 애플리케이션을 식별하는 키로 사용됩니다. 따라서 `app_name`을 고유하고 의미 있는 것으로 설정하는 것이 중요합니다.

예를 들어:

```python
from pyloid import Pyloid

app = Pyloid(app_name="MyUniqueApp")
app.set_auto_start(True)
```

이 경우, "MyUniqueApp"이라는 이름이 자동 시작 설정의 키로 사용됩니다. 이를 통해 여러 애플리케이션을 구분하고 각각에 대해 개별적으로 자동 시작을 관리할 수 있습니다.