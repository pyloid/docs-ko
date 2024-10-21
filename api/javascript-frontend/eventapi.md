# EventAPI

## EventAPI (JavaScript) 문서

`EventAPI`는 Pyloid 애플리케이션에서 Python에서 발생하는 이벤트를 JavaScript 프론트엔드에서 처리하기 위한 메서드를 제공합니다. 이 API를 사용하면 Python에서 보낸 이벤트를 프론트엔드에서 수신하고 관리할 수 있습니다.

JavaScript에서 Python을 실행하려면 `PyloidAPI`를 사용해야 합니다. 자세한 내용은 [PyloidAPI 문서](../python-backend/pyloidapi.md)를 참조하세요.

### 사용법

`EventAPI`의 메서드는 `window.pyloid.EventAPI.<메서드명>()`을 사용하여 호출할 수 있습니다.

---

#### 1. `listen(eventName: string, callback: function)`

- **설명**: Python에서 보낸 특정 이벤트를 수신하고 콜백 함수를 실행합니다.
- **매개변수**:
  - `eventName` (`string`): 수신할 이벤트의 이름
  - `callback` (`function`): 이벤트 수신 시 실행될 콜백 함수
- **반환값**: 없음

**사용 예**:

```javascript
window.pyloid.EventAPI.listen('pythonEvent', function (eventData) {
  console.log('Python에서 이벤트 수신:', eventData);
});
```

#### 2. `unlisten(eventName: string)`

- **설명**: 특정 Python 이벤트의 수신을 중지합니다.
- **매개변수**:
  - `eventName` (`string`): 수신을 중지할 이벤트의 이름
- **반환값**: 없음

**사용 예**:

```javascript
window.pyloid.EventAPI.unlisten('pythonEvent');
```

---

### Python에서 이벤트 발생시키기

Python에서 JavaScript로 이벤트를 발생시키려면 `WindowBrowser` 클래스의 `emit` 메서드를 사용하세요.

#### `emit(event_name: str, data: Optional[Dict] = None)`

- **설명**: Python에서 JavaScript 측으로 이벤트를 발생시킵니다.
- **매개변수**:
  - `event_name` (`str`): 발생시킬 이벤트의 이름
  - `data` (`Optional[Dict]`): 이벤트와 함께 보낼 데이터 (선택사항)

**사용 예**:

```python
# 간단한 이벤트 발생
window.emit('simpleEvent')

# 데이터와 함께 이벤트 발생
user_data = {
    'id': 1,
    'name': '홍길동',
    'email': 'hong@example.com'
}
window.emit('userDataUpdate', user_data)
```

다음은 Python에서 보낸 이벤트를 수신하고 처리하기 위해 `EventAPI`를 사용하는 예시입니다:

```javascript
// Python 이벤트 리스너 설정
window.pyloid.EventAPI.listen('simpleEvent', function () {
  console.log('Python에서 간단한 이벤트 수신');
});

window.pyloid.EventAPI.listen('userDataUpdate', function (userData) {
  console.log('Python에서 사용자 데이터 업데이트 수신:', userData);
});

// 나중에 이벤트 리스너 중지
function cleanupEventListeners() {
  window.pyloid.EventAPI.unlisten('simpleEvent');
  window.pyloid.EventAPI.unlisten('userDataUpdate');
}
```

이 예시에서는 `WindowBrowser` 인스턴스의 `emit` 메서드를 사용하여 두 가지 이벤트를 발생시킵니다:

1. `'simpleEvent'`: 데이터 없이 단순히 이벤트를 발생시킵니다.
2. `'userDataUpdate'`: 사용자 데이터와 함께 이벤트를 발생시킵니다.

이렇게 발생된 이벤트는 JavaScript 측에서 `EventAPI.listen` 메서드를 사용하여 수신하고 처리할 수 있습니다.

---

### 참고사항

- `listen` 메서드는 Python에서 보낸 이벤트 데이터를 자동으로 파싱하여 JSON 객체로 변환합니다. 파싱에 실패하면 원본 데이터를 그대로 전달합니다.
- 메모리 누수를 방지하기 위해 `unlisten` 메서드를 사용하여 이벤트 리스너를 제거하세요.
- 여러 Python 이벤트를 동시에 수신할 수 있으며, 각 이벤트에 대해 별도의 `listen` 호출을 사용하세요.

이 API를 사용하면 Python과 JavaScript 프론트엔드 간의 실시간 통신을 효과적으로 관리할 수 있습니다.
