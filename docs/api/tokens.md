# Tokens API

**All Tokens**

Returns the complete 'state' of SCP, including all tokens with their meta data, owners/accounts, activity and balances.

```bash
GET /api/v1/tokens/getalltokens
```

Example: `curl -X GET "https://stakecubecoin.net/web3/scp/tokens/getalltokens"`

**Fullnode required**: YES

**Parameters**: NONE

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
[
    {
        "version": 2,
        "contract": "063d1363528d29670cd8b0541e31a9c2d53edfff6070490ba165d9569111bc26",
        "name": "Moments",
        "ticker": "MMT",
        "maxSupply": 1000000000000000,
        "supply": 522113447567462,
        "creator": "sVJzD3nn4sFcadjZLXfo2UNMfTHqMd1B4W",
        "owners": [
            {
                "address": "sNVWSUa9tfNuPqeuUTjoUDo8tsbo355xej",
                "balance": 31615991124,
                "unclaimed_balance": 46880513,
                "lastTxBlock": 182409,
                "activity": [
                    {
                        "id": "104983ed44a50d2c02588f1a5a7640580760f03fe281c160fab00bc08e16962b",
                        "block": 178388,
                        "type": "received",
                        "amount": 25503850291
                    },
                    {
                        "id": "d4c4dc30d5f3eb5200205a6d1dfa4c31dddc2cbdc66aebe4cf140f8eccb2a010",
                        "block": 180286,
                        "type": "staked",
                        "amount": 34191380
                    },
                    {
                        "id": "4bd18b8a3a14185e82fb48808c7024601ff4c73046af9230f886c2fe21d86261",
                        "block": 180288,
                        "type": "sent",
                        "amount": 25538041671
                    },
                    ...
                ]
            }
        ],
        "inflation": 380000000,
        "minAge": 60
    },
    ...
]
```

</p>
</details>  

---

**Single Token**

Returns the complete 'state' of a single token with its meta data, owners/accounts, activity and balances.

```bash
GET /api/v1/tokens/gettoken/:contract
```

Example: `curl -X GET "https://stakecubecoin.net/web3/scp/tokens/gettoken/063d1363528d29670cd8b0541e31a9c2d53edfff6070490ba165d9569111bc26"`

**Fullnode required**: YES

**Parameters**:

| Name | Mandatory | Description |
|---------|---------|---------|
| contract | YES | The unique contract id |

<details>
<summary><strong>Example Response</strong></summary>
<p>

```json
{
    "version": 2,
    "contract": "063d1363528d29670cd8b0541e31a9c2d53edfff6070490ba165d9569111bc26",
    "name": "Moments",
    "ticker": "MMT",
    "maxSupply": 1000000000000000,
    "supply": 522113447567462,
    "creator": "sVJzD3nn4sFcadjZLXfo2UNMfTHqMd1B4W",
    "owners": [
        {
            "address": "sNVWSUa9tfNuPqeuUTjoUDo8tsbo355xej",
            "balance": 31615991124,
            "unclaimed_balance": 46880513,
            "lastTxBlock": 182409,
            "activity": [
                {
                    "id": "104983ed44a50d2c02588f1a5a7640580760f03fe281c160fab00bc08e16962b",
                    "block": 178388,
                    "type": "received",
                    "amount": 25503850291
                },
                {
                    "id": "d4c4dc30d5f3eb5200205a6d1dfa4c31dddc2cbdc66aebe4cf140f8eccb2a010",
                    "block": 180286,
                    "type": "staked",
                    "amount": 34191380
                },
                {
                    "id": "4bd18b8a3a14185e82fb48808c7024601ff4c73046af9230f886c2fe21d86261",
                    "block": 180288,
                    "type": "sent",
                    "amount": 25538041671
                },
                ...
            ]
        }
    ],
    "inflation": 380000000,
    "minAge": 60
}
```

</p>
</details>  

---

**Tokens by Account**

Finds and returns the complete 'state' of SCP, including all tokens with their meta data, owners/accounts, activity and balances by a specified address.

```bash
GET /api/v1/tokens/gettokensbyaccount/:account
```

Example: `curl -X GET "https://stakecubecoin.net/web3/scp/tokens/gettokensbyaccount/sbQVsmW9uXsCXdd1YaRSLWYJfc4sn8msvv"`

**Fullnode required**: YES

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
        "token": {
            "version": 2,
            "contract": "69a3bd3c864b69390e02cc43a0f9725d2736f8129cea527e333af472bc92a05b",
            "name": "SCP-Faucet",
            "ticker": "TEST",
            "maxSupply": 5000000000000000,
            "supply": 52652787702025,
            "creator": "sY2NPdY7TSpmH3Es1Ao4cB8mB9odbT1S2g",
            "inflation": 500000000,
            "minAge": 2
        },
        "account": {
            "address": "sbQVsmW9uXsCXdd1YaRSLWYJfc4sn8msvv",
            "balance": 10022551565686,
            "unclaimed_balance": 932696376542,
            "lastTxBlock": 174704,
            "activity": [
                {
                    "id": "bbe9c893d2873f168beae6b13b2ce312ddacaea4bf79ec1bce5f058238ae777f",
                    "block": 174704,
                    "type": "received",
                    "amount": 10000000000000
                },
                {
                    "id": "a51269b6dd7a75dc7dc7ac63b98dead476c7c422f68906df6df9ec3721a35a35",
                    "block": 174905,
                    "type": "staked",
                    "amount": 19679146218
                },
                {
                    "id": "358dc2ca2ac7e1331d953868b3d1a9de07a4ab881e67d6f1facf73a70152a8fb",
                    "block": 174930,
                    "type": "staked",
                    "amount": 2476156000
                },
                {
                    "id": "32660d6f9ca16b9b003ca49c4965b5b59a55f39b0db41ad15d45cacb43b71b89",
                    "block": 174934,
                    "type": "staked",
                    "amount": 396263468
                }
            ]
        }
	},
    ...
]
```

</p>
</details>