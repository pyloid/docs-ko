# Window Customization

By using the `data-pyloid-drag-region` attribute, you can make HTML elements draggable. Below is a description of how to customize the window title bar using this attribute.

## Basic Setup

First, when creating a window in `main.py`, pass the `frame=False` argument to remove the default frame.

```python
window = app.create_window(title="Draggable Region", frame=False)
```

In the HTML document, add the `data-pyloid-drag-region` attribute to the element you want to make draggable. For example, you can add this attribute to a `div` element as follows:

```html
<div data-pyloid-drag-region>Draggable Area</div>
```

## Example Usage

Below is an example of an HTML document that includes a draggable area using the `data-pyloid-drag-region` attribute:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script src="qrc:///qtwebchannel/qwebchannel.js"></script>
    <script>
      document.addEventListener('pyloidReady', function () {
        console.log('pyloidReady');
      });
    </script>
    <title>Draggable Region</title>
  </head>
  <body>
    <div data-pyloid-drag-region>Draggable Area</div>
    <h1>Hello</h1>
  </body>
</html>
```

By using the `data-pyloid-drag-region` attribute in this way, you can set the desired elements as draggable areas. This allows you to freely customize the window title bar.
