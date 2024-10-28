# 스레드

멀티 스레드 작업을 위해 PySide6의 QThread 클래스를 사용합니다.

## QThread 기본 사용법

### 1. QThread 클래스 상속

```python
from PySide6.QtCore import QThread

class WorkerThread(QThread):
    def run(self):
        # 여기에 실행할 작업 코드를 작성합니다
        pass
```

### 2. 시그널 정의 (선택사항)

```python
from PySide6.QtCore import QThread, Signal

class WorkerThread(QThread):
    progress = Signal(int)  # 진행상황을 알리는 시그널
    result = Signal(object)  # 결과를 전달하는 시그널

    def run(self):
        # 작업 진행 중 시그널 발생
        self.progress.emit(50)
        # 작업 결과 전달
        self.result.emit("작업완료")
```

### 3. 스레드 사용 예시

```python
def on_finished():
    print("작업이 완료되었습니다")

def on_progress(value):
    print(f"진행률: {value}%")


# 스레드 인스턴스 생성
worker = WorkerThread()

worker.finished.connect(on_finished)  # 작업 완료 시 호출될 콜백

worker.progress.connect(on_progress)  # 진행상황 업데이트 시 호출될 콜백

# 스레드 시작
worker.start()

```

## 주요 메서드와 시그널

### QThread 기본 메서드

- `start()`: 스레드 시작
- `quit()`: 스레드 종료 요청
- `wait()`: 스레드가 종료될 때까지 대기
- `isRunning()`: 스레드 실행 여부 확인
- `terminate()`: 스레드 강제 종료 (권장하지 않음)

### 기본 시그널

- `started`: 스레드가 시작될 때 발생
- `finished`: 스레드가 종료될 때 발생

## 주의사항

1. GUI 업데이트는 메인 스레드에서만 수행해야 합니다.
2. `terminate()`는 리소스 정리 없이 강제 종료되므로 사용을 피해야 합니다.
3. 스레드 간 데이터 공유 시 적절한 동기화가 필요합니다.

## 예제: 진행 상황 표시 작업

```python
from PySide6.QtCore import QThread, Signal
import time

class WorkerThread(QThread):
    progress = Signal(int)

    def run(self):
        for i in range(101):
            self.progress.emit(i)
            time.sleep(0.1)  # 작업 시뮬레이션

# 사용 예시
worker = WorkerThread()
worker.progress.connect(lambda v: print(f"진행률: {v}%"))
worker.finished.connect(lambda: print("작업 완료!"))
worker.start()
```

이 가이드는 PySide6에서 QThread를 사용하여 멀티스레딩을 구현하는 기본적인 방법을 설명합니다.
실제 애플리케이션에서는 작업의 특성에 따라 적절한 시그널과 슬롯을 설계하여 사용하시기 바랍니다.
