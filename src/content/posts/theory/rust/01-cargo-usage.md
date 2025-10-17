## 1. 认识 `Cargo` ✨

- 你可以使用rust的编译器`rustc`直接编译源代码

```sh
rustc main.rs
./main
```

> 对于简单项目rustc进行编译就可以了，但是复杂的项目就比较麻烦了。所幸我们有`cargo`，它是 Rust 的构建系统和包管理器提供了一系列工具。

## 2. 上手使用 `Cargo` 🌈

```sh
cargo new projerct_name     # 创建rust项目
cd project_name
cargo build                 # 安装依赖构建项目生成Cargo.lock文件
cargo run                   # 构建并运行
cargo check                 # 检查项目是否能够构建
cargo build --release       # 构建release版项目会进行优化
cargo run --release         # 构建并运行
cargo clean                 # 清除构建缓存
```

### 3. 添加依赖 😺

当你是使用cargo new创建文件夹后项目根目录会生成cargo.toml文件,
它是项目配置文件描述项目和声明所需依赖以及定义开关

```sh
$ tree
.
├── .git
├── .gitignore
├── Cargo.toml
└── src
    └── main.rs
```

cargo.toml 是 cargo 特有的项目数据描述文件。它存储了项目的所有元配置信息
Cargo.lock 文件是 cargo 工具根据同一项目的 toml 文件生成的项目依赖详细清单

添加依赖只需在`Cargo.toml`文件中[dependencies] 部分添加目标包名和版本号，然后执行`cargo build`依赖会自动安装
```toml
[dependencies]
time = "0.1.12"
```
::: note
Cargo 依赖版本号前面加`=`精确版本，默认为`^`当前主版本最新次版本和补丁
`cargo build`会使用 Cargo.lock 锁定的版本不会升级版本
:::

```sh
cargo update   # 更新依赖库到最新版本
```
### 4. 测试 🥰

Cargo 可以通过 cargo test 命令运行项目中的测试文件：它会在 src/ 底下的文件寻找单元测试，也会在 tests/ 目录下寻找集成测试。而且它还会编译 examples/ 下的示例文件以及文档中的示例。

```sh
cargo test
```

### 5. 清理`crate`缓存 🌸

```sh
cargo install cargo-cache
cargo cache --autoclean
```
> cargo-cache 自动清理旧的不再使用的crate
