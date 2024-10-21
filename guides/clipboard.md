# 클립보드

Pyloid는 사용하기 쉬운 클립보드 기능을 제공합니다. 텍스트와 이미지를 클립보드에 복사하거나 클립보드에서 가져올 수 있습니다.

## 텍스트 작업

### 텍스트를 클립보드에 복사하기

```python
app.copy_to_clipboard("복사할 텍스트")
```

이 함수를 사용하여 원하는 텍스트를 클립보드에 복사할 수 있습니다.

### 클립보드에서 텍스트 가져오기

```python
text = app.get_clipboard_text()
print(text)
```

이 함수를 사용하여 현재 클립보드에 있는 텍스트를 가져올 수 있습니다.

## 이미지 작업

### 이미지를 클립보드에 복사하기

```python
app.set_clipboard_image("assets/icon.png")
```

이 함수를 사용하여 이미지 파일을 클립보드에 복사할 수 있습니다. 파일 경로를 문자열로 전달하면 됩니다.

### 클립보드에서 이미지 가져오기

```python
image = app.get_clipboard_image()
if image:
    print("이미지를 성공적으로 가져왔습니다.")
else:
    print("클립보드에 이미지가 없습니다.")
```

이 함수를 사용하여 현재 클립보드에 있는 이미지를 가져올 수 있습니다. 반환된 이미지는 QImage 타입입니다. 클립보드에 이미지가 없으면 `None`을 반환합니다.

QImage 객체를 사용하여 이미지 처리, 표시, 저장 등 다양한 작업을 수행할 수 있습니다.

## 참고사항

- `set_clipboard_image` 함수는 이미지 파일 경로뿐만 아니라 바이트 데이터나 `os.PathLike` 객체도 받을 수 있습니다.
- `get_clipboard_image` 함수는 QImage 객체를 반환합니다. 이를 사용하여 이미지 처리, 표시 및 기타 작업을 수행할 수 있습니다.