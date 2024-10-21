# Clipboard

Pyloid provides easy-to-use clipboard functionality. You can copy text and images to the clipboard or retrieve them from the clipboard.

## Text Operations

### Copying Text to Clipboard

```python
app.copy_to_clipboard("Text to be copied")
```

You can use this function to copy desired text to the clipboard.

### Getting Text from Clipboard

```python
text = app.get_clipboard_text()
print(text)
```

You can use this function to retrieve the text currently on the clipboard.

## Image Operations

### Copying Image to Clipboard

```python
app.set_clipboard_image("assets/icon.png")
```

You can use this function to copy an image file to the clipboard. Just pass the file path as a string.

### Getting Image from Clipboard

```python
image = app.get_clipboard_image()
if image:
    print("Successfully retrieved the image.")
else:
    print("No image on the clipboard.")
```

You can use this function to retrieve the image currently on the clipboard. The returned image is of QImage type. If there's no image on the clipboard, it returns `None`.

With the QImage object, you can perform various operations such as image processing, display, saving, etc.

## Notes

* The `set_clipboard_image` function can accept not only image file paths but also byte data or `os.PathLike` objects.
* The `get_clipboard_image` function returns a QImage object. You can use this for image processing, display, and other operations.
