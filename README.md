# Collateral Vault Smart Contract

A Clarity smart contract for NFT-collateralized lending on the Stacks blockchain. This contract enables users to use their NFTs as collateral for STX loans.

## Features

- **NFT Collateral**: Lock SIP009-compliant NFTs as loan collateral
- **Flexible Terms**: Customizable loan amounts, repayment terms, and due dates
- **Secure Lending**: Built-in security checks and validations
- **Automated Processing**: Smart contract handles loan funding, repayments, and defaults

## Contract Functions

### Core Functions

```clarity
(create-loan (nft-id uint) (loan-principal uint) (loan-repay uint) (loan-due uint))
(fund-loan (id uint))
(repay-loan (id uint))
(claim-collateral (id uint))
```

### View Functions

```clarity
(get-loan (id uint))
(get-last-token-id)
(get-token-uri (id uint))
(get-owner (id uint))
```

## Error Codes

| Code | Description |
|------|-------------|
| u100 | Not borrower |
| u101 | Not lender |
| u102 | Loan not found |
| u103 | Already repaid |
| u104 | Not due yet |
| u105 | Not collateralized |
| u200 | Already funded |
| u201 | Transfer failed |

## Usage

1. **Creating a Loan**
   - Borrower calls `create-loan` with NFT ID and loan terms
   - NFT is locked in contract

2. **Funding a Loan**
   - Lender calls `fund-loan` with loan ID
   - STX transferred to borrower

3. **Repaying a Loan**
   - Borrower calls `repay-loan` before due date
   - STX transferred to lender

4. **Defaulted Loans**
   - Lender can claim NFT collateral after due date
   - Called via `claim-collateral`

## Security

- Principal validation
- Amount validation
- Block height checks
- Ownership verification
- State transition guards
- Transfer safety checks

## Development

Built with Clarity for Stacks blockchain.

### Prerequisites

- Stacks blockchain
- Clarinet
- NFT implementing SIP009 trait

### Testing

```bash
clarinet test
```
