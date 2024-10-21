# 타이머

`PyloidTimer`는 PySide6의 QTimer를 기반으로 한 편리한 타이머 관리 클래스입니다. 이를 통해 다양한 유형의 타이머를 쉽게 생성하고 관리할 수 있습니다.

## 목차

1. [기본 사용법](timer.md#기본-사용법)
2. [주기적 타이머](timer.md#주기적-타이머)
3. [단발성 타이머](timer.md#단발성-타이머)
4. [타이머 관리](timer.md#타이머-관리)
5. [정밀 타이머](timer.md#정밀-타이머)
6. [고급 사용법](timer.md#고급-사용법)

## 기본 사용법

먼저 `PyloidTimer` 인스턴스를 생성합니다:

```python
from pyloid.timer import PyloidTimer

timer_manager = PyloidTimer()
```

## 주기적 타이머

주기적으로 실행되는 타이머를 시작하려면 `start_periodic_timer` 메서드를 사용합니다:

{% tabs %}
{% tab title="부분 코드" %}

```python
def print_hello():
    print("안녕하세요!")

# 2초마다 "안녕하세요!"를 출력하는 타이머 시작
timer_id = timer_manager.start_periodic_timer(2000, print_hello)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import  Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

def print_hello():
    print("안녕하세요!")

# 2초마다 "안녕하세요!"를 출력하는 타이머 시작
timer_id = timer_manager.start_periodic_timer(2000, print_hello)

app.run()
```

{% endtab %}
{% endtabs %}

## 단발성 타이머

한 번만 실행되는 타이머를 시작하려면 `start_single_shot_timer` 메서드를 사용합니다:

{% tabs %}
{% tab title="부분 코드" %}

```python
def delayed_message():
    print("5초가 지났습니다!")

# 5초 후 메시지를 출력하는 단발성 타이머 시작
timer_id = timer_manager.start_single_shot_timer(5000, delayed_message)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

def delayed_message():
    print("5초가 지났습니다!")

# 5초 후 메시지를 출력하는 단발성 타이머 시작
timer_id = timer_manager.start_single_shot_timer(5000, delayed_message)

app.run()
```

{% endtab %}
{% endtabs %}

## 타이머 관리

### 타이머 중지하기

{% tabs %}
{% tab title="부분 코드" %}

```python
# ID를 사용하여 타이머 중지
timer_manager.stop_timer(timer_id)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# 타이머 시작
timer_id = timer_manager.start_periodic_timer(2000, lambda: print("안녕하세요!"))

# ID를 사용하여 타이머 중지
timer_manager.stop_timer(timer_id)

app.run()
```

{% endtab %}
{% endtabs %}

### 타이머 활성 상태 확인

{% tabs %}
{% tab title="부분 코드" %}

```python
if timer_manager.is_timer_active(timer_id):
    print("타이머가 아직 실행 중입니다.")
else:
    print("타이머가 중지되었습니다.")
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# 타이머 시작
timer_id = timer_manager.start_periodic_timer(2000, lambda: print("안녕하세요!"))

# 타이머 활성 상태 확인
if timer_manager.is_timer_active(timer_id):
    print("타이머가 아직 실행 중입니다.")
else:
    print("타이머가 중지되었습니다.")

app.run()
```

{% endtab %}
{% endtabs %}

### 남은 시간 확인

{% tabs %}
{% tab title="부분 코드" %}

```python
remaining_time = timer_manager.get_remaining_time(timer_id)
if remaining_time is not None:
    print(f"타이머가 실행되기까지 {remaining_time}ms 남았습니다.")
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# 타이머 시작
timer_id = timer_manager.start_periodic_timer(2000, lambda: print("안녕하세요!"))

# 남은 시간 확인
remaining_time = timer_manager.get_remaining_time(timer_id)
if remaining_time is not None:
    print(f"타이머가 실행되기까지 {remaining_time}ms 남았습니다.")

app.run()
```

{% endtab %}
{% endtabs %}

### 타이머 간격 변경

{% tabs %}
{% tab title="부분 코드" %}

```python
# 타이머 간격을 3초로 변경
timer_manager.set_interval(timer_id, 3000)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# 타이머 시작
timer_id = timer_manager.start_periodic_timer(1000, lambda: print("안녕하세요!"))

# 타이머 간격을 3초로 변경
timer_manager.set_interval(timer_id, 3000)

app.run()
```

{% endtab %}
{% endtabs %}

## 정밀 타이머

더 정밀한 타이밍이 필요한 경우 정밀 타이머를 사용할 수 있습니다:

{% tabs %}
{% tab title="부분 코드" %}

```python
def precise_task():
    print("정밀 작업 실행 중")

# 100ms 간격으로 정밀 주기적 타이머 시작
precise_timer_id = timer_manager.start_precise_periodic_timer(100, precise_task)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

def precise_task():
    print("정밀 작업 실행 중")

# 100ms 간격으로 정밀 주기적 타이머 시작
precise_timer_id = timer_manager.start_precise_periodic_timer(100, precise_task)

app.run()
```

{% endtab %}
{% endtabs %}

## 고급 사용법

### 람다 함수 사용

{% tabs %}
{% tab title="부분 코드" %}

```python
counter = 0

def count():
    global counter
    counter += 1
    print(f"카운터: {counter}")

timer_id = timer_manager.start_periodic_timer(1000, count)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# PyloidTimer 인스턴스 생성
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

counter = 0

def count():
    global counter
    counter += 1
    print(f"카운터: {counter}")

timer_id = timer_manager.start_periodic_timer(1000, count)

app.run()
```

{% endtab %}
{% endtabs %}

## 결론

`PyloidTimer`는 다양한 타이밍 요구사항을 쉽게 관리할 수 있는 강력한 도구입니다. 간단한 주기적 작업부터 정밀한 타이밍이 필요한 작업까지 다양한 상황에서 유용하게 사용될 수 있습니다.
