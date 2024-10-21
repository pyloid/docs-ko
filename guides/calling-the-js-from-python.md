# Calling the JS from Python

This guide explains how to call JavaScript functions from Python code.

## 1. JavaScript Side Setup

First, we need to prepare the JavaScript code to receive events coming from Python.

```javascript
document.addEventListener('pyloidReady', function () {
  window.pyloid.EventAPI.listen('pythonEvent', function (data) {
    console.log('Received event from Python:', data.message);
  });
});
```

This code does the following:

1. Waits for the `pyloidReady` event. This event occurs when the Pyloid environment is fully loaded.
2. Once the Pyloid environment is ready, it starts listening for an event named 'pythonEvent' using the `window.pyloid.EventAPI.listen` method.
3. When 'pythonEvent' occurs, it logs the `message` property of the passed data to the console.

## 2. Triggering Events from Python

In Python code, you can trigger events to JavaScript like this:

```python
window.emit('pythonEvent', { "message": 'Hello from Python!' })
```

This code does the following:

1. Uses the `window.emit` function to trigger an event named 'pythonEvent'.
2. Passes a data object along with the event. This object has a "message" key with the value 'Hello from Python!'.

Here, `window` is the `BrowserWindow` object created through the `create_window(...)` method.

## How It Works

1. The JavaScript code runs and sets up the 'pythonEvent' event listener.
2. The Python code runs and triggers 'pythonEvent', passing a message.
3. The JavaScript event listener detects this event and logs the passed message to the console.

## Precautions

* The JavaScript code must be loaded before the Python code runs. Otherwise, the event listener may not be set up, and it won't be able to receive events triggered from Python.
* JSON format is used for data transmission, so complex data structures can also be passed.
* For security reasons, care should be taken to only pass necessary data.

Using this method enables two-way communication between Python and JavaScript, allowing for more dynamic and interactive applications.
