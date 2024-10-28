# 창 위치

### 1. 윈도우 생성 시 파라미터 활용

```python
app = Pyloid(app_name="Pyloid-App")

window = app.create_window("Pyloid-Window", x=100, y=100)
```

### 2. `set_position` 메서드 활용

`x`, `y` 파라미터에 따라 창의 위치가 결정됩니다.

```python
app = Pyloid(app_name="Pyloid-App")

window = app.create_window("Pyloid-Window")

window.set_position(x=100, y=100)
```

### 3. `set_position_by_anchor` 메서드 활용

`anchor` 파라미터에 따라 창의 위치가 결정됩니다.

이용가능한 스크린 기준으로 위치가 정해집니다.(작업표시줄 제외한 스크린 내에서)

- `top`
- `left`
- `right`
- `bottom`
- `top-left`
- `top-right`
- `bottom-left`
- `bottom-right`
- `center`

```python
app = Pyloid(app_name="Pyloid-App")

window = app.create_window("Pyloid-Window")

window.set_position_by_anchor("center")
```
