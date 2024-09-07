#  co_learning_09_07

## 配置aptos的环境

### 一、快速配置Rust开发环境（Windows）

#### 1. 安装Rust

首先，你需要安装Rust工具链，这是开发Rust程序的基础。

- **访问Rust官网**：前往 [Rust官网](https://www.rust-lang.org/)。
- **点击“Get Started”**：点击页面中的“Get Started”按钮，这会引导你下载`rustup-init.exe`。
- **运行安装程序**：下载后运行安装程序，并按照提示进行默认安装。`rustup`会自动安装Rust编译器和包管理工具`cargo`。

#### 2. 安装Visual Studio Community（包含必要的组件）

Rust需要一些特定的C++工具和库，这些可以通过Visual Studio Community的安装程序获取。

1. **下载Visual Studio Installer**：前往 [Visual Studio官网](https://visualstudio.microsoft.com/)，下载并安装Visual Studio Community版本。
2. **选择C++桌面开发工作负载**：
   - 在Visual Studio Installer中，选择“**Desktop development with C++（使用C++的桌面开发）**”工作负载。这会安装所有Rust编译所需的工具，包括C++编译器、链接器、Windows SDK等。
3. **确认和安装**：
   - 确保勾选了“MSVC v143 - VS 2022 C++ x64/x86 build tools”和“Windows 10 SDK”组件，然后点击“安装”按钮。这些是Rust在Windows上使用MSVC（微软C++编译器）所需的关键工具。
4. **等待安装完成**：安装完成后，所有需要的工具就都配置好了。

#### 3. 验证Rust环境

安装完成后，验证Rust是否能够正常使用。

- **打开命令提示符**：按下`Win + R`，输入`cmd`并回车。

- **输入命令**：

  ```bash
  rustc --version
  cargo --version
  ```

  如果Rust和Cargo都返回版本信息，说明Rust工具链已经安装成功。

- **编译示例项目**：

  ```bash
  cargo new hello_rust
  cd hello_rust
  cargo run
  ```

  这会创建一个简单的Rust项目并运行，如果输出“Hello, world!”，则说明配置成功。

 Aptos CLI 环境配置教程（Windows）

Aptos CLI 是一个用于与 Aptos 区块链交互的命令行工具，主要用于部署和管理区块链资源。以下是如何在 Windows 系统上配置 Aptos CLI 的详细步骤。我们推荐使用 Python 脚本安装，因其更便于更新和管理。如果遇到问题，也可以选择手动安装预编译的二进制文件。

### 二、通过 Python 脚本安装 Aptos CLI

#### 确认安装 Python 3.6+

1. **检查 Python 是否已安装**：

   - 打开 PowerShell 或命令提示符，输入以下命令检查 Python 版本：

     ```
     python3 --version
     ```

   - 如果没有输出 Python 版本信息，则需要安装 Python。前往 [Python官网](https://www.python.org/) 下载并安装最新版本的 Python 3。

2. **确保 Python 和 pip 已正确安装并在 PATH 中**：

   - 安装过程中，请勾选“Add Python to PATH”选项，确保命令行能识别 `python3` 和 `pip3`。

#### 运行 Aptos CLI 安装脚本

1. **在 PowerShell 中执行以下命令**：

   - 这条命令将从 Aptos 官方下载并运行 CLI 安装脚本：

     ```powershell
     iwr "https://aptos.dev/scripts/install_cli.py" -useb | Select-Object -ExpandProperty Content | python3
     ```

   - 如果出现 

     ```
     ModuleNotFoundError: No module named packaging
     ```

      错误，输入以下命令安装缺失的 Python 包：

     ```bash
     pip3 install packaging
     ```

   - 然后重新运行上述安装命令。

2. **更新 PATH 环境变量**：

   - 安装完成后，终端会提示一条更新 PATH 的命令，类似于：

     ```bash
     setx PATH "%PATH%;C:\Users\<your_account_name>\.aptoscli\bin"
     ```

   - 复制并在终端中运行这条命令，以便系统识别 Aptos CLI。

#### 步骤 3：验证安装

1. **打开新的 PowerShell 或命令提示符**。

2. **输入以下命令查看帮助信息**：

   ```bash
   aptos help
   ```

   - 如果成功显示命令列表，说明 Aptos CLI 安装成功。

3. **更新 Aptos CLI**：

   - 当需要更新 Aptos CLI 时，可以运行：

     ```bash
     aptos update
     ```

### 方法二：通过预编译二进制文件安装 Aptos CLI（备选方法）

#### 步骤 1：下载预编译二进制文件

1. 访问 Aptos CLI 发布页面：
   - 前往 [Aptos CLI Release 页面](https://github.com/aptos-labs/aptos-core/releases)。
2. **展开“Assets”查看预编译的二进制文件**。
3. 下载适用于 Windows 的 zip 文件：
   - 文件名称类似于：`aptos-cli-<version>-Windows-x86_64.zip`。
4. **解压下载的文件**。

#### 步骤 2：配置 CLI

1. **将解压后的文件移动到你想调用 Aptos 的文件夹**。
2. **复制可执行文件的路径**：
   - 例如：`C:\Users\<username>\Downloads\aptos-cli-3.1.0-Windows-x86_64\aptos.exe`。
3. **将路径添加到系统 PATH 环境变量中**：
   - 打开“系统属性” > “高级系统设置” > “环境变量”。
   - 找到 `Path`，点击“编辑”，添加你复制的 Aptos CLI 可执行文件路径。

#### 步骤 3：验证安装

1. **打开 PowerShell**。

2. **运行以下命令验证安装**：

   ```bash
   C:\Users\<username>\Downloads\aptos-cli-3.1.0-Windows-x86_64\aptos.exe help
   ```

   - 显示帮助信息即表示安装成功。

3. **更新 CLI**：

   - 如果需要更新 CLI，删除现有安装的文件，并重复上述步骤。

![1725719262633](C:\Users\23576\AppData\Roaming\Typora\typora-user-images\1725719262633.png)