# Cosmwasm Maths Operations

This is a  example of a CosmWasm contract that implements simple maths operations like addition, substraction, multiplication, division, modulo and exponential

---

## 合约部署及交互演示
### 账户管理
```
# 创建
xiond keys add your_account

# 查询余额
xiond query bank balances your_account --node https://rpc.xion-testnet-1.burnt.com:443
```

### 合约编译
```
cargo wasm 

# 优化合约大小
RUSTFLAGS='-C link-arg=-s' cargo wasm
```

### 部署上链
```
# 设置环境变量
RPC="https://rpc.xion-testnet-1.burnt.com:443"
export NODE=(--node $RPC)
export TXFLAG=($NODE --chain-id xion-testnet-1 --gas-prices 0.25uxion --gas auto --gas-adjustment 1.4)

# 上传
xiond tx wasm store target/wasm32-unknown-unknown/release/cosmwasm_math.wasm --from demo $TXFLAG -y --output json

# 查询 code_id
RESP=$(xiond q tx C11556D6A214DCB3655102A4D9631F0AA65EAEDABBA2BCBD676E57273A2DB62D -o json $NODE)

CODE_ID=$(echo "$RESP" | jq -r '.events[]| select(.type=="store_code").attributes[]| select(.key=="code_id").value')

echo $CODE_ID

```

### 实例化合约
```
# 参数
INIT='{}'

# 实例化
xiond tx wasm instantiate $CODE_ID "$INIT" --from demo --label "initialize cosmwasm math contract" $TXFLAG -y --no-admin

# 查询合约地址
xiond query wasm list-contract-by-code $CODE_ID $NODE --output json

```

### 合约读写
```
# 参数
EXECMSG='{"operations":{"a":"5","b":"2"}}'
CONTRACT='xion1vvddpg4drp34k388xej297duptgwasac832xmpan2je799nwp3uqnzf29j'

# 计算
xiond tx wasm execute $CONTRACT "$EXECMSG" --amount 100uxion --from demo $TXFLAG -y

# 参数
QUERYMSG='{"get_response":{}}'

# 查询
xiond query wasm contract-state smart $CONTRACT "$QUERYMSG" $NODE --output json
```

---

