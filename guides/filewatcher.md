# 파일 감시자(filewatcher)

파일 감시자는 특정 파일이나 디렉토리의 변경 사항을 모니터링하는 기능을 제공합니다. 이를 통해 파일이나 디렉토리가 수정될 때 자동 알림을 받을 수 있습니다.

## 기본 사용법

### 파일 감시 시작

특정 파일의 변경 사항을 모니터링하려면 다음과 같이 사용하세요:

{% tabs %}
{% tab title="부분 코드" %}

```python
result = app.watch_file("경로/파일.txt")
if result:
    print("파일 감시가 시작되었습니다")
else:
    print("파일 감시 시작에 실패했습니다")
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

result = app.watch_file("/경로/파일.txt")
if result:
    print("파일 감시가 시작되었습니다")
else:
    print("파일 감시 시작에 실패했습니다")

app.run()
```

{% endtab %}
{% endtabs %}

### 디렉토리 감시 시작

특정 디렉토리의 변경 사항을 모니터링하려면 다음과 같이 사용하세요:

{% tabs %}
{% tab title="부분 코드" %}

```python
result = app.watch_directory("/경로/디렉토리")
if result:
    print("디렉토리 감시가 시작되었습니다")
else:
    print("디렉토리 감시 시작에 실패했습니다")
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

result = app.watch_directory("/경로/디렉토리")
if result:
    print("디렉토리 감시가 시작되었습니다")
else:
    print("디렉토리 감시 시작에 실패했습니다")

app.run()
```

{% endtab %}
{% endtabs %}

### 파일 변경 콜백 설정

파일이 변경될 때 실행될 콜백 함수를 설정할 수 있습니다:

{% tabs %}
{% tab title="부분 코드" %}

```python
def 파일_변경시(경로):
    print(f"파일이 변경되었습니다: {경로}")

app.set_file_change_callback(파일_변경시)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

app.watch_file("/경로/파일.txt")

# 콜백 함수 정의
def 파일_변경시(경로):
    print(f"파일이 변경되었습니다: {경로}")

# 콜백 함수 설정
app.set_file_change_callback(파일_변경시)

app.run()
```

{% endtab %}
{% endtabs %}

### 디렉토리 변경 콜백 설정

디렉토리가 변경될 때 실행될 콜백 함수를 설정할 수 있습니다:

{% tabs %}
{% tab title="부분 코드" %}

```python
def 디렉토리_변경시(경로):
    print(f"디렉토리가 변경되었습니다: {경로}")

app.set_directory_change_callback(디렉토리_변경시)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

app.watch_directory("/경로/디렉토리")

# 콜백 함수 정의
def 디렉토리_변경시(경로):
    print(f"디렉토리가 변경되었습니다: {경로}")

# 콜백 함수 설정
app.set_directory_change_callback(디렉토리_변경시)

app.run()
```

{% endtab %}
{% endtabs %}

### 감시 중지

특정 파일이나 디렉토리의 감시를 중지하려면 다음과 같이 사용하세요:

{% tabs %}
{% tab title="부분 코드" %}

```python
result = app.stop_watching("/경로/파일_또는_디렉토리")
if result:
    print("감시가 성공적으로 중지되었습니다")
else:
    print("감시 중지에 실패했습니다")
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

result = app.stop_watching("/경로/파일_또는_디렉토리")
if result:
    print("감시가 성공적으로 중지되었습니다")
else:
    print("감시 중지에 실패했습니다")

app.run()
```

{% endtab %}
{% endtabs %}

### 감시 중인 경로 확인

현재 감시 중인 모든 경로(파일 및 디렉토리)를 확인하려면 다음과 같이 사용하세요:

{% tabs %}
{% tab title="부분 코드" %}

```python
감시_중인_경로 = app.get_watched_paths()
print("모든 감시 중인 경로:", 감시_중인_경로)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

감시_중인_경로 = app.get_watched_paths()
print("모든 감시 중인 경로:", 감시_중인_경로)

app.run()
```

