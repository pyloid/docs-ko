# Timer

`PyloidTimer` is a convenient timer management class based on PySide6's QTimer. It allows you to easily create and manage various types of timers.

## Table of Contents

1. [Basic Usage](timer.md#basic-usage)
2. [Periodic Timers](timer.md#periodic-timers)
3. [Single-Shot Timers](timer.md#single-shot-timers)
4. [Timer Management](timer.md#timer-management)
5. [Precise Timers](timer.md#precise-timers)
6. [Advanced Usage](timer.md#advanced-usage)

## Basic Usage

First, create a `PyloidTimer` instance:

```python
from pyloid.timer import PyloidTimer

timer_manager = PyloidTimer()
```

## Periodic Timers

To start a timer that runs periodically, use the `start_periodic_timer` method:

{% tabs %}
{% tab title="Partial Code" %}
```python
def print_hello():
    print("Hello!")

# Start a timer that prints "Hello!" every 2 seconds
timer_id = timer_manager.start_periodic_timer(2000, print_hello)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import  Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

def print_hello():
    print("Hello!")

# Start a timer that prints "Hello!" every 2 seconds
timer_id = timer_manager.start_periodic_timer(2000, print_hello)

app.run()
```
{% endtab %}
{% endtabs %}

## Single-Shot Timers

To start a timer that runs only once, use the `start_single_shot_timer` method:

{% tabs %}
{% tab title="Partial Code" %}
```python
def delayed_message():
    print("5 seconds have passed!")

# Start a single-shot timer that prints a message after 5 seconds
timer_id = timer_manager.start_single_shot_timer(5000, delayed_message)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

def delayed_message():
    print("5 seconds have passed!")

# Start a single-shot timer that prints a message after 5 seconds
timer_id = timer_manager.start_single_shot_timer(5000, delayed_message)

app.run()
```
{% endtab %}
{% endtabs %}

## Timer Management

### Stopping a Timer

{% tabs %}
{% tab title="Partial Code" %}
```python
# Stop a timer using its ID
timer_manager.stop_timer(timer_id)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# Start a timer
timer_id = timer_manager.start_periodic_timer(2000, lambda: print("Hello!"))

# Stop a timer using its ID
timer_manager.stop_timer(timer_id)

app.run()
```
{% endtab %}
{% endtabs %}

### Checking Timer Activity

{% tabs %}
{% tab title="Partial Code" %}
```python
if timer_manager.is_timer_active(timer_id):
    print("The timer is still running.")
else:
    print("The timer has stopped.")
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# Start a timer
timer_id = timer_manager.start_periodic_timer(2000, lambda: print("Hello!"))

# Check if the timer is active
if timer_manager.is_timer_active(timer_id):
    print("The timer is still running.")
else:
    print("The timer has stopped.")

app.run()
```
{% endtab %}
{% endtabs %}

### Checking Remaining Time

{% tabs %}
{% tab title="Partial Code" %}
```python
remaining_time = timer_manager.get_remaining_time(timer_id)
if remaining_time is not None:
    print(f"{remaining_time}ms left until the timer fires.")
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# Start a timer
timer_id = timer_manager.start_periodic_timer(2000, lambda: print("Hello!"))

# Check remaining time
remaining_time = timer_manager.get_remaining_time(timer_id)
if remaining_time is not None:
    print(f"{remaining_time}ms left until the timer fires.")

app.run()
```
{% endtab %}
{% endtabs %}

### Changing Timer Interval

{% tabs %}
{% tab title="Partial Code" %}
```python
# Change the timer interval to 3 seconds
timer_manager.set_interval(timer_id, 3000)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

# Start a timer
timer_id = timer_manager.start_periodic_timer(1000, lambda: print("Hello!"))

# Change the timer interval to 3 seconds
timer_manager.set_interval(timer_id, 3000)

app.run()
```
{% endtab %}
{% endtabs %}

## Precise Timers

For more precise timing, you can use precise timers:

{% tabs %}
{% tab title="Partial Code" %}
```python
def precise_task():
    print("Executing precise task")

# Start a precise periodic timer with 100ms interval
precise_timer_id = timer_manager.start_precise_periodic_timer(100, precise_task)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

def precise_task():
    print("Executing precise task")

# Start a precise periodic timer with 100ms interval
precise_timer_id = timer_manager.start_precise_periodic_timer(100, precise_task)

app.run()
```
{% endtab %}
{% endtabs %}

## Advanced Usage

### Using Lambda Functions

{% tabs %}
{% tab title="Partial Code" %}
```python
counter = 0

def count():
    global counter
    counter += 1
    print(f"Counter: {counter}")

timer_id = timer_manager.start_periodic_timer(1000, count)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid.timer import PyloidTimer
from pyloid import Pyloid

# Create a PyloidTimer instance
app = Pyloid(app_name="Pyloid-App")
timer_manager = PyloidTimer()

counter = 0

def count():
    global counter
    counter += 1
    print(f"Counter: {counter}")

timer_id = timer_manager.start_periodic_timer(1000, count)

app.run()
```
{% endtab %}
{% endtabs %}

## Conclusion

`PyloidTimer` is a powerful tool for managing various timing requirements easily. It can be useful in a wide range of situations, from simple periodic tasks to tasks that require precise timing.
