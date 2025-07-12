# DONUT Referral Matrix System

A decentralized multi-level referral system built on Solana blockchain that rewards participants for onboarding new users through a structured 3×1 matrix mechanism.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Solana](https://img.shields.io/badge/Solana-v1.18.15-blue)](https://solana.com/)
[![Anchor](https://img.shields.io/badge/Anchor-v0.29.0-blue)](https://github.com/coral-xyz/anchor)

## Overview

The DONUT Referral Matrix System implements a novel incentive structure using a 3-slot matrix for each participant. When a new user joins with a referrer, they fill one of the referrer's slots, triggering specific financial actions:

- **Slot 1**: Swap and burn donut tokens
- **Slot 2**: SOL is reserved
- **Slot 3**: Reserved SOL tokens paid to the referrer, completing their matrix

Once all three slots are filled, a new matrix is created, allowing continuous participation in the ecosystem.

## Key Features

- **Verifiable Smart Contract**: Open-source, auditable, and fully on-chain code
- **Chainlink Integration**: Reliable SOL/USD price oracles for minimum deposit validation
- **Meteora Pool Integration**: Direct interaction with official token pool with 100% locked liquidity
- **Secure Address Verification**: Strict validation of all critical addresses
- **Automated Upline Processing**: Manages referral chain relationships automatically

## Technical Architecture

### Matrix Structure

Each user operates a personal 3-slot matrix that captures referrals and controls financial operations. The system:

- Tracks slot filling in a ReferralChain structure
- Automatically processes new matrices when one is completed
- Emits on-chain events for referral tracking

### Upline Management

- Optimized data structures for memory efficiency
- Complete tracking between referrers and referees

### Chainlink Oracles

- SOL/USD price verification for minimum deposit determination
- Protection against stale price feeds (fallback to default price)
- Strict validation of Chainlink program and price feed addresses

### Airdrop Distribution

Each completed matrix automatically registers the user in the airdrop program and contributes to their weekly reward eligibility.
Weekly Distribution Mechanics

Duration: 36 weeks of progressive token distribution
Weekly: Each week has a predetermined DONUT token allocation
Distribution Formula: Weekly tokens ÷ Total matrices completed that week

### Security Features

- Rigorous account and address validation
- Detailed error handling for transparency
- Memory optimization to prevent computation errors
- Protection against reentrancy and other common vulnerabilities

## Technical Requirements

### Dependencies

- Solana CLI: v1.18.15 or higher
- Anchor Framework: v0.29.0
- Rust: v1.75.0 or higher (recommended)
- NodeJS: v16.0.0 or higher (for testing and scripts)

### Program Dependencies

\`\`\`toml
anchor-lang = "0.29.0"
anchor-spl = "0.29.0"
solana-program = "1.18.15"
spl-token = "4.0.0"
chainlink_solana = "1.0.0"
solana-security-txt = "1.1.1"
\`\`\`

### Accounts and PDAs

- \`program_state\`: Global program state
- \`user_account\`: Individual user accounts
- \`program_sol_vault\`: Program's SOL reserve

### Data Structures

- \`UserAccount\`: Stores user data, referrals, and matrix
- \`ReferralUpline\`: Chain of referrers
- \`ReferralChain\`: 3×1 matrix for each user
- \`UplineEntry\`: Detailed data for each referrer

## Program Instructions

1. **initialize**: Initialize the program state
2. **register_without_referrer**: Administrative registration without referrer (multisig only)
3. **register_with_sol_deposit**: Register a new user with SOL deposit

## Build Optimization

The project uses optimized build settings for release:

- Full LTO (Link Time Optimization)
- Single codegen unit for maximum optimization
- Overflow checks enabled for additional security
- Custom build overrides for optimal performance

## Security

Please see [SECURITY.md](./SECURITY.md) for our security policy and vulnerability reporting procedures.

## Contact

For questions, integrations, or support:

- Email: dev@mydonut.io
