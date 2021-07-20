# Wallet API

**New Address**

Creates a new wallet address.

```bash
GET /api/v1/wallet/getnewaddress
```

Example: `curl -X GET "localhost:3000/api/v1/wallet/getnewaddress"`

**Fullnode required**: NO

**Parameters**: NONE

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
sV5QNeZvcGmDke91ncnbuoMLBJcpTZQCzs
```

</p>
</details>  

---

**List addresses**

Gets a list of all addresses available in the wallet.

```bash
GET /api/v1/wallet/listaddresses
```

Example: `curl -X GET "localhost:3000/api/v1/wallet/listaddresses"`

**Fullnode required**: NO

**Parameters**: NONE

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
[
    {
        "address": "sgu2PRDZv9yeqco6ouVG5WvPegZ7iVHFod",
        "unlocked": true
    },
    {
        "address": "shMrmPKbCy2ZksH8B9odbnRWxQhdsSusDp",
        "unlocked": true
    }
]
```

</p>
</details>  

---

**Get balances by account**

Get the balances of all owned tokens for the given account address, including SCC.

```bash
GET /api/v1/wallet/getbalances/:account
```

Example: `curl -X GET "localhost:3000/api/v1/wallet/getbalances/sgu2PRDZv9yeqco6ouVG5WvPegZ7iVHFod"`

**Fullnode required**: NO

**Parameters**:

| Name | Mandatory | Description |
|---------|---------|---------|
| account | YES | The account address |

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
[
    {
        "name": "StakeCubeCoin",
        "ticker": "SCC",
        "balance": 99999192,
        "utxos": [
            {
                "address": "sgu2PRDZv9yeqco6ouVG5WvPegZ7iVHFod",
                "id": "5dbf84c3f2b6feac276928453e9080eb15f957bbf84779ebe842b3db678e470d",
                "vout": 1,
                "script": "76a914f870774783ff34265f03a859985ad44fa5ec4a4788ac",
                "sats": 99999192,
                "spent": false,
                "mempool": false
            }
        ]
    },
    {
        "name": "SCP-Faucet",
        "contract": "69a3bd3c864b69390e02cc43a0f9725d2736f8129cea527e333af472bc92a05b",
        "ticker": "TEST",
        "version": 2,
        "balance": 100000000,
        "unclaimed_balance": 0
    }
]
```

</p>
</details>

---

**Send**

Creates a transfer transaction to an destination address, using the given account's address.

The transaction fee/gas is paid from the given accounts SCC balance.

```bash
GET /api/v1/wallet/send/:address/:currency/:to/:amount
```

Example: `curl -X GET "localhost:3000/api/v1/wallet/send/sgu2PRDZv9yeqco6ouVG5WvPegZ7iVHFod/69a3bd3c864b69390e02cc43a0f9725d2736f8129cea527e333af472bc92a05b/shMrmPKbCy2ZksH8B9odbnRWxQhdsSusDp/1"`

**Fullnode required**: NO

**Parameters**:

| Name | Mandatory | Description |
|---------|---------|---------|
| address | YES | The 'from' address |
| currency | YES | `scc` or the tokens unique contract id |
| to | YES | The receiver / the destination address |
| amount | YES | The amount to be transfered |

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
{
    "txid":"5dbf84c3f2b6feac276928453e9080eb15f957bbf84779ebe842b3db678e470d",
    "rawTx":"0200000001A1E32542A010A59D128FE4736961FC091A8009FA2D92E4E0DDB326C7CD572139000000006B483045022100EF78DFF7E5782B12B6E4D67427668253B551E1B6CAE4DFBAC0A080CC5B66AB1302206FB2C9893A2DAB18EC8F877668AA802A94DCD887E5518F308A19F0A0C3E1A9530121037006754D12568A9F4C3C102E87FE1032C12BE13935E9BA18BB9F469B6470DDECFFFFFFFF020100000000000000756A4C72363961336264336338363462363933393065303263633433613066393732356432373336663831323963656135323765333333616634373262633932613035622073656E64203130303030303030302073684D726D504B624379325A6B73483842396F64626E525778516864735375734470D8DDF505000000001976A914F870774783FF34265F03A859985AD44FA5EC4A4788AC00000000"
}
```

</p>
</details>

---

**Stake (SCP-2)**

Creates a stake transaction to claim the pending rewards of a given account and token.

```bash
GET /api/v1/wallet/stake/:address/:contract
```

Example: `curl -X GET "localhost:3000/api/v1/wallet/stake/sgu2PRDZv9yeqco6ouVG5WvPegZ7iVHFod/69a3bd3c864b69390e02cc43a0f9725d2736f8129cea527e333af472bc92a05b"`

**Fullnode required**: NO

**Parameters**:

| Name | Mandatory | Description |
|---------|---------|---------|
| address | YES | The account address |
| contract | YES |The tokens unique contract id |

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
{
    "txid": "1a39509458c52bf19f56bd59298e083ccd5c51219169c9b19fdf99ef9508e2f7",
    "rawTx": "02000000010D478E67DBB342E8EB7947F8BB57F915EB80903E45286927ACFEB6F2C384BF5D010000006B483045022100E8E674D7117C1F898858BD7BB1F42CDEDD2569DDED66FD5C1727ED1D48B380DB0220302C6F285ED66E733904E178F9B186BE0E7A87EE8BACA2D0796ADD0A15DDF2940121037006754D12568A9F4C3C102E87FE1032C12BE13935E9BA18BB9F469B6470DDECFFFFFFFF0201000000000000004A6A4C47363961336264336338363462363933393065303263633433613066393732356432373336663831323963656135323765333333616634373262633932613035622072656465656D5CDBF505000000001976A914F870774783FF34265F03A859985AD44FA5EC4A4788AC00000000"
}
```

</p>
</details>

---

**Staking status (SCP-2)**

Get the SCP-2 staking status of a given account and token.

```bash
GET /api/v1/wallet/getstakingstatus/:contract/:account
```

Example: `curl -X GET "localhost:3000/api/v1/wallet/getstakingstatus/69a3bd3c864b69390e02cc43a0f9725d2736f8129cea527e333af472bc92a05b/sgu2PRDZv9yeqco6ouVG5WvPegZ7iVHFod"`

**Fullnode required**: NO

**Parameters**:

| Name | Mandatory | Description |
|---------|---------|---------|
| contract | YES | The tokens unique contract id |
| address | YES | The account address |

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
{
    "enabled": true,
    "age": 11,
    "unclaimed_rewards": 18995484,
    "weight": 0.018995484582832304,
    "note": "currently staking 10,001.665 TEST with an age of 11 blocks, with 0.19 TEST in unclaimed stake rewards"
}
```

</p>
</details>