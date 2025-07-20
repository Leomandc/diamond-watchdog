# Diamond Watchdog

## Project Overview
Diamond Watchdog is a decentralized asset monitoring and verification platform leveraging the Stacks blockchain for transparent, secure digital asset tracking and trading. The platform enables peer-to-peer verification, automated settlement, and secure transaction infrastructure.

### Key Features
- Decentralized energy grid participant registration and management
- Peer-to-peer energy trading marketplace with real-time pricing
- Fungible energy tokens for standardized trading units
- Smart meter integration with verification system
- Secure grid operations and maintenance
- Automated trade settlement and dispute resolution

### Project Description
Diamond Watchdog revolutionizes digital asset verification by providing a decentralized platform for tracking and trading valuable assets. By leveraging the Stacks blockchain, Diamond Watchdog offers a transparent, secure, and efficient system for asset monitoring. The platform combines participant registration, trade verification, tokenization, and dispute resolution to create a comprehensive ecosystem for decentralized asset management.

## Contract Architecture

### grid-access-control.clar
The core registration and access control system for Diamond Watchdog participants. Enhanced with verification metadata support.

**Data Structures**:
- `registered-participants`: Stores participant information including verification capabilities
- `pending-registrations`: Manages registration requests
- `participant-metadata`: Enhanced verification statistics and reputation data

**Public Functions**:
- `register-participant`: Register new platform participants
- `approve-registration`: Approve pending registrations
- `update-participant-info`: Update participant information
- `remove-participant`: Remove participants from the system
- `update-reputation-score`: Modify participant reputation based on verification history
- `record-asset-transaction`: Log completed asset transactions

### trade-orchestrator.clar
The marketplace contract enabling peer-to-peer asset trading and verification.

**Key Features**:
- Asset listing management
- Dynamic pricing mechanisms
- Automated trade settlement
- Escrow system for secure transactions
- Dispute resolution system

**Public Functions**:
- `create-asset-listing`: List asset for sale
- `purchase-asset`: Buy listed asset
- `place-bid`: Bid on auction-style listings
- `finalize-auction`: Complete auction-style sales
- `confirm-delivery`: Verify asset delivery
- `settle-payment`: Process payment after delivery
- `open-dispute`: Initiate dispute resolution

### watchdog-token.clar
A SIP-010 compliant fungible token representing standardized verification units.

**Features**:
- Fungible verification unit representation
- Standard token operations (transfer, mint, burn)
- Role-based minting and burning permissions
- Integration with trading system

**Key Functions**:
- `mint`: Create new verification tokens
- `burn`: Remove tokens from circulation
- `transfer`: Transfer tokens between participants
- `get-balance`: Check token holdings

### meter-verification.clar
Asset tracking and verification system.

**Features**:
- Asset registration and management
- Verification status tracking
- Dispute resolution for registrations
- Provenance and ownership tracking

**Key Functions**:
- `register-asset`: Add new trackable assets
- `submit-verification`: Record verification status
- `verify-asset`: Validate submitted verifications
- `file-dispute`: Contest incorrect verifications
- `resolve-dispute`: Settle verification disputes

## Installation & Setup

1. Ensure you have Clarinet installed on your system.
2. Clone the Diamond Watchdog repository: `git clone https://github.com/diamond-watchdog/diamond-watchdog.git`
3. Navigate to the project directory: `cd diamond-watchdog`
4. Install the project dependencies: `npm install`
5. Run the Clarinet development environment: `clarinet dev`

## Usage Guide

### Participant Registration
```clarity
(register-participant 'ABCD1234 PARTICIPANT-TYPE-PRODUCER "location-data")
```

### Energy Trading
```clarity
;; List energy for sale
(create-energy-listing u1000 u500 PRICING-FIXED u0)

;; Purchase energy
(purchase-energy u1)

;; Place bid (for auction listings)
(place-bid u1 u550)
```

### Energy Token Operations
```clarity
;; Transfer energy tokens
(transfer u100 tx-sender 'RECIPIENT none)

;; Check balance
(get-balance 'ADDRESS)
```

### Smart Meter Integration
```clarity
;; Register a smart meter
(register-meter 0x1234 METER-TYPE-PRODUCER "location")

;; Submit reading
(submit-energy-reading 0x1234 block-height u100 0xSIGNATURE)
```

## Security Considerations

- **Role-Based Access Control**: Strict permissions for critical operations
- **Escrow System**: Secure trade settlement with funds in escrow
- **Verified Meters**: Only registered and verified meters can submit readings
- **Dispute Resolution**: Formal process for handling disputes
- **Multi-Stage Settlement**: Phased completion of trades with verification steps

## Examples

### Complete Trading Cycle
```clarity
;; 1. Create energy listing
(create-energy-listing u1000 u500 PRICING-FIXED u0)

;; 2. Purchase energy
(purchase-energy u1)

;; 3. Confirm delivery
(confirm-delivery u1)

;; 4. Settle payment
(settle-payment u1)
```

### Meter Reading Verification
```clarity
;; 1. Submit reading
(submit-energy-reading 0x1234 block-height u100 0xSIGNATURE)

;; 2. Verify reading
(verify-reading 0x1234 block-height true "Verification notes")
```

### Token Operations
```clarity
;; Mint tokens to producer
(mint u1000 'PRODUCER_ADDRESS)

;; Transfer tokens
(transfer u100 tx-sender 'CONSUMER_ADDRESS none)
```

The enhanced GridFlow system provides a complete solution for decentralized energy trading, from participant registration to final settlement, with robust security measures and dispute resolution mechanisms.