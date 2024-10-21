# EventAPI

## EventAPI (JavaScript) Documentation

`EventAPI` provides methods for handling events in JavaScript frontend that originate from Python in Pyloid applications. This API allows you to receive and manage events sent from Python in the frontend.

To execute Python from JavaScript, you need to use `PyloidAPI`. For more details, refer to the [PyloidAPI documentation](../python-backend/pyloidapi.md).

### Usage

Methods of `EventAPI` can be called using `window.pyloid.EventAPI.<methodName>()`.

***

#### 1. `listen(eventName: string, callback: function)`

* **Description**: Listens for a specified event sent from Python and executes a callback function.
* **Parameters**:
  * `eventName` (`string`): Name of the event to listen for
  * `callback` (`function`): Callback function to be executed when the event is received
* **Return value**: None

**Usage example**:

```javascript
window.pyloid.EventAPI.listen('pythonEvent', function (eventData) {
  console.log('Received event from Python:', eventData);
});
```

#### 2. `unlisten(eventName: string)`

* **Description**: Stops listening for a specified Python event.
* **Parameters**:
  * `eventName` (`string`): Name of the event to stop listening for
* **Return value**: None

**Usage example**:

```javascript
window.pyloid.EventAPI.unlisten('pythonEvent');
```

***

### Emitting Events from Python

To emit events from Python to JavaScript, use the `emit` method of the `WindowBrowser` class.

#### `emit(event_name: str, data: Optional[Dict] = None)`

* **Description**: Emits an event from Python to the JavaScript side.
* **Parameters**:
  * `event_name` (`str`): Name of the event to emit
  * `data` (`Optional[Dict]`): Data to send along with the event (optional)

**Usage example**:

```python
# Emitting a simple event
window.emit('simpleEvent')

# Emitting an event with data
user_data = {
    'id': 1,
    'name': 'John Doe',
    'email': 'john@example.com'
}
window.emit('userDataUpdate', user_data)
```

Here's an example of using `EventAPI` to receive and handle events sent from Python:

```javascript
// Setting up Python event listeners
window.pyloid.EventAPI.listen('simpleEvent', function () {
  console.log('Received simple event from Python');
});

window.pyloid.EventAPI.listen('userDataUpdate', function (userData) {
  console.log('Received user data update from Python:', userData);
});

// Later, to stop listening for events
function cleanupEventListeners() {
  window.pyloid.EventAPI.unlisten('simpleEvent');
  window.pyloid.EventAPI.unlisten('userDataUpdate');
}
```

In this example, we use the `emit` method of the `WindowBrowser` instance to emit two events:

1. `'simpleEvent'`: Simply emits an event without any data.
2. `'userDataUpdate'`: Emits an event with user data.

These emitted events can be received and handled on the JavaScript side using the `EventAPI.listen` method.

***

### Notes

* The `listen` method automatically parses event data sent from Python and converts it to a JSON object. If parsing fails, it passes the original data as is.
* Use the `unlisten` method to remove event listeners. This helps prevent memory leaks.
* You can listen for multiple Python events simultaneously, with separate `listen` calls for each event.

Using this API, you can effectively manage real-time communication between Python and the JavaScript frontend.
