# 테마

## 시스템 테마 연동하기

Pyloid는 사용자의 시스템 테마 설정을 자동으로 감지하여 적용할 수 있습니다. CSS 변수를 활용하여 라이트/다크 모드에 따른 스타일을 쉽게 관리할 수 있습니다.

### 기본 설정

```css
/* 라이트 모드 테마 */
[data-pyloid-theme='light'] {
  --background-color: white;
  --font-color: #333333;
}

/* 다크 모드 테마 */
[data-pyloid-theme='dark'] {
  --background-color: #333333;
  --font-color: white;
}

/* CSS 변수 적용 */
body {
  background-color: var(--background-color);
  color: var(--font-color);
}
```

### 동작 방식

1. `data-pyloid-theme` 속성은 시스템의 테마 설정에 따라 자동으로 'light' 또는 'dark' 값으로 설정됩니다.
2. CSS 변수를 사용하여 각 테마별 스타일을 정의합니다.
3. 컴포넌트에서는 정의된 CSS 변수를 참조하여 스타일이 적용됩니다.

### 예제

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      [data-pyloid-theme='light'] {
        --background-color: white;
        --font-color: #333333;
      }

      [data-pyloid-theme='dark'] {
        --background-color: #333333;
        --font-color: white;
      }

      body {
        background-color: var(--background-color);
        color: var(--font-color);
      }
    </style>
  </head>

  <body>
    <div class="card">
      <h1>다크모드 테스트</h1>
      <p>
        이 페이지는 시스템의 다크모드 설정에 따라 자동으로 테마가 변경됩니다.
      </p>
    </div>
  </body>
</html>
```

### 커스텀 테마 변수

자주 사용되는 테마 변수들:

```css
[data-pyloid-theme='light'] {
  --primary-color: #007bff;
  --secondary-color: #6c757d;
  --background-color: white;
  --surface-color: #f8f9fa;
  --font-color: #333333;
  --border-color: #dee2e6;
}

[data-pyloid-theme='dark'] {
  --primary-color: #0d6efd;
  --secondary-color: #6c757d;
  --background-color: #333333;
  --surface-color: #424242;
  --font-color: white;
  --border-color: #495057;
}
```

## 수동 테마 전환

필요한 경우 JavaScript를 통해 수동으로 테마를 전환할 수 있습니다:

```javascript
// 다크 모드로 전환
document.documentElement.setAttribute('data-pyloid-theme', 'dark');

// 라이트 모드로 전환
document.documentElement.setAttribute('data-pyloid-theme', 'light');
```

## 테마 변경 감지하기

Pyloid는 테마가 변경될 때 `themeChange` 커스텀 이벤트를 발생시킵니다. 이 이벤트를 활용하여 테마 변경 시 필요한 작업을 수행할 수 있습니다.

### 이벤트 리스너 등록

```javascript
document.addEventListener('themeChange', (e) => {
    console.log('테마 변경됨:', e.detail.theme); // 'light' 또는 'dark'

    updateTheme(e.detail.theme);
});
```

### 활용 예시

1. 테마별 이미지 변경:
```javascript
function updateTheme(theme) {
    const logo = document.querySelector('.logo');
    if (theme === 'dark') {
        logo.src = '/images/logo-dark.png';
    } else {
        logo.src = '/images/logo-light.png';
    }
}
```

2. API 호출 시 테마 정보 전달:
```javascript
function updateTheme(theme) {
    // 사용자 설정 저장
    fetch('/api/user/preferences', {
        method: 'POST',
        body: JSON.stringify({ theme: theme }),
        headers: {
            'Content-Type': 'application/json'
        }
    });
}
```

### 주의사항

- `themeChange` 이벤트는 처음 시작 시와 시스템 테마가 변경될 때 발생합니다.
- `e.detail.theme`에는 'light' 또는 'dark' 값이 포함됩니다.

이러한 이벤트 리스너를 활용하면 테마 변경에 따른 동적인 UI/UX 구현이 가능합니다.

