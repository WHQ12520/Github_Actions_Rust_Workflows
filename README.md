# Rust 项目构建工作流

 [`.github/workflows/rust.yml`](.github/workflows/rust.yml) 文件主要用于在 GitHub Actions 环境中构建 Rust 项目。该工作流支持多平台（Windows、Ubuntu、macOS）及多架构（amd64、arm64）的构建。
- 使用了 [dtolnay/rust-toolchain](https://github.com/dtolnay/rust-toolchain) 的脚本安装 stable 版本的 Rust 工具链，感谢脚本作者的辛勤维护~

## 必要配置变量

- 使用前请在rust.yml文件中配置program_name环境变量
- **program_name**: 项目的可执行文件名称。当构建完成后，产物文件会按照格式 `<program_name>_<os>_<arch>` 复制文件到输出目录。

## 使用说明

1. 把.github/workflows/rust.yml复制到你的rust项目仓库根目录中
2. 配置rust.yml文件中的program_name的值为rust项目Cargo.toml中package的name值（你的程序名字）
3. 在 GitHub 仓库页面的 Actions 选项卡中点击 **Run workflow** 开始构建。
4. 根据rust.yml文件中matrix选择的操作系统和架构矩阵，工作流会自动执行并构建对应平台的可执行文件。
5. 构建完成后，指定构建产物会被上传至对应的构建产物列表中，便于下载和后续使用。

## 注意
- 这个工作流只会把构建产物的可执行文件（target/x86_64-unknown-linux-gnu/release/program_name）上传到构建产物中，如果需要上传多个文件，请自行配置rust.yml中“Build for rust”的cp复制指令

此工作流文件适用于需要跨平台构建 Rust 项目的场景，确保在不同系统环境下能够正确配置编译器及链接器，并生成对应平台的可执行文件。