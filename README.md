# Rust 项目构建工作流

 [`.github/workflows/rust.yml`](.github/workflows/rust.yml) 文件主要用于在 GitHub Actions 环境中构建 Rust 项目。该工作流支持多平台（Windows、Ubuntu、macOS）及多架构（amd64、arm64）的构建。
- 使用了 [dtolnay/rust-toolchain](https://github.com/dtolnay/rust-toolchain) 的脚本安装 stable 版本的 Rust 工具链，感谢脚本作者的辛勤维护~

## 配置变量

- 允许在rust.yml文件中配置program_name环境变量
- **program_name**: 当构建完成后，产物会压缩并上传到Github Actions目录，压缩包名为`program_name + 平台 + 架构`。

## 使用说明

1. 把.github/workflows/rust.yml复制到你的rust项目仓库根目录中
2. 在 GitHub 仓库页面的 Actions 选项卡中点击 **Run workflow** 开始构建。
3. 工作流会根据rust.yml文件中matrix选择的操作系统和架构矩阵，工作流会自动执行并构建对应平台的可执行文件。
4. 构建完成后，指定目录构建产物（target/）会被上传至对应的构建产物列表中，便于下载和后续使用。

## 注意
- 这个工作流只会把Cargo的编译产物（target/）上传到构建产物中，如果需要上传多个文件，请自行配置rust.yml中`path: output/*`

此工作流文件适用于需要跨平台构建 Rust 项目的场景，确保在不同系统环境下能够正确配置编译器及链接器，并生成对应平台的可执行文件。