{% endtab %}
{% endtabs %}

### 감시 중인 파일만 가져오기

{% tabs %}
{% tab title="부분 코드" %}

```python
감시_중인_파일 = app.get_watched_files()
print("감시 중인 파일:", 감시_중인_파일)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

감시_중인_파일 = app.get_watched_files()
print("감시 중인 파일:", 감시_중인_파일)

app.run()
```

{% endtab %}
{% endtabs %}

### 감시 중인 디렉토리만 가져오기

{% tabs %}
{% tab title="부분 코드" %}

```python
감시_중인_디렉토리 = app.get_watched_directories()
print("감시 중인 디렉토리:", 감시_중인_디렉토리)
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

감시_중인_디렉토리 = app.get_watched_directories()
print("감시 중인 디렉토리:", 감시_중인_디렉토리)

app.run()
```

{% endtab %}
{% endtabs %}

### 모든 감시 중인 경로 제거

{% tabs %}
{% tab title="부분 코드" %}

```python
app.remove_all_watched_paths()
print("모든 감시 중인 경로가 제거되었습니다.")
```

{% endtab %}

{% tab title="전체 코드" %}

```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-앱", single_instance=True)

window = app.create_window(
    title="Pyloid 브라우저",
)

window.load_url("https://www.example.com")
window.show_and_focus()

# 모든 감시 중인 경로 제거
app.remove_all_watched_paths()
print("모든 감시 중인 경로가 제거되었습니다.")

app.run()
```

{% endtab %}
{% endtabs %}

## 사용 예시

다음은 파일 감시자를 사용하는 종합적인 예시입니다:

```python
# 파일과 디렉토리 감시 시작
app.watch_file("/경로/파일1.txt")
app.watch_file("/경로/파일2.txt")
app.watch_file("/경로/파일3.txt")
app.watch_file("/경로/파일4.txt")
app.watch_directory("/경로/디렉토리1")
app.watch_directory("/경로/디렉토리2")
app.watch_directory("/경로/디렉토리3")
app.watch_directory("/경로/디렉토리4")

# 콜백 함수 정의
def 파일_변경시(경로):
    print(f"파일이 변경되었습니다: {경로}")

def 디렉토리_변경시(경로):
    print(f"디렉토리가 변경되었습니다: {경로}")

# 콜백 함수 설정
app.set_file_change_callback(파일_변경시)
app.set_directory_change_callback(디렉토리_변경시)

# 감시 중인 경로 확인
print("감시 중인 경로:", app.get_watched_paths())
print("감시 중인 파일:", app.get_watched_files())
print("감시 중인 디렉토리:", app.get_watched_directories())

# 특정 경로 감시 중지
app.stop_watching("/경로/파일1.txt")
app.stop_watching("/경로/파일2.txt")
app.stop_watching("/경로/파일3.txt")
app.stop_watching("/경로/파일4.txt")
app.stop_watching("/경로/디렉토리1")
app.stop_watching("/경로/디렉토리2")
app.stop_watching("/경로/디렉토리3")
app.stop_watching("/경로/디렉토리4")

# 모든 감시 중인 경로 제거
app.remove_all_watched_paths()
```

## 주의사항

- 파일 감시자는 시스템 리소스를 사용하므로 필요할 때만 사용하고 사용이 끝나면 적절히 정리하세요.
- 많은 수의 파일이나 디렉토리를 감시하면 시스템 성능에 영향을 줄 수 있으므로 주의하세요.
- 일부 파일 시스템이나 운영 체제에서는 특정 유형의 변경 사항을 감지하지 못할 수 있습니다.

이 가이드를 통해 파일 감시자의 기본 사용법과 고급 기능을 이해하실 수 있을 것입니다. 추가 질문이나 도움이 더 필요하시면 언제든 물어보세요.
