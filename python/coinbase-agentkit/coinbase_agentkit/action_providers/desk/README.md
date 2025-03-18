# DESK Action Provider

This directory contains the **DeskActionProvider** implementation, which provides actions for interacting with the DESK trading platform.

## Overview

The DeskActionProvider is designed to work with EthAccountWalletProvider for blockchain interactions. It provides a set of actions that enable users to interact with the DESK trading platform, view account information, check market data, and execute trades.

## Directory Structure

```
desk/
├── __init__.py # Package exports
├── desk_action_provider.py # Main provider implementation
├── schemas.py # Action schemas and types
├── utils.py # Utility functions
└── README.md # Documentation (this file)

```

## Supported Actions
```
  get_subaccount_summary
  get_market_info
  get_collaterals_info
  get_current_funding_rate
  get_historical_funding_rates
  get_last_trades
  get_mark_price
  place_order
  cancel_order
  cancel_all_orders
  deposit_collateral
  withdraw_collateral
```


## Implementation Details

### Network Support
- Base `8453`
- Arbitrum Sepolia `421614`

### Wallet Provider Integration
This provider is designed to work with EthAccountWalletProvider. Key integration points:
- Authentication with the DESK platform
- Account management and subaccount access
- Transaction signing for trading operations

## Configuration

The DeskActionProvider requires the following configuration:
- `private_key`: The private key for the Ethereum account
- `chain_id`: The chain to connect to. currently supported '8453' (base) and '421614' (arbitrum sepolia)
- `sub_account_id`: The subaccount ID to use for trading
- `rpc_url` (optional): RPC url to use

Example configuration:
```python
from coinbase_agentkit.action_providers.desk.schemas import DeskConfigSchema
from coinbase_agentkit import desk_action_provider

provider = desk_action_provider(
        private_key="0x123"
        sub_account_id=1
        chain_id=8453
        rpc_url="https://rpc.url
  )
```

## Notes
- The DESK platform requires authentication with a valid Ethereum account
- All actions return formatted JSON strings for easy parsing and display
- Position, order, and collateral information is formatted for human readability
- For detailed API documentation, refer to the DESK platform documentation