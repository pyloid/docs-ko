# 키보드 단축키

## 단축키 추가 및 관리

이 섹션에서는 Tauri 애플리케이션에서 키보드 단축키를 추가하고 관리하는 방법을 설명합니다.

### 단축키 추가하기

`window.add_shortcut()` 메서드를 사용하여 새로운 단축키를 추가할 수 있습니다.

```python
window.add_shortcut("단축키", lambda: (동작1, 동작2, ...))
```

예시:

```python
window.add_shortcut("Ctrl+Shift+S", lambda: (
    print("Ctrl+Shift+S 단축키가 눌렸습니다."),
))
```

일반 함수를 사용한 예시:

```python
def 단축키_처리():
    print("Ctrl+Shift+F 단축키가 눌렸습니다.")
    print("현재 시간:", datetime.now())

window.add_shortcut("Ctrl+Shift+F", 단축키_처리)
```

### 단축키 제거하기

`window.remove_shortcut()` 메서드를 사용하여 기존 단축키를 제거할 수 있습니다.

```python
window.remove_shortcut("<단축키>")
```

예시:

```python
window.remove_shortcut("Ctrl+Shift+F")
```

### 모든 단축키 보기

`window.get_all_shortcuts()->Dict` 메서드를 사용하여 현재 등록된 모든 단축키를 볼 수 있습니다.

예시:

```python
print(window.get_all_shortcuts())
```

### 이벤트 트리거하기

단축키를 통해 JavaScript 이벤트를 트리거할 수 있습니다.

```python
window.add_shortcut("단축키", lambda: (
    window.emit('이벤트이름', { "데이터": '값' })
))
```

예시:

```python
window.add_shortcut("Ctrl+Shift+E", lambda: (
    print("Ctrl+Shift+E 단축키가 눌렸습니다."),
    window.emit('파이썬이벤트', { "메시지": '파이썬에서 안녕하세요!' })
))
```
