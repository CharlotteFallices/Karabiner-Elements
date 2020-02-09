[![Build Status](https://github.com/pqrs-org/Karabiner-Elements/workflows/Karabiner-Elements%20CI/badge.svg)](https://github.com/pqrs-org/Karabiner-Elements/actions)
[![License](https://img.shields.io/badge/license-Public%20Domain-blue.svg)](https://github.com/pqrs-org/Karabiner-Elements/blob/master/LICENSE.md)

# Karabiner-Elements

Karabiner-Elements可在macOS Sierra或更高版本上自定义键盘.

## Download

您可以从[这里](https://pqrs.org/osx/karabiner/)下载Karabiner-Elements.

### Old releases

您可以从[这里](https://pqrs.org/osx/karabiner/history.html)下载Karabiner-Elements的早期版本.

## Supported systems

-   macOS Sierra (10.12)
-   macOS High Sierra (10.13)
-   macOS Mojave (10.14)
-   macOS Catalina (10.15)

## Usage

<https://pqrs.org/osx/karabiner/document.html>

## Donations

如果您想为Karabiner Elements做出`经济贡献`,您可以通过<https://pqrs.org/osx/karabiner/pricing.html>进行捐赠.

---

## For developers

### How to build

编译Karabiner-Elements的系统要求:

-   macOS 10.14+
-   Xcode 10+
-   Command Line Tools for Xcode
-   CMake (`brew install cmake`)

#### Step 1: Getting source code

请从[Gitub](https://github.com/CharlotteFallices/Karabiner-Elements)克隆仓库:

```shell
git clone --depth 1 https://github.com/pqrs-org/Karabiner-Elements.git
```

#### Step 2: Building a package

```shell
cd Karabiner-Elements
make package
```

The  script will create a redistributable **Karabiner-Elements-VERSION.dmg** in the current directory.
`make`脚本将在当前目录中创建可重新构建(redistributable)的**Karabiner-Elements-VERSION.dmg** .

#### Note: About pre-built binaries in the source tree

Karabiner-Elements在源代码树中使用一些预编译的二进制文件。

-`src / vendor / Karabiner-VirtualHIDDevice / dist / *。kext`
-`src / vendor / Sparkle / Sparkle.framework`

上面的`make package`命令不会重建这些二进制文件<br/>
(这些二进制文件将复制到分布式程序包(distributed package)中)

如果要重建这些二进制文件,则必须手动进行编译.<br/>
请遵循这些(?)项目的要求(instruction).
##### About rebuilding kext in Karabiner-VirtualHIDDevice

如果要在`Karabiner-VirtualHIDDevice`中编译kext,则可能需要一个有效的证书,该证书可以对已编译的kext进行签名.<br/>
除非有此类证书,否则系统将拒绝加载内置的kext.<br/>
有关更多详细信息，请阅读[System Integrity Protection Guide](https://developer.apple.com/library/archive/documentation/Security/Conceptual/System_Integrity_Protection_Guide/KernelExtensions/KernelExtensions.html).

（我们添加了预编译的kext二进制文件,以避免证书的限制)
