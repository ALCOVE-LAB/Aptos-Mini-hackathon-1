# 14-NostrOnAptos

## 项目名称

Nostr on Aptos.

## 项目描述

Nostr on Aptos 项目实现 Nostr 协议在 Aptos 区块链上的功能（建档，发文，分享）。

Nostr on Aptos 项目旨在实现 Aptos 区块链上缺失的 Web3 点对点社交模块，并通过实现 Nostr 协议，打通 Nostr 协议和 Aptos 区块链协议之间的桥梁，使得基于 Nostr 协议实现的比特币和 DeFi 应用也同时能在 Aptos 上运行。

## Aptos 区块链集成

Nostr on Aptos 经由 aptos-framework 实现 Nostr 协议的基本功能和特性。

### 技术栈

- aptos-framework
- Move

### 安装与运行指南

安装 Aptos CLI。

克隆仓库。

进入 `nostraptos/move/nips/nip_01`。

#### 编译

```zsh
aptos move compile --named-addresses nip_01_addr=default
```

#### 测试

```zsh
aptos move test
```

#### 部署

```zsh
aptos move deploy-object --address-name nip_01_addr
```

#### 运行示例

```zsh
aptos move run --function-id <object_address>::event::save_event_entry --args string:"cddcc4a1d4a94d627e7808f904d0477cf16ae9d4fafa1eb883ab7a498bdda777" u64:1744959972 u16:0 string:"[[]]" string:'{\"name\":\"ZHANG, HENGMING\",\"about\":\"\",\"picture\":\"\",\"website\":\"\"}' string:"6c2565ceabff153609aa9ccdeb13421a1181a54d0ca4fe10cd074b0c2da44c641c98992701c9a4d3e24391db3e358eff190510be46e73d0e517d5e5b13bb06fd"
```

替换 `<object_address>` 为部署的合约地址。

### 项目亮点/创新点

实现 Nostr 协议。

Nostr 是 Web2 的协议。

这让 Web2 的应用也能在 Web3 上的 Aptos 区块链上运行。

### 未来发展计划

在 Aptos，Sui，Rooch 上实现 Nostr 协议。

### 团队成员

ZHANG, HENGMING

### 演示链接

https://explorer.aptoslabs.com/object/0xe222a55e1163fe916a097bf0ca469943701351f793f249470d683d59f8c9818c/modules/run/nip_01?network=testnet
