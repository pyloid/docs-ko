# 파일 다이어로그

## 개요

이 문서는 파일 다이어로그를 열고 파일이나 디렉토리를 선택하는 방법에 대해 설명합니다. 이 기능은 PySide6의 `QFileDialog` 클래스를 사용하여 구현됩니다. 이 문서에서는 `open_file_dialog`, `save_file_dialog`, `select_directory_dialog` 세 가지 메서드를 다룹니다.

## 메서드 설명

### `open_file_dialog`

파일을 열기 위한 다이어로그를 엽니다.

#### 매개변수

- `dir` (str, optional): 다이어로그가 처음 열릴 디렉토리입니다. 기본값은 현재 작업 디렉토리입니다.
- `filter` (str, optional): 선택 가능한 파일 형식을 지정하는 문자열입니다. 예를 들어, `"Text Files (*.txt);;All Files (*)"`와 같이 사용할 수 있습니다.

#### 반환값

- `Optional[str]`: 선택된 파일의 경로를 반환합니다. 파일이 선택되지 않으면 `None`을 반환합니다.

#### 예제

```python
app = Pyloid(app_name="Pyloid-App")
file_path = app.open_file_dialog(dir="/home/user", filter="Text Files (*.txt)")
if file_path:
    print("Selected file:", file_path)
```

### `save_file_dialog`

파일을 저장하기 위한 다이어로그를 엽니다.

#### 매개변수

- `dir` (str, optional): 다이어로그가 처음 열릴 디렉토리입니다. 기본값은 현재 작업 디렉토리입니다.
- `filter` (str, optional): 저장 가능한 파일 형식을 지정하는 문자열입니다. 예를 들어, `"Text Files (*.txt);;All Files (*)"`와 같이 사용할 수 있습니다.

#### 반환값

- `Optional[str]`: 선택된 파일의 경로를 반환합니다. 파일이 선택되지 않으면 `None`을 반환합니다.

#### 예제

```python
app = Pyloid(app_name="Pyloid-App")
file_path = app.save_file_dialog(dir="/home/user", filter="Text Files (*.txt)")
if file_path:
    print("File will be saved to:", file_path)
```

### `select_directory_dialog`

디렉토리를 선택하기 위한 다이어로그를 엽니다.

#### 매개변수

- `dir` (str, optional): 다이어로그가 처음 열릴 디렉토리입니다. 기본값은 현재 작업 디렉토리입니다.

#### 반환값

- `Optional[str]`: 선택된 디렉토리의 경로를 반환합니다. 디렉토리가 선택되지 않으면 `None`을 반환합니다.

#### 예제

```python
app = Pyloid(app_name="Pyloid-App")
directory_path = app.select_directory_dialog(dir="/home/user")
if directory_path:
    print("Selected directory:", directory_path)
```

## 참고

이 메서드들은 PyQt의 `QFileDialog` 클래스를 사용하여 구현됩니다. PyQt는 Python에서 Qt 라이브러리를 사용할 수 있게 해주는 바인딩입니다. `QFileDialog`는 파일 및 디렉토리 선택을 위한 표준 다이어로그를 제공합니다.
