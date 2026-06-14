# ValidFi DApp on Stellar Soroban

A decentralized identity and data verification platform built on the Stellar Soroban Smart Contract Platform. SecureData enables users to securely store, verify, and share their identity documents using blockchain technology, zero-knowledge proofs, and AI-powered verification.

## 🌟 Features

### Core Capabilities
- **Self-Sovereign Identity Management**: Users have full control over their digital identities and personal data
- **AI-Assisted Document Verification**: Automated document analysis using Groq AI (Llama 4, DeepSeek R1, Mixtral)
- **Privacy-Preserving zk Proofs**: Zero-knowledge proofs enable verification without revealing sensitive data
- **Wallet-Based Authentication**: Secure authentication using Stellar wallets (Freighter, Albedo, LOBSTR)
- **Decentralized Storage**: Documents stored on IPFS with Pinata integration
- **User-Controlled Access Permissions**: Granular control over who can access your data
- **Instant Credential Sharing**: Share verified credentials with third parties securely
- **Tamper-Proof Verification Records**: All verification records stored on-chain for immutability

### Advanced Features
- **Time-Limited Access**: Set expiration dates for shared documents
- **Revocable Access**: Revoke access to shared documents at any time
- **Risk Assessment**: AI-powered risk scoring for document verification
- **Multi-Wallet Support**: Support for multiple Stellar wallet providers
- **Encrypted Storage**: All documents encrypted before storage
- **Audit Trail**: Complete audit trail of all data access and sharing events

## 🏗️ Architecture

### On-Chain Components (Soroban Smart Contracts)

#### Identity Registry Contract
- Manages user digital identities
- Stores identity metadata and verification status
- Links wallet addresses to identity records
- Enables identity lookup and verification

#### Verification Contract
- Handles document verification requests
- Validates zero-knowledge proofs
- Stores verification results on-chain
- Manages verification status updates

#### Access Control Contract
- Manages permissions and access rights
- Controls who can access specific data
- Implements time-based access controls
- Handles access revocation

#### Data Sharing Contract
- Controls document sharing with encryption
- Manages sharing permissions and expiration
- Tracks access logs
- Enables secure data transfer

### Off-Chain Components

#### Backend (NestJS)
- RESTful API for frontend communication
- Business logic for identity, verification, and data sharing
- Integration with external services (IPFS, AI, Soroban)
- Authentication and authorization middleware
- Database management with PostgreSQL
- Caching with Redis

#### Frontend (Next.js 15)
- Modern, responsive user interface
- Wallet connection and management
- Identity vault for document management
- Verification center for tracking status
- Secure sharing interface
- Real-time updates and notifications

#### Storage Layer (IPFS)
- Decentralized document storage
- Pinata gateway for reliable access
- Content-addressed storage
- Automatic deduplication

#### AI Layer (Groq)
- Document analysis and verification
- Risk assessment scoring
- Fraud detection
- Automated compliance checks

#### Zero-Knowledge Infrastructure
- Circom for circuit creation
- SnarkJS for proof generation
- Groth16 proving system
- Privacy-preserving verification

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 15.1.0
- **Language**: TypeScript
- **Styling**: TailwindCSS
- **UI Components**: Shadcn UI, Radix UI
- **Animations**: Framer Motion
- **Forms**: React Hook Form, Zod
- **Icons**: Lucide React
- **HTTP Client**: Axios
- **Wallet Integration**: @stellar/freighter-api

### Backend
- **Framework**: NestJS
- **Language**: TypeScript
- **Database**: PostgreSQL with TypeORM
- **Caching**: Redis
- **Authentication**: JWT, Passport
- **Validation**: class-validator, class-transformer
- **Blockchain**: Soroban SDK
- **Storage**: IPFS, Pinata SDK
- **AI**: Groq SDK

### Smart Contracts
- **Language**: Rust
- **Platform**: Stellar Soroban
- **Build Tool**: Cargo
- **Testing**: Soroban SDK

