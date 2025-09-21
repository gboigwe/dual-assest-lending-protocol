# Stacks Lending Pool

A decentralized lending protocol on the Stacks blockchain that enables users to deposit STX as liquidity, borrow STX against sBTC collateral, and earn interest on deposits.

## Overview

This project implements a dual-asset lending pool where:
- **Lenders** deposit STX tokens to earn interest
- **Borrowers** provide sBTC as collateral to borrow STX
- **Liquidators** can liquidate undercollateralized positions

## Key Features

- **STX Deposits**: Lenders can deposit STX and earn interest over time
- **sBTC Collateral**: Borrowers deposit sBTC to secure STX loans
- **Interest Accrual**: 10% annual interest rate on borrowed STX
- **Liquidation Mechanism**: Positions can be liquidated when collateral value drops
- **Price Oracle Integration**: Uses mock oracle for sBTC/STX price feeds

## Protocol Parameters

- **Loan-to-Value (LTV)**: 70%
- **Interest Rate**: 10% annually
- **Liquidation Threshold**: 100%

## Smart Contracts

### `lending-pool.clar`
Main lending protocol contract with the following public functions:
- `deposit-stx`: Deposit STX to earn interest
- `withdraw-stx`: Withdraw STX deposits plus accrued interest
- `borrow-stx`: Borrow STX against sBTC collateral
- `repay`: Repay borrowed STX with accrued interest
- `liquidate`: Liquidate undercollateralized positions

### `mock-oracle.clar`
Price oracle contract for testing purposes that provides sBTC/STX exchange rates.

## Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) - Stacks smart contract development toolkit
- [Node.js](https://nodejs.org/) - For running tests

## Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```

## Testing

Run the test suite:
```bash
npm test
```

Run tests with coverage and cost analysis:
```bash
npm run test:report
```

Watch for changes and auto-run tests:
```bash
npm run test:watch
```

## Project Structure

```
.
├── contracts/
│   ├── lending-pool.clar      # Main lending protocol
│   └── mock-oracle.clar       # Price oracle for testing
├── tests/
│   ├── lending-pool.test.ts   # Protocol tests
│   └── mock-oracle.test.ts    # Oracle tests
├── deployments/               # Deployment configurations
├── settings/                  # Network configurations
└── Clarinet.toml             # Project configuration
```

## Dependencies

The protocol integrates with:
- `sbtc-token` - sBTC token contract
- `token-stx-v-1-2` - STX token interface
- `xyk-swap-helper-v-1-3` - AMM swap utilities
- `xyk-pool-sbtc-stx-v-1-1` - sBTC/STX liquidity pool

## Development

This project uses:
- **Clarity 3.0** smart contracts
- **Vitest** for testing
- **TypeScript** for test scripts
- **Clarinet SDK** for blockchain interactions

## License

ISC