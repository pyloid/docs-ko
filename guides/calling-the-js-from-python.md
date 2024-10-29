# Python에서 JavaScript 호출하기

이 가이드는 Python 코드에서 JavaScript 함수를 호출하는 방법을 설명합니다.

## 1. JavaScript 측 설정

먼저, Python에서 오는 이벤트를 받기 위해 JavaScript 코드를 준비해야 합니다.

```javascript
document.addEventListener('pyloidReady', function () {
  window.pyloid.EventAPI.listen('pythonEvent', function (data) {
    console.log('Python에서 이벤트 수신:', data.message);
  });
});
```

이 코드는 다음과 같은 작업을 수행합니다:

1. `pyloidReady` 이벤트를 기다립니다. 이 이벤트는 Pyloid 환경이 완전히 로드되었을 때 발생합니다.
2. Pyloid 환경이 준비되면, `window.pyloid.EventAPI.listen` 메소드를 사용하여 'pythonEvent'라는 이벤트를 수신하기 시작합니다.
3. 'pythonEvent'가 발생하면, 전달된 데이터의 `message` 속성을 콘솔에 기록합니다.

## 2. Python에서 이벤트 트리거하기

Python 코드에서는 다음과 같이 JavaScript로 이벤트를 트리거할 수 있습니다:

```python
window.emit('pythonEvent', { "message": 'Python에서 안녕하세요!' })
```

이 코드는 다음과 같은 작업을 수행합니다:

1. `window.emit` 함수를 사용하여 'pythonEvent'라는 이벤트를 트리거합니다.
2. 이벤트와 함께 데이터 객체를 전달합니다. 이 객체는 "message" 키와 'Python에서 안녕하세요!' 값을 가집니다.

여기서 `window`는 `create_window(...)` 메소드를 통해 생성된 `BrowserWindow` 객체입니다.

## 작동 방식

1. JavaScript 코드가 실행되어 'pythonEvent' 이벤트 리스너를 설정합니다.
2. Python 코드가 실행되어 'pythonEvent'를 트리거하고 메시지를 전달합니다.
3. JavaScript 이벤트 리스너가 이 이벤트를 감지하고 전달된 메시지를 콘솔에 기록합니다.

## 주의사항

- JavaScript 코드는 Python 코드가 실행되기 전에 로드되어야 합니다. 그렇지 않으면 이벤트 리스너가 설정되지 않아 Python에서 트리거된 이벤트를 받지 못할 수 있습니다.
- 데이터 전송에는 JSON 형식이 사용되므로 복잡한 데이터 구조도 전달할 수 있습니다.

이 방법을 사용하면 Python과 JavaScript 간의 양방향 통신이 가능해져 더 동적이고 상호작용적인 애플리케이션을 만들 수 있습니다.
