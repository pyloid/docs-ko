# WindowAPI

## WindowAPI (JavaScript) 문서

`WindowAPI`는 Pyloid 애플리케이션에서 창과 상호 작용하기 위한 다양한 메서드를 제공합니다. 각 메서드는 JavaScript를 통해 `window.pyloid.WindowAPI`로 사용할 수 있으며, 비동기 작업을 위해 `await`를 사용하거나 Promise로 호출할 수 있습니다. 아래는 이 API를 통해 사용 가능한 각 메서드에 대한 자세한 설명입니다.

### 사용법

`WindowAPI`의 모든 메서드를 사용하려면 간단히 `window.pyloid.WindowAPI.<메서드명>()`으로 호출하면 됩니다. 대부분의 메서드는 Promise를 반환하며 비동기 환경에서 동기적 동작을 위해 `await`와 함께 사용할 수 있습니다.

---

#### 1. `getWindowId()`

- **설명**: 현재 창의 ID를 반환합니다.
- **반환**: `Promise<string>` - 창 ID를 문자열로 반환합니다.

**사용 예**:

```javascript
const windowId = await window.pyloid.WindowAPI.getWindowId();
console.log(windowId);
```

#### 2. `close()`

- **설명**: 현재 창을 닫습니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.close();
```

#### 3. `hide()`

- **설명**: 현재 창을 숨깁니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.hide();
```

#### 4. `show()`

- **설명**: 현재 창을 보여주고 포커스를 맞춥니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.show();
```

#### 5. `focus()`

- **설명**: 현재 창에 포커스를 맞춥니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.focus();
```

#### 6. `showAndFocus()`

- **설명**: 현재 창을 보여주고 포커스를 맞춥니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.showAndFocus();
```

#### 7. `fullscreen()`

- **설명**: 현재 창을 전체 화면 모드로 전환합니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.fullscreen();
```

#### 8. `toggleFullscreen()`

- **설명**: 현재 창의 전체 화면 모드를 전환합니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.toggleFullscreen();
```

#### 9. `minimize()`

- **설명**: 현재 창을 최소화합니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.minimize();
```

#### 10. `maximize()`

- **설명**: 현재 창을 최대화합니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.maximize();
```

#### 11. `unmaximize()`

- **설명**: 창을 정상 상태로 복원합니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.unmaximize();
```

#### 12. `toggleMaximize()`

- **설명**: 현재 창의 최대화 상태를 전환합니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.toggleMaximize();
```

#### 13. `isFullscreen()`

- **설명**: 현재 창이 전체 화면 모드인지 확인합니다.
- **반환**: `Promise<boolean>` - 전체 화면이면 `true`, 아니면 `false`를 반환합니다.

**사용 예**:

```javascript
const isFullscreen = await window.pyloid.WindowAPI.isFullscreen();
console.log(isFullscreen);
```

#### 14. `isMaximized()`

- **설명**: 현재 창이 최대화되었는지 확인합니다.
- **반환**: `Promise<boolean>` - 최대화되었으면 `true`, 아니면 `false`를 반환합니다.

**사용 예**:

```javascript
const isMaximized = await window.pyloid.WindowAPI.isMaximized();
console.log(isMaximized);
```

#### 15. `setTitle(title: string)`

- **설명**: 창의 제목을 설정합니다.
- **매개변수**:
  - `title` (`string`): 창에 설정할 제목입니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.setTitle('내 앱 창');
```

#### 16. `setSize(width: number, height: number)`

- **설명**: 창의 크기를 설정합니다.
- **매개변수**:
  - `width` (`number`): 창의 원하는 너비입니다.
  - `height` (`number`): 창의 원하는 높이입니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.setSize(800, 600);
```

#### 17. `setPosition(x: number, y: number)`

- **설명**: 창의 위치를 설정합니다.
- **매개변수**:
  - `x` (`number`): 창 위치의 x 좌표입니다.
  - `y` (`number`): 창 위치의 y 좌표입니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.setPosition(100, 100);
```

#### 18. `setFrame(frame: boolean)`

- **설명**: 창의 프레임(예: 창 테두리)을 설정합니다.
- **매개변수**:
  - `frame` (`boolean`): 프레임을 표시하려면 `true`, 숨기려면 `false`입니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.setFrame(true);
```

#### 19. `setContextMenu(contextMenu: boolean)`

- **설명**: 창의 컨텍스트 메뉴 표시 여부를 설정합니다.
- **매개변수**:
  - `contextMenu` (`boolean`): 컨텍스트 메뉴를 활성화하려면 `true`, 비활성화하려면 `false`입니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
await window.pyloid.WindowAPI.setContextMenu(false);
```

#### 20. `setDevTools(enable: boolean)`

- **설명**: 창의 개발자 도구를 활성화하거나 비활성화합니다. 또한 `F12` 키를 사용하여 개발자 도구를 열 수 있는지 여부를 설정합니다.
- **매개변수**:
  - `enable` (`boolean`):
    - `true`로 설정하면 개발자 도구를 활성화하고 `F12`로 열 수 있습니다.
    - `false`로 설정하면 개발자 도구를 비활성화하고 `F12`로 열 수 없습니다.
- **반환**: `Promise<void>`

**사용 예**:

```javascript
// 개발자 도구를 활성화하고 F12로 열 수 있게 합니다
await window.pyloid.WindowAPI.setDevTools(true);

// 개발자 도구를 비활성화하고 F12로 열 수 없게 합니다
await window.pyloid.WindowAPI.setDevTools(false);
```

#### 21. `capture(savePath: string)`

- **설명**: 현재 창의 뷰를 캡처하여 지정된 경로에 저장합니다.
- **매개변수**:
  - `savePath` (`string`): 캡처된 이미지를 저장할 파일 경로입니다.
- **반환**: `Promise<string | null>` - 성공 시 파일 경로, 실패 시 `null`을 반환합니다.

**사용 예**:

```javascript
const filePath = await window.pyloid.WindowAPI.capture(
  '/path/to/save/screenshot.png'
);
if (filePath) {
  console.log(`스크린샷이 ${filePath}에 저장되었습니다`);
} else {
  console.log('캡처에 실패했습니다');
}
```

---

### 참고사항

- 모든 메서드는 `Promise`를 반환하므로 비동기 함수에서 `await`와 함께 사용할 수 있습니다.
- 이러한 API를 책임감 있게 사용하세요. 일부 동작(예: 창 닫기 또는 최소화)은 사용자 경험에 영향을 줄 수 있습니다.
