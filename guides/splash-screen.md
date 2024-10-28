# 스플래시 스크린

애플리케이션 로딩 중에 표시되는 스플래시 스크린 기능을 제공합니다.

## 기본 사용법

### 1. 스플래시 스크린 설정

#### 정적 이미지 스플래시 스크린

```python
app = Pyloid(app_name="Pyloid-App")

window = app.create_window("Splash Screen Example")
window.set_static_image_splash_screen(image_path="./assets/loading.png")
```

#### 매개변수

- `image_path`: 이미지 파일 경로
- `close_on_load`: 페이지 로드 완료 시 자동 종료 여부 (기본값: True)
- `stay_on_top`: 항상 위에 표시 여부 (기본값: True)
- `clickable`: 클릭으로 닫기 가능 여부 (기본값: True)
- `position`: 스플래시 스크린 위치 (기본값: "center")
  - 지원 위치: "center", "top-left", "top-right", "bottom-left", "bottom-right"

#### GIF 스플래시 스크린

```python
window.set_gif_splash_screen(gif_path="./assets/loading.gif")
```

#### 매개변수

- `gif_path`: GIF 파일 경로
- `close_on_load`: 페이지 로드 완료 시 자동 종료 여부 (기본값: True)
- `stay_on_top`: 항상 위에 표시 여부 (기본값: True)
- `clickable`: 클릭으로 닫기 가능 여부 (기본값: True)
- `position`: 스플래시 스크린 위치 (기본값: "center")
  - 지원 위치: "center", "top-left", "top-right", "bottom-left", "bottom-right"

### 2. 스플래시 스크린 제어

#### 수동으로 스플래시 스크린 닫기

```python
window.close_splash_screen()
```

#### 스레드를 이용한 제어 예제

```python
from PySide6.QtCore import QThread
import time

# ... window 객체는 이미 생성되어 있는 상태라고 가정

class SplashWorkerThread(QThread):
    def run(self):
        # 여기에 초기화 작업 코드 작성
        time.sleep(2)  # 예: 2초 대기

def finish_callback():
    window.close_splash_screen()
    window.show_and_focus()

# 스레드 생성 및 시작
splash_worker = SplashWorkerThread()
splash_worker.finished.connect(finish_callback)
splash_worker.start()
```

## 활용 시나리오

1. **초기 로딩 화면**

   - 애플리케이션 시작 시 리소스 로딩
   - 데이터베이스 연결
   - 외부 API 초기화

2. **긴 작업 진행 중 표시**
   - 대용량 파일 처리
   - 네트워크 작업
   - 복잡한 계산 작업

## 주의사항

1. GIF 파일은 적절한 크기와 화질로 최적화하여 사용
2. `close_on_load=False` 설정 시 수동으로 스플래시 스크린을 닫아야 함
3. 스레드 사용 시 예외 처리 고려 필요
