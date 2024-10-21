# 사전 요구사항

## 목차

1. [공통 사전 요구사항](prerequisites.md#공통-사전-요구사항)
2. [Windows 설치](prerequisites.md#windows-설치)
3. [macOS 설치](prerequisites.md#macos-설치)
4. [Linux 설치](prerequisites.md#linux-설치)
5. [Raspberry Pi5 OS 설치](prerequisites.md#raspberry-pi5-os-설치)

## 공통 사전 요구사항

### 1. Python

- **필요 버전**: 3.9 ~ 3.12 (`>=3.9,<3.13`)
- 설치되어 있지 않거나 업데이트가 필요한 경우, 공식 Python 웹사이트에서 다운로드하여 설치하세요.

[Python 공식 웹사이트](https://www.python.org/)

### 2. Node.js

- **필요 버전**: 18 이상
- 설치 확인: 터미널에서 `node --version`을 실행하세요 (18.x 이상이 출력되는지 확인)

## Windows 설치

1. [Node.js 공식 웹사이트](https://nodejs.org/)에서 최신 버전(v18 이상)을 다운로드하세요.
2. 설치 프로그램을 실행하고 지시에 따르세요.
3. 설치 확인: 명령 프롬프트에서 `node --version`을 실행하세요.

## macOS 설치

1. [Node.js 공식 웹사이트](https://nodejs.org/)에서 최신 버전(v18 이상)을 다운로드하세요.
2. 설치 프로그램을 실행하고 지시에 따르세요.
3. 설치 확인: 터미널에서 `node --version`을 실행하세요.

또는 Homebrew를 사용하여 설치:

```bash
brew install node
```

## Linux 설치

1. nvm(Node Version Manager)을 사용하여 Node.js 설치:

```bash
sudo apt update
sudo apt install curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source ~/.bashrc
nvm install --lts
```

2. 설치 확인: 터미널에서 `node --version`을 실행하세요 (18.x 이상이 출력되는지 확인)

## Raspberry Pi5 OS 설치

1. 일반 Linux 설치 과정을 따르세요:

```bash
sudo apt update
sudo apt install curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source ~/.bashrc
nvm install --lts
```

2. 설치 확인: 터미널에서 `node --version`을 실행하세요 (18.x 이상이 출력되는지 확인)
3. 추가로 필요한 라이브러리에 대한 심볼릭 링크를 생성하기 위해 다음 명령어를 실행하세요:

```bash
sudo ln -s /usr/lib/aarch64-linux-gnu/libwebp.so.7 /usr/lib/aarch64-linux-gnu/libwebp.so.6
sudo ln -s /usr/lib/aarch64-linux-gnu/libtiff.so.6 /usr/lib/aarch64-linux-gnu/libtiff.so.5
```

이 명령어들은 Raspberry Pi5 OS에서 Pyloid가 올바르게 작동하는 데 필요한 라이브러리 버전에 대한 심볼릭 링크를 생성합니다.
