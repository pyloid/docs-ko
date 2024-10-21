# Notification

You can display notifications to users using the `show_notification()` method of Pyloid.

## Usage

```python
app.show_notification(title, message)
```

### Parameters

* `title` (string): The title of the notification
* `message` (string): The content of the notification message

### Example

```python
app.show_notification("Notification", "Notification message")
```

This code displays a notification with the title "Notification" and the content "Notification message".

## Setting a Notification Click Callback

You can set a callback function to be executed when a notification is clicked.

### Usage

```python
app.set_notification_callback(callback_function)
```

### Parameters

* `callback_function` (function): The function to be executed when the notification is clicked

### Example

```python
def on_notification_clicked():
    print("The notification was clicked!")

app.set_notification_callback(on_notification_clicked)

# Display a new notification
app.show_notification("New Notification", "Click this notification!")
```

This code sets up a notification click callback and displays a new notification. When the user clicks the notification, the message "The notification was clicked!" will be printed.
