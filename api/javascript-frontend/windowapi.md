# WindowAPI

## WindowAPI (JavaScript) Documentation

The `WindowAPI` provides various methods to interact with a window in the Pyloid application. Each method is available through JavaScript using `window.pyloid.WindowAPI` and can be called with `await` for asynchronous operation or as a Promise. Below is a detailed overview of each method available through this API.

### Usage

To use any method in the `WindowAPI`, simply call it using `window.pyloid.WindowAPI.<methodName>()`. Most methods return a Promise and can be used with `await` for synchronous-like behavior in an asynchronous environment.

***

#### 1. `getWindowId()`

* **Description**: Returns the current window's ID.
* **Returns**: `Promise<string>` - The window ID as a string.

**Usage**:

```javascript
const windowId = await window.pyloid.WindowAPI.getWindowId();
console.log(windowId);
```

#### 2. `close()`

* **Description**: Closes the current window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.close();
```

#### 3. `hide()`

* **Description**: Hides the current window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.hide();
```

#### 4. `show()`

* **Description**: Shows and focuses the current window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.show();
```

#### 5. `toggleFullscreen()`

* **Description**: Toggles fullscreen mode for the current window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.toggleFullscreen();
```

#### 6. `minimize()`

* **Description**: Minimizes the current window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.minimize();
```

#### 7. `maximize()`

* **Description**: Maximizes the current window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.maximize();
```

#### 8. `unmaximize()`

* **Description**: Restores the window to its normal state.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.unmaximize();
```

#### 9. `setTitle(title: string)`

* **Description**: Sets the title of the window.
* **Parameters**:
  * `title` (`string`): The title to set for the window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.setTitle("My App Window");
```

#### 10. `setSize(width: number, height: number)`

* **Description**: Sets the size of the window.
* **Parameters**:
  * `width` (`number`): The desired width of the window.
  * `height` (`number`): The desired height of the window.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.setSize(800, 600);
```

#### 11. `setPosition(x: number, y: number)`

* **Description**: Sets the position of the window.
* **Parameters**:
  * `x` (`number`): The x-coordinate for the window position.
  * `y` (`number`): The y-coordinate for the window position.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.setPosition(100, 100);
```

#### 12. `setFrame(frame: boolean)`

* **Description**: Sets the frame of the window (e.g., window border).
* **Parameters**:
  * `frame` (`boolean`): `true` to show the frame, `false` to hide it.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.setFrame(true);
```

#### 13. `setContextMenu(contextMenu: boolean)`

* **Description**: Sets the context menu visibility for the window.
* **Parameters**:
  * `contextMenu` (`boolean`): `true` to enable the context menu, `false` to disable it.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
await window.pyloid.WindowAPI.setContextMenu(false);
```

#### 14. `setDevTools(enable: boolean)`

* **Description**: Enables or disables the developer tools for the window. Additionally, it allows or disallows opening the developer tools using the `F12` key.
* **Parameters**:
  * `enable` (`boolean`):
    * `true` to enable dev tools and allow opening with `F12`.
    * `false` to disable dev tools and prevent opening with `F12`.
* **Returns**: `Promise<void>`

**Usage**:

```javascript
// Enable developer tools and allow opening with F12
await window.pyloid.WindowAPI.setDevTools(true);

// Disable developer tools and prevent opening with F12
await window.pyloid.WindowAPI.setDevTools(false);
```

#### 15. `capture(savePath: string)`

* **Description**: Captures the current window's view and saves it to the specified path.
* **Parameters**:
  * `savePath` (`string`): The file path where the captured image should be saved.
* **Returns**: `Promise<string | null>` - The file path if successful, otherwise `null`.

**Usage**:

```javascript
const filePath = await window.pyloid.WindowAPI.capture('/path/to/save/screenshot.png');
if (filePath) {
  console.log(`Screenshot saved to ${filePath}`);
} else {
  console.log('Capture failed');
}
```

***

### Notes

* All methods return a `Promise`, allowing them to be used with `await` in asynchronous functions.
* Use these APIs responsibly, as some actions (e.g., closing or minimizing the window) can affect the user experience.
