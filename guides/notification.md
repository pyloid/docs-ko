# 알림

Pyloid의 `show_notification()` 메서드를 사용하여 사용자에게 알림을 표시할 수 있습니다.

## 사용법

```python
app.show_notification(title, message)
```

### 매개변수

- `title` (문자열): 알림의 제목
- `message` (문자열): 알림 메시지의 내용

### 예시

```python
app.show_notification("알림", "알림 메시지")
```

이 코드는 "알림"이라는 제목과 "알림 메시지"라는 내용의 알림을 표시합니다.

## 알림 클릭 콜백 설정하기

알림이 클릭되었을 때 실행될 콜백 함수를 설정할 수 있습니다.

### 사용법

```python
app.set_notification_callback(callback_function)
```

### 매개변수

- `callback_function` (함수): 알림이 클릭되었을 때 실행될 함수

### 예시

```python
def on_notification_clicked():
    print("알림이 클릭되었습니다!")

app.set_notification_callback(on_notification_clicked)

# 새 알림 표시
app.show_notification("새 알림", "이 알림을 클릭하세요!")
```

이 코드는 알림 클릭 콜백을 설정하고 새 알림을 표시합니다. 사용자가 알림을 클릭하면 "알림이 클릭되었습니다!"라는 메시지가 출력됩니다.
