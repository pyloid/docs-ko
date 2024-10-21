# TrayEvent

`TrayEvent`는 시스템 트레이 아이콘과 관련된 이벤트를 나타내는 열거형(Enum) 클래스입니다. 이 클래스는 `QSystemTrayIcon.ActivationReason`에 매핑됩니다.

## 열거형 멤버

- `DoubleClick`: 트레이 아이콘을 더블 클릭했을 때 발생하는 이벤트
- `MiddleClick`: 트레이 아이콘을 중간 버튼으로 클릭했을 때 발생하는 이벤트
- `RightClick`: 트레이 아이콘을 오른쪽 버튼으로 클릭했을 때 발생하는 이벤트 (컨텍스트 메뉴)
- `LeftClick`: 트레이 아이콘을 왼쪽 버튼으로 클릭했을 때 발생하는 이벤트
- `Unknown`: 알 수 없는 이벤트

## 사용 예시

```python
from Pyloid import Pyloid, TrayEvent

app.set_tray_actions(
    {
        TrayEvent.DoubleClick: lambda: print("트레이 아이콘이 더블 클릭되었습니다."),
        TrayEvent.MiddleClick: lambda: print("트레이 아이콘이 중간 버튼으로 클릭되었습니다."),
        TrayEvent.RightClick: lambda: print("트레이 아이콘이 오른쪽 버튼으로 클릭되었습니다."),
        TrayEvent.LeftClick: lambda: print("트레이 아이콘이 왼쪽 버튼으로 클릭되었습니다."),
    }
)
```
