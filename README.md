# LegacyETH Open Dataset

LegacyETH Open Dataset is a public index of historical Ethereum contracts and unclaimed on-chain asset records.

The dataset focuses on legacy Ethereum contracts, discontinued protocols, migration vaults, refund mechanisms, and other historical systems where assets may remain claimable or recoverable through on-chain contract interaction.

## What is included

- 287 indexed historical Ethereum contracts
- Contract names and Ethereum mainnet contract addresses
- Project categories and metadata
- Unclaimed asset type, primarily ETH
- Total indexed unclaimed amounts by contract
- Wallet-address-level balance records
- Data source notes
- SHA-256 file integrity checksums

## Directory structure

```text
data/
  protocols.json              # contract index: key, name, address, balance file
  protocol_info.json          # extended project metadata where available
  total.json                  # aggregate dataset totals
  table_meta/                 # per-contract summary metadata
  balances/                   # per-contract wallet balance records
  index_shards/               # lookup shards for address-level search
SOURCE.md                     # upstream source and commit information
SHA256SUMS                    # SHA-256 checksums for dataset files
```

## Data format

Most balance files follow this structure:

```json
{
  "contract": "0x...",
  "balance_source": "eth",
  "contract_eth_balance": 0,
  "total_eth_in_balances": 0,
  "addresses_with_balance": 0,
  "scan_date": "YYYY-MM-DD HH:MM:SS UTC",
  "balances": [
    {
      "address": "0x...",
      "balance_wei": "0",
      "balance_eth": 0
    }
  ]
}
```

## Verification

After cloning, verify file integrity with:

```bash
shasum -a 256 -c SHA256SUMS
```

## Important notice

This repository is an open data index. It is not financial advice, legal advice, or a guarantee that any wallet is eligible to claim assets. Eligibility and claim paths vary by contract and should be independently verified on-chain before any transaction is submitted.

LegacyETH never requires private keys or seed phrases.

## License

The dataset is released under CC0 1.0 Universal. See `LICENSE`.
