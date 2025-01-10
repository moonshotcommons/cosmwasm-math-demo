# 环境搭建

This is a  example of a CosmWasm contract that implements simple maths operations like addition, substraction, multiplication, division, modulo and exponential

---

## 安装依赖
### [Rust 安装](https://www.rust-lang.org/tools/install)
```
# macOS, Linux, or another Unix-like OS
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# 验证
rustc --version

# 添加对 WASM 的支持
rustup target add wasm32-unknown-unknown

# 或者使用国内镜像来安装
https://rsproxy.cn/#getStarted
```

### [Go 安装](https://go.dev/doc/install)
```

# 选择适合您操作系统的安装包

# 配置环境变量
vim ~/.bash_profile  or   vim ~/.zshrc

# 输入环境变量
export GOPATH=$(go env GOPATH)
export PATH=$GOPATH/bin:$PATH

# 生效环境变量
source ~/.bash_profile

# 验证
echo $GOPATH

# 或者使用国内镜像
https://learnku.com/go/wikis/38122
```

## 安装客户端命令工具（Xion Daemon）
```
# 获取 XION 仓库最新版本代码
git clone https://github.com/burnt-labs/xion.git

# 在刚刚下载的 XION 项目目录下构建 xiond
make install

# 验证
xiond --help
```


### [测试币领取](https://discord.gg/burnt)
```
/faucet your_address
```

### 添加钱包

### 区块链浏览器
https://explorer.burnt.com/xion-testnet-1

https://testnet.xion.explorers.guru/
---