### DevOps
- **Version Control**: Git
- **Containerization**: Docker
- **CI/CD**: GitHub Actions
- **Deployment**: Vercel (frontend), Docker (backend)

## 📁 Project Structure

```
GuardZero/
├── contracts/                 # Soroban smart contracts (Rust)
│   ├── src/                  # Contract source code
│   └── Cargo.toml           # Rust dependencies
├── backend/                   # NestJS backend
│   ├── src/
│   │   ├── auth/            # Authentication module
│   │   ├── data-sharing/    # Data sharing module
│   │   ├── identity/        # Identity module
│   │   ├── ipfs/            # IPFS integration
│   │   ├── ai/              # AI service
│   │   ├── soroban/         # Soroban integration
│   │   └── verification/    # Verification module
│   ├── .env.example         # Environment variables template
│   └── package.json         # Backend dependencies
├── frontend/                  # Next.js 15 frontend
│   ├── src/
│   │   ├── app/            # Next.js app directory
│   │   └── components/     # React components
│   ├── public/              # Static assets
│   ├── .env.local          # Frontend environment variables
│   └── package.json        # Frontend dependencies
├── zk/                       # Zero-Knowledge proof infrastructure
│   └── README.md           # ZK proof documentation
├── scripts/                   # Deployment and utility scripts
│   ├── deploy-contracts.sh  # Smart contract deployment
│   └── deploy-backend.sh    # Backend deployment
├── .gitignore               # Git ignore rules
├── DEPLOYMENT.md            # Deployment guide
└── README.md                # This file
```

## 🚀 Getting Started

### Prerequisites

- **Node.js**: 18.0 or higher
- **Rust**: 1.70 or higher
- **Cargo**: Latest version
- **Soroban CLI**: Latest version
- **PostgreSQL**: 14 or higher
- **Redis**: 7 or higher
- **Git**: Latest version

### Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/GuardZero144/SureData.git
cd GuardZero
```

#### 2. Install Smart Contract Dependencies

```bash
cd contracts
cargo build --release
```

#### 3. Setup Backend

```bash
cd ../backend
npm install
cp .env.example .env
# Edit .env with your configuration
npm run start:dev
```

#### 4. Setup Frontend

```bash
cd ../frontend
npm install
cp .env.local.example .env.local
# Edit .env.local with your configuration
npm run dev
```

### Environment Variables

#### Backend (.env)

```bash
NODE_ENV=development
PORT=3001
API_PREFIX=api/v1

# Database
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=your_password
DB_DATABASE=securedata

# Redis
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=

# Stellar Soroban
SOROBAN_NETWORK_URL=https://soroban-testnet.stellar.org
SOROBAN_NETWORK_PASSPHRASE=Test SDF Network ; September 2015
IDENTITY_REGISTRY_CONTRACT_ID=your_contract_id
VERIFICATION_CONTRACT_ID=your_contract_id
ACCESS_CONTROL_CONTRACT_ID=your_contract_id
DATA_SHARING_CONTRACT_ID=your_contract_id

# IPFS / Pinata
PINATA_API_KEY=your_pinata_api_key
PINATA_API_SECRET=your_pinata_api_secret
PINATA_GATEWAY=https://gateway.pinata.cloud/ipfs/

# Groq AI
GROQ_API_KEY=your_groq_api_key

# JWT
JWT_SECRET=your_secret_key
JWT_EXPIRES_IN=7d

