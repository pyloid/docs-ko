# 커스텀 보일러플레이트 만들기

기존에 제공된 보일러플레이트 말고, 원하는 프론트엔드 프레임워크를 사용하여 보일러플레이트를 만들 수 있습니다.

## 방법

원하는 프론트엔드 프레임워크를 선택합니다. ex) React, Vue, Svelte, Angular 등...

## 예시 (React)

### 1. 리액트 프로젝트 생성

```bash
npm create vite@latest
# 리액트 선택
```

### 2. index.html 파일 수정

#### index.html 에 Security Policy 추가 (선택사항)

{% code title="index.html" %}

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <script src="qrc:///qtwebchannel/qwebchannel.js"></script>
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Pyloid</title>
    <!-- Add security policy  (선택사항) -->
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self'; script-src 'self' qrc://*; img-src 'self' data:; style-src 'self' 'unsafe-inline';"
    />
    <!------------------------------------>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

{% endcode %}

### 3. main.jsx/tsx 파일 수정

pylonReady 가 발생한 다음에 렌더링을 진행하여, Pyloid 의 함수가 로드된 이후 렌더링을 진행되도록 합니다.

```tsx
document.addEventListener('pyloidReady', () => {
  // DOM 렌더링 코드
});
```

이를 통해 렌더링 Pyloid 의 함수가 로드된 이후 렌더링을 진행되도록 합니다.

{% code title="main.tsx" %}

```tsx
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import App from './App.tsx';
import './index.css';

document.addEventListener('pyloidReady', () => {
  createRoot(document.getElementById('root')!).render(
    <StrictMode>
      <App />
    </StrictMode>
  );
});
```

{% endcode %}

### 4. vite.config.ts 파일 수정

빌드되어 html 파일이 생성되는 경로를 build 폴더로 지정합니다.

{% code title="vite.config.ts" %}

```ts
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  base: './',
  build: {
    outDir: 'build',
  },
});
```

{% endcode %}

### 5. package.json 수정

각 os별 개발 및 빌드 작업을 위해 스크립트를 추가합니다.
그리고 devDependencies 에 concurrently 와 run-script-os 를 추가합니다.

{% hint style="info" %}
만약에 pnpm 이나 yarn, bun 등의 패키지 매니저를 사용하고 있다면, 각 패키지 매니저에 맞는 스크립트로 변경해야합니다.
{% endhint %}

{% hint style="warning" %}
windows: python / linux: python3 / macos: python3 을 기본 파이썬 커맨드 명령어로 지정합니다. 그래서 만약 자신의 컴퓨터가 py/python/python3 등을 사용하여 기본 명령어가 다르다면 수정해야합니다.
{% endhint %}

{% code title="package.json" %}

```json
{
  // ...

  "scripts": {
    "dev": "run-script-os",
    "dev:windows": "concurrently --raw --names \"front,pyloid\" \"npm run vite\" \".\\venv-pyloid\\Scripts\\python .\\src-pyloid\\main.py\"",
    "dev:linux": "concurrently --raw --names \"front,pyloid\" \"npm run vite\" \"./venv-pyloid/bin/python ./src-pyloid/main.py\"",
    "dev:macos": "concurrently --raw --names \"front,pyloid\" \"npm run vite\" \"./venv-pyloid/bin/python ./src-pyloid/main.py\"",
    "vite": "vite",
    "build": "tsc -b && vite build && run-script-os",
    "build:windows": ".\\venv-pyloid\\Scripts\\pyinstaller build-windows.spec",
    "build:linux": "./venv-pyloid/bin/pyinstaller build-linux.spec",
    "build:macos": "./venv-pyloid/bin/pyinstaller build-macos.spec",
    "init": "npm install && run-script-os",
    "init:windows": "python -m venv venv-pyloid && .\\venv-pyloid\\Scripts\\pip install -r requirements.txt",
    "init:linux": "python3 -m venv venv-pyloid && ./venv-pyloid/bin/pip install -r requirements.txt",
    "init:macos": "python3 -m venv venv-pyloid && ./venv-pyloid/bin/pip install -r requirements.txt"
  },

  // ...

  "devDependencies": {
    "concurrently": "^9.0.1",
    "run-script-os": "^1.1.6"
  }
}
```

{% endcode %}

### 6. 최상위 디렉토리에 requirements.txt 추가

pyloid 패키지와 pyinstaller 패키지를 추가합니다.

{% code title="requirements.txt" %}

```
pyloid
pyinstaller
```

{% endcode %}

### 7. pyinstaller 스펙 파일 추가

프로젝트를 exe 파일로 빌드하기 위해 pyinstaller 스펙 파일을 루트 경로에 추가합니다.

![file tree](/.gitbook/assets/boilerplate1.png)

여기서 사용된 파일 경로 이미지입니다.
루트 경로에 src-pyloid 폴더가 있고, 그 안에 main.py 파일이 있습니다.

