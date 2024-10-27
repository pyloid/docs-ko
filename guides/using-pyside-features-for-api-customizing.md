# pyside를 사용하여 API 커스터마이징

Pyloid는 PySide6를 기반으로 만들어졌으며, 사용자가 직접 API를 확장할 수 있는 기능을 제공합니다. 이를 통해 PySide6의 다양한 기능을 Pyloid 애플리케이션에서 쉽게 사용할 수 있습니다.

## 커스텀 API 생성 방법

1. `PyloidAPI` 클래스를 상속받아 새로운 클래스를 만듭니다.
2. 원하는 메서드를 정의하고 `@Bridge` 데코레이터를 사용하여 JavaScript와 연결합니다.
3. 메서드 내에서 PySide6의 기능을 활용합니다.

## 예제

### 파일 열기 대화상자 구현

```python
from PySide6.QtWidgets import QFileDialog
from pyloid import PyloidAPI, Bridge

class CustomAPI(PyloidAPI):
    @Bridge(result=str)
    def open_file(self):
        file, _ = QFileDialog.getOpenFileName(filter="Text files (*.txt)")
        return file if file else ""

    @Bridge(result=str)
    def save_file(self):
        file, _ = QFileDialog.getSaveFileName(filter="Text files (*.txt)")
        return file if file else ""

    @Bridge(result=str)
    def select_directory(self):
        directory = QFileDialog.getExistingDirectory()
        return directory if directory else ""
```

### 메시지 박스 구현

```python
from PySide6.QtWidgets import QMessageBox
from pyloid import PyloidAPI, Bridge

class MessageAPI(PyloidAPI):
    @Bridge(str, str, result=str)
    def show_info(self, title: str, message: str):
        QMessageBox.information(None, title, message)

    @Bridge(str, str,result=str)
    def show_warning(self, title: str, message: str):
        QMessageBox.warning(None, title, message)

    @Bridge(str, str,result=bool)
    def show_question(self, title: str, message: str):
        reply = QMessageBox.question(None, title, message)
        return reply == QMessageBox.Yes
```

### 사용 방법

1. 커스텀 API 클래스를 정의합니다.
2. Pyloid 애플리케이션 생성 시 API 인스턴스를 전달합니다.

```python
from pyloid import Pyloid

app = Pyloid(app_name="CustomApp")

window = app.create_window(title="Custom API Example", js_apis=[CustomAPI(), MessageAPI()])
window.load_file("path/index.html")
window.show()

app.run()
```

3. HTML/JavaScript에서 API 사용:

```html
<!DOCTYPE html>
<html>
  <body>
    <button id="openFile">파일 열기</button>
    <button id="showMessage">메시지 표시</button>

    <script>
      document.addEventListener('pyloidReady', function () {
        async function openFile() {
          const filePath = await window.pyloid.CustomAPI.open_file();
          console.log('선택된 파일:', filePath);
        }

        async function showMessage() {
          await window.pyloid.MessageAPI.show_info(
            '안내',
            '커스텀 API 테스트입니다.'
          );
        }

        document
          .querySelector('#openFile')
          .addEventListener('click', openFile);
        document
          .querySelector('#showMessage')
          .addEventListener('click', showMessage);
      });
    </script>
  </body>
</html>
```

## QMainWindow 사용하여 원하는 기능 직접 구현

app.create_window() 함수를 통해 생성된 BrowserWindow 인스턴스에서 `get_QMainWindow()` 메서드를 통해 Pyside6의 QMainWindow 인스턴스를 얻을 수 있습니다. 이를 통해 원하는 기능을 직접 구현할 수 있습니다.

```python
from PySide6.QtCore import Qt
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App")

window = app.create_window("pyloid-window")
qmain = window.get_QMainWindow() # return QMainWindow instance

qmain.setWindowFlags(qmain.windowFlags() | Qt.WindowStaysOnTopHint) # window stays on top
```

## 주의사항

1. `@Bridge` 데코레이터를 사용할 때, 입력 매개변수의 타입과 반환 값의 타입을 모두 명시해야 합니다. 예:
   - 입력 매개변수가 없고 문자열을 반환하는 경우: `@Bridge(result=str)`
   - 문자열 두 개를 입력받고 불리언을 반환하는 경우: `@Bridge(str, str, result=bool)`
   - 정수를 입력받고 문자열을 반환하는 경우: `@Bridge(int, result=str)`
2. 복잡한 객체를 반환할 때는 JSON 직렬화가 가능한 형태로 변환해야 합니다.
3. UI 관련 작업은 메인 스레드에서 실행되어야 합니다.

이러한 방식으로 PySide6의 다양한 기능을 Pyloid 애플리케이션에 통합할 수 있습니다. `QtSql`, `QtBluetooth`, `QtMultimedia`, `QtNetwork` 등 더 복잡한 기능도 필요에 따라 구현할 수 있습니다.
