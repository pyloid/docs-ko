# 창 사용자 정의

`data-pyloid-drag-region` 속성을 사용하여 HTML 요소를 드래그 가능하게 만들 수 있습니다. 아래는 이 속성을 사용하여 창 제목 표시줄을 사용자 정의하는 방법에 대한 설명입니다.

## 기본 설정

먼저, `main.py`에서 창을 생성할 때 기본 프레임을 제거하기 위해 `frame=False` 인수를 전달합니다.

```python
window = app.create_window(title="드래그 가능 영역", frame=False)
```

HTML 문서에서 드래그 가능하게 만들고 싶은 요소에 `data-pyloid-drag-region` 속성을 추가합니다. 예를 들어, `div` 요소에 이 속성을 다음과 같이 추가할 수 있습니다:

```html
<div data-pyloid-drag-region>드래그 가능 영역</div>
```

## 사용 예시

다음은 `data-pyloid-drag-region` 속성을 사용하여 드래그 가능한 영역을 포함하는 HTML 문서의 예시입니다:

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    />
    <script src="qrc:///qtwebchannel/qwebchannel.js"></script>
    <script>
      document.addEventListener('pyloidReady', function () {
        console.log('pyloidReady');
      });
    </script>
    <title>드래그 가능 영역</title>
  </head>
  <body>
    <div data-pyloid-drag-region>드래그 가능 영역</div>
    <h1>안녕하세요</h1>
  </body>
</html>
```

이와 같이 `data-pyloid-drag-region` 속성을 사용하면 원하는 요소를 드래그 가능한 영역으로 설정할 수 있습니다. 이를 통해 창 제목 표시줄을 자유롭게 사용자 정의할 수 있습니다.
