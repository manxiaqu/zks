# 屏蔽交易

证明内容：

- input 金额总和等于 output 金额总和
- 交易发送方知道 input note 的私钥
- input notes 与交易签名相关，该笔交易中的数据无法被篡改

```bash
commitment = Hash(recipient address, amount, rho, r)

# recipient address: 接收方地址
# amount: 发送的金额
# rho: 唯一标识，用于派生nullifier
# nonce: 随机数
```

```bash
Nullifier = Hash(spending key, rho)
# spending key: 密钥
# rho: commitment唯一标识
```

屏蔽交易验证内容：

- 对于 input note，存在对于的 commitment
- note commitment 与 nullifier 正确计算
- output note 的 nullifier 与其他任意的 nullifier 无法碰撞