# Encryption
ENCRYPTION_KEY=your_32_byte_encryption_key
```

#### Frontend (.env.local)

```bash
NEXT_PUBLIC_API_URL=http://localhost:3001/api/v1
```

## 📖 Usage Guide

### Connecting Your Wallet

1. Install a Stellar wallet (Freighter, Albedo, or LOBSTR)
2. Click "Connect Wallet" on the homepage
3. Approve the connection request in your wallet
4. Your wallet address will be displayed

### Managing Your Identity

1. Navigate to the "Identity Vault" tab
2. Click "Select File" to upload a document
3. The document will be encrypted and uploaded to IPFS
4. The hash will be registered on-chain
5. Track verification status in the "Verification Center"

### Sharing Documents

1. Navigate to the "Secure Sharing" tab
2. Enter the recipient's wallet address
3. Select the document you want to share
4. Set the access duration
5. Click "Share Document"
6. The recipient will receive access for the specified duration

### Verifying Documents

1. Documents are automatically analyzed by AI
2. Risk assessment scores are generated
3. Zero-knowledge proofs are created for verification
4. Verification results are stored on-chain
5. Track status in the "Verification Center"

## 🔧 API Documentation

### Authentication Endpoints

#### POST /api/v1/auth/login
Login with wallet signature

#### POST /api/v1/auth/verify
Verify wallet signature

#### GET /api/v1/auth/profile
Get user profile (requires authentication)

### Identity Endpoints

#### POST /api/v1/identity
Create new identity

#### GET /api/v1/identity/:id
Get identity by ID

#### PUT /api/v1/identity/:id
Update identity

#### DELETE /api/v1/identity/:id
Delete identity

### Verification Endpoints

#### POST /api/v1/verification
Submit document for verification

#### GET /api/v1/verification/:id
Get verification status

#### GET /api/v1/verification
List all verifications

### Data Sharing Endpoints

#### POST /api/v1/data-sharing
Share data with another user

#### GET /api/v1/data-sharing/:id
Get sharing details

#### PUT /api/v1/data-sharing/:id/revoke
Revoke shared access

#### PUT /api/v1/data-sharing/:id/extend
Extend sharing duration

## 🧪 Testing

### Run Smart Contract Tests

```bash
cd contracts
cargo test
```

### Run Backend Tests

```bash
cd backend
npm run test
```

### Run Frontend Tests

```bash
cd frontend
npm run test
```

## 🚢 Deployment

### Deploy Smart Contracts

```bash
./scripts/deploy-contracts.sh testnet GYOUR_WALLET_ADDRESS
```

### Deploy Backend

```bash
./scripts/deploy-backend.sh production
```

### Deploy Frontend

The frontend can be deployed to Vercel:

```bash
cd frontend
vercel deploy
```

For detailed deployment instructions, see [DEPLOYMENT.md](DEPLOYMENT.md).

## 🔒 Security Considerations

- **Never commit `.env` files** to version control
- **Use strong secrets** for JWT and encryption keys
- **Enable HTTPS** in production environments
- **Implement rate limiting** on API endpoints
- **Use a reverse proxy** (nginx) for production
- **Regularly update dependencies** to patch vulnerabilities
- **Monitor for suspicious activity** and implement alerts
- **Encrypt all sensitive data** before storage
- **Use hardware wallets** for production accounts

## 🤝 Contributing

We welcome contributions to SecureData! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow the existing code style
- Write tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting
- Use meaningful commit messages

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

- **GitHub Issues**: https://github.com/GuardZero144/SureData/issues
- **Documentation**: https://github.com/GuardZero144/SureData/wiki
- **Discord**: [Join our Discord server]

## 🙏 Acknowledgments

- Stellar Development Foundation for Soroban
- Groq for AI services
- Pinata for IPFS hosting
- The open-source community

## 🗺️ Roadmap

### Phase 1 (Completed)
- ✅ Smart contract development
- ✅ Backend API implementation
- ✅ Frontend UI development
- ✅ Basic wallet integration
- ✅ IPFS integration
- ✅ AI-powered verification

### Phase 2 (In Progress)
- 🔄 Advanced zk-proof circuits
- 🔄 Mobile app development
- 🔄 Multi-chain support
- 🔄 Enhanced security features

### Phase 3 (Planned)
- 📋 Enterprise features
- 📋 Compliance certifications
- 📋 Advanced analytics
- 📋 Community governance

---

**Built with ❤️ for the decentralized future**
