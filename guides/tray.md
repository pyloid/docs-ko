# 트레이

Pyloid는 시스템 트레이 기능을 쉽게 구현할 수 있게 해줍니다. 이 가이드에서는 트레이 아이콘 설정, 이벤트 처리, 메뉴 항목 추가, 아이콘 애니메이션, 툴팁 설정 방법을 설명합니다. 모든 트레이 관련 기능은 동적으로 작동하여 앱 실행 중에도 실시간 변경이 가능합니다.

## 트레이 아이콘 설정하기

`set_tray_icon` 메서드를 사용하여 트레이 아이콘을 설정합니다. 이 메서드는 언제든지 호출하여 아이콘을 변경할 수 있습니다:

```python
app.set_tray_icon("assets/icon.ico")
```

참고: 이 메서드는 앱 실행 중에도 호출할 수 있어, 다양한 조건에 따라 아이콘을 동적으로 변경할 수 있습니다.

## 트레이 아이콘 애니메이션

트레이 아이콘에 애니메이션을 적용할 수 있습니다. `set_tray_icon_animation` 메서드를 사용하여 여러 아이콘 프레임을 순차적으로 표시합니다:

```python
app.set_tray_icon_animation(
    [
        "assets/frame1.png",
        "assets/frame2.png",
        "assets/frame3.png",
        "assets/frame4.png",
    ],
    interval=500,
)
```

이 설정은 런타임 중에 변경할 수 있으며, 언제든지 일반 아이콘으로 되돌릴 수 있습니다.

## 트레이 아이콘 툴팁 설정하기

트레이 아이콘에 마우스를 올렸을 때 나타나는 툴팁을 설정할 수 있습니다. `set_tray_tooltip` 메서드를 사용하세요:

```python
app.set_tray_tooltip("이것은 Pyloid 애플리케이션입니다.")
```

툴팁도 앱 실행 중 언제든지 동적으로 변경할 수 있습니다.

## 트레이 이벤트 처리하기

트레이 아이콘의 다양한 클릭 이벤트를 처리할 수 있습니다. `set_tray_actions` 메서드를 사용하여 이벤트 핸들러를 설정합니다. 이 설정도 언제든지 변경할 수 있습니다:

```python
app.set_tray_actions(
    {
        TrayEvent.DoubleClick: lambda: print("트레이 아이콘이 더블 클릭되었습니다."),
        TrayEvent.MiddleClick: lambda: print("트레이 아이콘이 중간 클릭되었습니다."),
        TrayEvent.RightClick: lambda: print("트레이 아이콘이 우클릭되었습니다."),
        TrayEvent.LeftClick: lambda: print("트레이 아이콘이 좌클릭되었습니다."),
    }
)
```

참고: 이벤트 핸들러는 앱 실행 중에 동적으로 추가, 수정 또는 제거할 수 있습니다.

## 트레이 메뉴 항목 추가 및 동적 업데이트

트레이 아이콘을 우클릭할 때 나타나는 컨텍스트 메뉴에 항목을 추가할 수 있습니다. `set_tray_menu_items` 메서드를 사용하여 메뉴 항목을 설정합니다. 이 메뉴 구성도 실시간으로 변경할 수 있습니다:

```python
app.set_tray_menu_items(
    [
        {"label": "창 보이기", "callback": lambda: app.show_and_focus_main_window()},
        {"label": "종료", "callback": lambda: app.quit()},
    ]
)
```

각 메뉴 항목은 `label`과 `callback` 키를 가진 딕셔너리로 정의됩니다. 메뉴 항목은 앱 실행 중에 동적으로 추가, 수정 또는 제거할 수 있습니다.

메뉴를 동적으로 업데이트하는 예:

```python
def update_menu():
    app.set_tray_menu_items(
        [
            {
                "label": "새 메뉴 1",
                "callback": lambda: print("새 메뉴 1 클릭됨"),
            },
            {
                "label": "새 메뉴 2",
                "callback": lambda: print("새 메뉴 2 클릭됨"),
            },
            {"label": "종료", "callback": lambda: app.quit()},
        ]
    )

# 5초 후 트레이 메뉴 업데이트
timer.start_single_shot_timer(5000, update_menu)
```

## 완전한 예제

다음은 트레이 기능을 구현한 완전한 예제입니다. 모든 설정이 동적으로 변경될 수 있음을 보여줍니다:

```python
import os
from pyloid import PyloidApp, TrayEvent, is_production, get_production_path, PyloidTimer


app = PyloidApp("Pyloid-App", single_instance=True)
timer = PyloidTimer()

if (is_production()):
    app.set_icon(os.path.join(get_production_path(), "icon.ico"))
    app.set_tray_icon(os.path.join(get_production_path(), "icon.ico"))
else:
    app.set_icon("assets/icon.ico")
    app.set_tray_icon("assets/icon.ico")

app.set_tray_actions(
    {
        TrayEvent.DoubleClick: lambda: print("트레이 아이콘이 더블 클릭되었습니다."),
        TrayEvent.MiddleClick: lambda: print("트레이 아이콘이 중간 클릭되었습니다."),
        TrayEvent.RightClick: lambda: print("트레이 아이콘이 우클릭되었습니다."),
        TrayEvent.LeftClick: lambda: print("트레이 아이콘이 좌클릭되었습니다."),
    }
)

app.set_tray_menu_items(
    [
        {"label": "창 보이기", "callback": lambda: app.show_and_focus_main_window()},
        {"label": "종료", "callback": lambda: app.quit()},
    ]
)

# 트레이 아이콘 툴팁 설정
app.set_tray_tooltip("이것은 Pyloid 애플리케이션입니다.")

def update_menu():
    app.set_tray_menu_items(
        [
            {
                "label": "새 메뉴 1",
                "callback": lambda: print("새 메뉴 1 클릭됨"),
            },
            {
                "label": "새 메뉴 2",
                "callback": lambda: print("새 메뉴 2 클릭됨"),
            },
            {"label": "종료", "callback": lambda: app.quit()},
        ]
    )

def update_tray_icon():
    # 트레이 아이콘 애니메이션 설정
    app.set_tray_icon_animation(
        [
            "assets/frame1.png",
            "assets/frame2.png",
            "assets/frame3.png",
            "assets/frame4.png",
        ],
        interval=500,
    )

# 5초 후 트레이 메뉴 업데이트
timer.start_single_shot_timer(5000, update_menu)

# 3초 후 트레이 아이콘 애니메이션 시작
timer.start_single_shot_timer(3000, update_tray_icon)

# 6초 후 트레이 아이콘을 정적 아이콘으로 변경
timer.start_single_shot_timer(6000, lambda: app.set_tray_icon("assets/icon.ico"))

# 10초 후 트레이 아이콘 툴팁 변경
timer.start_single_shot_timer(10000, lambda: app.set_tray_tooltip("새로운 툴팁!"))
```

이 예제는 트레이 아이콘 설정, 이벤트 처리, 메뉴 항목 추가, 아이콘 애니메이션, 툴팁 설정을 보여줍니다. 모든 설정은 앱 실행 중에 동적으로 변경할 수 있어, 필요에 따라 트레이 기능을 실시간으로 업데이트할 수 있습니다.