{% hint style="warning" %}
자신의 프로젝트 파일 경로가 다르다면 그에 맞게 spec 파일을 수정해야합니다.
(아이콘 경로, 빌드 html 경로, 파이썬 파일 경로)
{% endhint %}

{% tabs %}
{% tab title="build-windows.spec" %}

```python
# -*- mode: python ; coding: utf-8 -*-
block_cipher = None

a = Analysis(['src-pyloid/main.py'],
            pathex=[],
            binaries=[],
            datas=[('src-pyloid/icons/', 'icons/'),
            ('build/', 'build/'),
            ],
            hiddenimports=[],
            hookspath=[],
            hooksconfig={},
            runtime_hooks=[],
            excludes=['PySide6.QtQml', 'PySide6.QtTest', 'PySide6.Qt3D', 'PySide6.QtSensors', 'PySide6.QtCharts', 'PySide6.QtGraphs', 'PySide6.QtDataVisualization', 'PySide6.QtQuick', 'PySide6.QtDesigner', 'PySide6.QtUiTools', 'PySide6.QtHelp'],
            win_no_prefer_redirects=False,
            win_private_assemblies=False,
            cipher=block_cipher,
            noarchive=False)

pyz = PYZ(a.pure, a.zipped_data,
          cipher=block_cipher)

exe = EXE(
    pyz,
    a.scripts,
    [],
    exclude_binaries=True,
    name='pyloid-app',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    console=False,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
    icon=['src-pyloid/icons/icon.ico'],
)

coll = COLLECT(
    exe,
    a.binaries,
    a.zipfiles,
    a.datas,
    strip=False,
    upx=True,
    upx_exclude=[],
    name='pyloid-app'
)

```

{% endtab %}

{% tab title="build-linux.spec" %}

```python
# -*- mode: python ; coding: utf-8 -*-

block_cipher = None

a = Analysis(['src-pylon/main.py'],
            pathex=[],
            binaries=[],
            datas=[('src-pyloid/icons/', 'icons/'),
            ('build/', 'build/'),
            ],
            hiddenimports=[],
            excludes=['PySide6.QtQml', 'PySide6.QtTest', 'PySide6.Qt3D', 'PySide6.QtSensors', 'PySide6.QtCharts', 'PySide6.QtGraphs', 'PySide6.QtDataVisualization', 'PySide6.QtQuick', 'PySide6.QtDesigner', 'PySide6.QtUiTools', 'PySide6.QtHelp'],
            hookspath=[],
            hooksconfig={},
            runtime_hooks=[],
            win_no_prefer_redirects=False,
            win_private_assemblies=False,
            cipher=block_cipher,
            noarchive=False)

pyz = PYZ(a.pure, a.zipped_data,
          cipher=block_cipher)

exe = EXE(
    pyz,
    a.scripts,
    [],
    exclude_binaries=True,
    name='pyloid-app',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    console=False,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
    icon=['src-pyloid/icons/icon.png'],
)

coll = COLLECT(
    exe,
    a.binaries,
    a.zipfiles,
    a.datas,
    strip=False,
    upx=True,
    upx_exclude=[],
    name='pyloid-app'
)

```

{% endtab %}
{% tab title="build-macos.spec" %}

```python
# -*- mode: python ; coding: utf-8 -*-


a = Analysis(
    ['src-pyloid/main.py'],
    pathex=[],
    binaries=[],
    datas=[('src-pyloid/icons/', 'icons/'),
             ('build/', 'build/'),
             ],
    hiddenimports=['PySide6.QtWebEngineCore'],
    hookspath=[],
    hooksconfig={},
    runtime_hooks=[],
    excludes=['PySide6.QtQml', 'PySide6.QtTest', 'PySide6.Qt3D', 'PySide6.QtSensors', 'PySide6.QtCharts', 'PySide6.QtGraphs', 'PySide6.QtDataVisualization', 'PySide6.QtQuick', 'PySide6.QtDesigner', 'PySide6.QtUiTools', 'PySide6.QtHelp'],
    noarchive=False,
    optimize=0,
)
pyz = PYZ(a.pure)

exe = EXE(
    pyz,
    a.scripts,
    [],
    exclude_binaries=True,
    name='pyloid-app',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    console=False,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
)
coll = COLLECT(
    exe,
    a.binaries,
    a.datas,
    strip=False,
    upx=True,
    upx_exclude=[],
    name='pyloid-app',
)
app = BUNDLE(
    coll,
    name='pyloid-app.app',
    icon='src-pyloid/icons/icon.icns',
    bundle_identifier=None,
)
```

{% endtab %}
{% endtabs %}

### 8. 아이콘 추가 (Optional)

필요한 경우 아이콘 파일을 추가합니다.

![icon path](/.gitbook/assets/boilerplate1.png)

그리고 그 경로에 맞게 spec 파일을 수정해야합니다.

### 9. 실행

```bash
npm run dev
```

프로젝트를 실행하여 테스트합니다.

### 10. 빌드

```bash
npm run build
```

프로젝트를 빌드하여 테스트합니다.
