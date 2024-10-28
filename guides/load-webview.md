# 웹뷰 로드하기

### `load_url` (url 로드하기)

```python
app = Pyloid(app_name="Pyloid-App")

window = app.create_window("Pyloid-Window")

window.load_url("https://www.example.com")

window.show()
```

### `load_file` (파일 로드하기)

```python
app = Pyloid(app_name="Pyloid-App")

window = app.create_window("Pyloid-Window")

window.load_file("./index.html")

window.show()
```

### `load_html` (html 로드하기)

```python
app = Pyloid(app_name="Pyloid-App")

window = app.create_window("Pyloid-Window")

window.load_html("<h1>Hello, Pyloid!</h1>")

window.show()
```
