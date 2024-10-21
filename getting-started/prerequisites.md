# Prerequisites

## Table of Contents

1. [Common Prerequisites](prerequisites.md#common-prerequisites)
2. [Windows Installation](prerequisites.md#windows-installation)
3. [macOS Installation](prerequisites.md#macos-installation)
4. [Linux Installation](prerequisites.md#linux-installation)
5. [Raspberry Pi5 OS Installation](prerequisites.md#raspberry-pi5-os-installation)

## Common Prerequisites

### 1. Python

* **Required Version**: 3.9 \~ 3.12 (`>=3.9,<3.13`)
* If not installed or needs an update, download and install from the official Python website.

[Python Official Website](https://www.python.org/)

### 2. Node.js

* **Required Version**: 18 or higher
* Check installation: Run `node --version` in the terminal (ensure it outputs 18.x or higher)

## Windows Installation

1. Download the latest version (v18 or higher) from the [Node.js official website](https://nodejs.org/).
2. Run the installer and follow the instructions.
3. Verify installation: Run `node --version` in the command prompt.

## macOS Installation

1. Download the latest version (v18 or higher) from the [Node.js official website](https://nodejs.org/).
2. Run the installer and follow the instructions.
3. Verify installation: Run `node --version` in the terminal.

Alternatively, install using Homebrew:

```bash
brew install node
```

## Linux Installation

1. Install Node.js using nvm (Node Version Manager):

```bash
sudo apt update
sudo apt install curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source ~/.bashrc
nvm install --lts
```

2. Verify installation: Run `node --version` in the terminal (ensure it outputs 18.x or higher)

## Raspberry Pi5 OS Installation

1. Follow the general Linux installation process:

```bash
sudo apt update
sudo apt install curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source ~/.bashrc
nvm install --lts
```

2. Verify installation: Run `node --version` in the terminal (ensure it outputs 18.x or higher)
3. Additionally, run the following commands to create symbolic links for the required libraries:

```bash
sudo ln -s /usr/lib/aarch64-linux-gnu/libwebp.so.7 /usr/lib/aarch64-linux-gnu/libwebp.so.6
sudo ln -s /usr/lib/aarch64-linux-gnu/libtiff.so.6 /usr/lib/aarch64-linux-gnu/libtiff.so.5
```

These commands create symbolic links for the library versions required for Pyloid to function correctly on Raspberry Pi5 OS.
