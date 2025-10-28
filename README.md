## 概要

- `eth0` のゲートウェイ設定を変更
- `eth1` の設定ファイル (`99-eth1.yaml`) をテンプレート から生成
- ホスト名に応じて、`eth1` に静的なIPアドレスを割り当てる

## 前提条件

- `netplan` がインストールされている
- `make` コマンドが利用可能
- `sudo` 権限（`netplan` の設定変更のため）
- 各サーバーのホスト名が以下のように設定されている

## 設定されるIPアドレス

`Makefile` に基づき、ホスト名に応じて以下のIPアドレスが `eth1` に設定される。

| ホスト名 | 割り当てられるIPアドレス |
| :--- | :--- |
| `microservices-demo-01` | `192.168.10.101` |
| `microservices-demo-02` | `192.168.10.102` |
| `microservices-demo-03` | `192.168.10.103` |

## 使用方法

1. このリポジトリをクローン

```bash
git clone https://github.com/kikulabo/sakura-cloud-netplan-init.git
cd sakura-cloud-netplan-init
```

2. `netplan` の設定ファイルを生成

```bash
make network-config
```

3. 設定を適用

```bash
make network-apply
```
