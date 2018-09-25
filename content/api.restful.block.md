## 和区块数据相关的接口

### 查询区块信息

支持分页

```endpoint
GET http://localhost:17332/public/blocks
```

#### Example Request

```bash
  curl https://bch-insight.bitpay.com/api/blocks
```

#### Example Response

```json
{
    "blocks": [
      {
        "height": 544972,
        "size": 1126,
        "virtualSize": 1126,
        "hash": "000000000000000001aadeb33e33230bf35eaa6d4303c57074a8040077c7aef1",
        "time": 1535208512,
        "txlength": 5,
        "poolInfo": {}
      }, {
        "height": 544971,
        "size": 33307,
        "virtualSize": 33307,
        "hash": "000000000000000000b193ca28b0388c6900cde1ee3d77578136a4cbbe9a2d59",
        "time": 1535208493,
        "txlength": 72,
        "poolInfo": {
            "poolName": "AntMiner",
            "url": "https://bitmaintech.com/"
        }
      }
    ],
    "length": 2,
    "pagination": {
        "next": "2018-08-26",
        "prev": "2018-08-24",
        "currentTs": 1535241599,
        "current": "2018-08-25",
        "isToday": true,
        "more": false
    }
}
```

### 根据哈希查询区块

```endpoint
GET http://localhost:17332/public/block/:hash
```

#### Example Request

```bash
  curl https://bch-insight.bitpay.com/api/block/000000000000000001aadeb33e33230bf35eaa6d4303c57074a8040077c7aef1
```

#### Example Response

```json
{
    "hash": "000000000000000001aadeb33e33230bf35eaa6d4303c57074a8040077c7aef1",
    "size": 1126,
    "height": 544972,
    "version": 536870912,
    "merkleroot": "820df9ed8f57fe6464e5032fe0a9cbf4f986d793dcf78192b8a899993ba27d4b",
    "tx": ["38f6aa1c8112d681be031ea5113c1d4ffa9d245e0515cf27ed45210307cba86f", "2b45705210e20bbcb1f8c22ab26cddca086964f0122df42cd3dc48a2e1c563aa", "382cc1a07ccfc94676aa6373c4d19ac3a8485064b665335d270713393f0d6514", "60fe5f9173a1c78f2e0cbcff2b69baef5b90ee437c7363a367cbffb0e3a3c755", "ec1e19f1e121b1650d174e322bd3b674e0c943e5db6bc4a5422d6f177ea89bf3"],
    "time": 1535208512,
    "nonce": 4137301843,
    "bits": 402788059,
    "difficulty": 534246483976,
    "chainwork": "000000000000000000000000000000000000000000bc51a0a20e00709ff0f905",
    "confirmations": 1,
    "previousblockhash": "000000000000000000b193ca28b0388c6900cde1ee3d77578136a4cbbe9a2d59",
    "reward": 12.50007423,
    "isMainChain": true,
    "poolInfo": {}
}
```

### 获取块原始数据

```endpoint
GET http://localhost:17332/public/rawblock/:hash
```

#### Example Request

```bash
  curl https://bch-insight.bitpay.com/api/rawblock/000000000000000001aadeb33e33230bf35eaa6d4303c57074a8040077c7aef1
```

#### Example Response

```json
{
  "rawblock":"00000020592d9abecba4368157773deee1cd00698c38b028ca93b1000000000000000000820df9ed8f57fe6464e5032fe0a9cbf4f986d793dcf78192b8a899993ba27d4b406c815bdb0e021853379af60501000000010000000000000000000000000000000000000000000000000000000000000000ffffffff5c03cc5008192f5669614254432f4d696e6564206279206e6d73393133352f2cfabe6d6d184dc8e1ef0d19eddd4581a029620e0de25eaad2d6a1787c9df61d782045f37f0400000000000000109b63d30764e69a2d914f1943512b0100ffffffff017f99814a000000001976a914f1c075a01882ae0972f95d3a4177c86c852b7d9188ac000000000100000001e19cfde39d5ce89d39200dd0e7e7bbc9a2ea8bcf3a9c74b15edb40b45c921240000000006b483045022100f06cf926c0c630f678434cb6b8eb602064d0615f41bca5ad3c2b31d87692ab470220149e26ee6d4b0fb375dcb09ef81996365b853a8538be8cc0dc61b5db9f9e71be4121038dcabe66cc702624e6c7f2a437df7c36a68962a9becaa0f5f3e68a36839b5faaffffffff01c6dffe65010000001976a9146279b5d9e239500612d4f57d9cb1383bc6957a2288ac000000000200000001e7023fd9f341275c71181dc8797c987495d8fbe12db5619ac86d8c3e2fb1c197010000006b4830450221008a4a6b2d29bb5c5d96f55db2f513f8ef584aaa313c9112c745647fbd9d104cc00220646830de592a2ccea9abd9e30b4d9ded0cacbc66515792e56ca6291f02da84dd412102e730398dca951ded3e419829579c857f956d861ad5738d032ef17ccd2ca370aeffffffff02600e4e07000000001976a914cbe7d31810af5abb158d531fce0be1048021a30a88ace6b90100000000001976a9140a061221aa52f3942e8b39ad2b2c98abf058833488ac0000000002000000017755ce1733b8f89f14feceff96c9094ed571d78554478e733fa42abdfcffb5f3010000006b483045022100a9150be4afc7c0caffeed0b8f138701fc340be8ab0a0612862e600169b738acc0220792e8e9a274debb52c7a4ff76b84dbe1bc546efac36076dbac7d2211531f111b41210346e53d43ae00387c5198579129d4cf2e03ec6a66d7aee2f3efeba10c07cd64b3ffffffff02ff54bd03000000001976a914aa1604b040a7d3c86401fba95d1731b992d366e888ac19798c0d000000001976a9143bf58baf7fb8b69f7f4ffbb1a146c54ac78873e188ac00000000010000000145213921cec40e505c6f16e649b8205944e31dc85182a843909b234da605bc42010000006b483045022100bdf5c7dcf2baf938be5d336b222591f8e3435e9d67d8330544cc0cab40c631a002207979ad560335d35596e0d0141ff1e5ba7b363ce83a84328e6b549185b8506455412103cb8a7ef04cadfdc25425d84162f553bfee89b3109e939a3998c336b2f80642f0ffffffff02abdb00000000000017a9140c1ffe16047f2177e9e55b7b22e4ab699332b0d4870f763800000000001976a91429c69c5c468eab11fc22a558d80d7c555465595c88ac00000000"
}
```

### 根据高度查询区块

```endpoint
GET http://localhost:17332/public/block-index/:height
```

#### Example Request

```bash
  curl https://bch-insight.bitpay.com/api/block-index/544972
```

#### Example Response

```json
{
    "blockHash": "000000000000000001aadeb33e33230bf35eaa6d4303c57074a8040077c7aef1"
}
```