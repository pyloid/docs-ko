# File Watcher

The File Watcher provides functionality to monitor changes in specific files or directories. This allows you to receive automatic notifications when files or directories are modified.

## Basic Usage

### Start Watching a File

To monitor changes in a specific file, use the following:

{% tabs %}
{% tab title="Partial Code" %}
```python
result = app.watch_file("path/file.txt")
if result:
    print("File watching started")
else:
    print("Failed to start file watching")
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

result = app.watch_file("/path/file.txt")
if result:
    print("File watching started")
else:
    print("Failed to start file watching")

app.run()
```
{% endtab %}
{% endtabs %}

### Start Watching a Directory

To monitor changes in a specific directory, use the following:

{% tabs %}
{% tab title="Partial Code" %}
```python
result = app.watch_directory("/path/directory")
if result:
    print("Directory watching started")
else:
    print("Failed to start directory watching")
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

result = app.watch_directory("/path/directory")
if result:
    print("Directory watching started")
else:
    print("Failed to start directory watching")

app.run()
```
{% endtab %}
{% endtabs %}

### Set File Change Callback

You can set a callback function to be executed when a file is changed:

{% tabs %}
{% tab title="Partial Code" %}
```python
def on_file_changed(path):
    print(f"File has been changed: {path}")

app.set_file_change_callback(on_file_changed)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

app.watch_file("/path/file.txt")

# Define callback function
def on_file_changed(path):
    print(f"File has been changed: {path}")

# Set callback function
app.set_file_change_callback(on_file_changed)

app.run()
```
{% endtab %}
{% endtabs %}

### Set Directory Change Callback

You can set a callback function to be executed when a directory is changed:

{% tabs %}
{% tab title="Partial Code" %}
```python
def on_directory_changed(path):
    print(f"Directory has been changed: {path}")

app.set_directory_change_callback(on_directory_changed)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

app.watch_directory("/path/directory")

# Define callback function
def on_directory_changed(path):
    print(f"Directory has been changed: {path}")

# Set callback function
app.set_directory_change_callback(on_directory_changed)

app.run()
```
{% endtab %}
{% endtabs %}

### Stop Watching

To stop watching a specific file or directory, use the following:

{% tabs %}
{% tab title="Partial Code" %}
```python
result = app.stop_watching("/path/to/file_or_directory")
if result:
    print("Watching stopped successfully")
else:
    print("Failed to stop watching")
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()


result = app.stop_watching("/path/to/file_or_directory")
if result:
    print("Watching stopped successfully")
else:
    print("Failed to stop watching")

app.run()
```
{% endtab %}
{% endtabs %}

### Check Watched Paths

To check all currently watched paths (files and directories), use the following:

{% tabs %}
{% tab title="Partial Code" %}
```python
watched_paths = app.get_watched_paths()
print("All watched paths:", watched_paths)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

watched_paths = app.get_watched_paths()
print("All watched paths:", watched_paths)

app.run()
```
{% endtab %}
{% endtabs %}

### Get Only Watched Files

{% tabs %}
{% tab title="Partial Code" %}
```python
watched_files = app.get_watched_files()
print("Watched files:", watched_files)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

watched_files = app.get_watched_files()
print("Watched files:", watched_files)

app.run()
```
{% endtab %}
{% endtabs %}

### Get Only Watched Directories

{% tabs %}
{% tab title="Partial Code" %}
```python
watched_directories = app.get_watched_directories()
print("Watched directories:", watched_directories)
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

watched_directories = app.get_watched_directories()
print("Watched directories:", watched_directories)

app.run()
```
{% endtab %}
{% endtabs %}

### Remove All Watched Paths

{% tabs %}
{% tab title="Partial Code" %}
```python
app.remove_all_watched_paths()
print("All watched paths have been removed.")
```
{% endtab %}

{% tab title="Full Code" %}
```python
from pyloid import Pyloid

app = Pyloid(app_name="Pyloid-App", single_instance=True)

window = app.create_window(
    title="Pyloid Browser",
)

window.load_url("https://www.example.com")
window.show_and_focus()

# Remove all watched paths
app.remove_all_watched_paths()
print("All watched paths have been removed.")

app.run()
```
{% endtab %}
{% endtabs %}

## Usage Example

Here's a comprehensive example of using the File Watcher:

```python
# Start watching file and directory
app.watch_file("/path/to/file1.txt")
app.watch_file("/path/to/file2.txt")
app.watch_file("/path/to/file3.txt")
app.watch_file("/path/to/file4.txt")
app.watch_directory("/path/to/directory1")
app.watch_directory("/path/to/directory2")
app.watch_directory("/path/to/directory3")
app.watch_directory("/path/to/directory4")

# Define callback functions
def on_file_changed(path):
    print(f"File changed: {path}")

def on_directory_changed(path):
    print(f"Directory changed: {path}")

# Set callback functions
app.set_file_change_callback(on_file_changed)
app.set_directory_change_callback(on_directory_changed)

# Check watched paths
print("Watched paths:", app.get_watched_paths())
print("Watched files:", app.get_watched_files())
print("Watched directories:", app.get_watched_directories())

# Stop watching a specific path
app.stop_watching("/path/to/file1.txt")
app.stop_watching("/path/to/file2.txt")
app.stop_watching("/path/to/file3.txt")
app.stop_watching("/path/to/file4.txt")
app.stop_watching("/path/to/directory1")
app.stop_watching("/path/to/directory2")
app.stop_watching("/path/to/directory3")
app.stop_watching("/path/to/directory4")

# Remove all watched paths
app.remove_all_watched_paths()
```

## Precautions

* The File Watcher uses system resources, so use it only when necessary and clean up properly when finished.
* Watching a large number of files or directories can impact system performance, so use caution.
* Some file systems or operating systems may not detect certain types of changes.

This guide should help you understand the basic usage and advanced features of the File Watcher. If you have any additional questions or need further assistance, please don't hesitate to ask.
