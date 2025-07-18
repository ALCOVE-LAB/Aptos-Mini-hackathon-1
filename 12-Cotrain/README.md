# CoTrain - Collaborative AI Training Platform on Aptos

<div align="center">
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js" />
  <img src="https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white" alt="NestJS" />
  <img src="https://img.shields.io/badge/Aptos-000000?style=for-the-badge&logo=aptos&logoColor=white" alt="Aptos" />
  <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis" />
</div>

## 🌟 Overview

CoTrain is a revolutionary collaborative AI training platform built on the Aptos blockchain. It enables distributed machine learning where participants can contribute data, computational resources, and expertise while being fairly rewarded through blockchain-based incentives.

### Key Features

- 🤖 **Collaborative AI Training**: Distributed machine learning with multiple participants
- 🔗 **Blockchain Integration**: Built on Aptos for transparency and fair rewards
- 💰 **Tokenized Incentives**: Earn tokens for contributing data, compute, and expertise
- 🔒 **Privacy-Preserving**: Federated learning ensures data privacy
- 📊 **Real-time Monitoring**: Track training progress and model performance
- 🌐 **Web3 Integration**: Seamless wallet connection and blockchain interactions
- 📱 **Modern UI/UX**: Responsive design with dark/light mode support

## 🏗️ Architecture

This is a monorepo containing:

```
co-train_aptos/
├── apps/
│   ├── frontend/          # Next.js web application
│   └── backend/           # NestJS API server
├── packages/
│   ├── shared-types/      # Shared TypeScript types
│   ├── shared-utils/      # Common utility functions
│   └── shared-config/     # Configuration management
├── CotrainCore/          # Core AI training service (Python) with distributed training
├── move/                 # Aptos Move smart contracts
├── configs/              # Shared configuration files
├── scripts/              # Development and deployment scripts
└── docs/                 # Documentation
```

## 🚀 Quick Start

### Prerequisites

- **Node.js** >= 18.0.0
- **pnpm** >= 8.0.0
- **Docker** (for databases)
- **Git**
- **Aptos CLI** (for smart contracts)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/BytebunnyLabs/co-train_aptos.git
   cd co-train_aptos
   ```

2. **Run the setup script**
   ```bash
   pnpm setup
   ```
   This will:
   - Install all dependencies
   - Set up environment variables
   - Build shared packages
   - Start required services (PostgreSQL, Redis)
   - Run database migrations

3. **Start development servers**
   ```bash
   # Start all applications
   pnpm dev
   
   # Or start individually
   pnpm dev:frontend    # Frontend at http://localhost:3000
   pnpm dev:backend     # Backend at http://localhost:8000
   ```

## 📋 Available Scripts

### Development
```bash
pnpm dev                 # Start all apps in development mode
pnpm dev:frontend        # Start frontend only
pnpm dev:backend         # Start backend only
pnpm dev:cotrain-core    # Start CotrainCore service
pnpm setup              # Initial project setup
```

### Building
```bash
pnpm build              # Build all packages and apps
pnpm build:packages     # Build shared packages only
pnpm build:apps         # Build applications only
pnpm build:clean        # Clean build with fresh dependencies
pnpm build:prod         # Production build
```

### Testing
```bash
pnpm test               # Run all tests
pnpm test:unit          # Run unit tests
pnpm test:integration   # Run integration tests
pnpm test:e2e           # Run end-to-end tests
pnpm test:watch         # Run tests in watch mode
pnpm test:coverage      # Run tests with coverage
```

### Code Quality
```bash
pnpm lint               # Run linting
pnpm lint:fix           # Fix linting issues
pnpm format             # Format code with Prettier
pnpm type-check         # TypeScript type checking
pnpm security-check     # Security vulnerability check
pnpm quality            # Run all quality checks
```

### Database Management
```bash
pnpm db:start           # Start PostgreSQL and Redis
pnpm db:stop            # Stop databases
pnpm db:reset           # Reset database with fresh data
pnpm db:migrate         # Run database migrations
pnpm db:seed            # Seed database with sample data
pnpm db:status          # Check database status
```

### Smart Contracts
```bash
pnpm contracts:build    # Compile Move contracts
pnpm contracts:test     # Test Move contracts
pnpm contracts:deploy   # Deploy contracts to network
```

### Deployment
```bash
pnpm deploy:dev         # Deploy to development
pnpm deploy:staging     # Deploy to staging
pnpm deploy:prod        # Deploy to production
```

## 🔧 Configuration

### Environment Variables

Copy `.env.template` to `.env` and configure:

```bash
cp .env.template .env
```

Key configuration sections:
- **Database**: PostgreSQL connection settings
- **Redis**: Cache and session storage
- **JWT**: Authentication tokens
- **Aptos**: Blockchain network configuration
- **File Upload**: Storage settings
- **Email**: SMTP configuration
- **Monitoring**: Logging and analytics

### Development Setup

The setup script will guide you through:
1. Installing dependencies
2. Setting up environment variables
3. Starting required services
4. Running initial migrations
5. Creating sample data

## 🏛️ Smart Contracts

The platform uses Aptos Move smart contracts for:

- **Training Sessions**: Manage collaborative training rounds
- **Contributions**: Track data and compute contributions
- **Rewards**: Distribute tokens based on contributions
- **Governance**: Community voting on platform decisions

### Contract Development

```bash
cd move
aptos move compile      # Compile contracts
aptos move test         # Run contract tests
aptos move publish      # Deploy to network
```

### Key Functions

```move
// Create a new training session
public entry fun create_training_session(
    creator: &signer,
    session_id: u64,
    reward_amount: u64
)

// Register as a participant
public entry fun register_participant(
    participant: &signer,
    session_id: u64
)

// Submit contribution score
public entry fun submit_contribution(
    participant: &signer,
    session_id: u64,
    score: u64
)

// Complete session and distribute rewards
public entry fun complete_session_and_distribute(
    creator: &signer,
    session_id: u64
)
```

## 🧪 Testing

Comprehensive testing setup with:

- **Unit Tests**: Jest for individual components
- **Integration Tests**: API and database testing
- **E2E Tests**: Playwright for full user flows
- **Contract Tests**: Move testing framework

### Running Tests

```bash
# Run specific test types
pnpm test:unit
pnpm test:integration
pnpm test:e2e

# Run tests for specific packages
pnpm --filter '@cotrain/frontend' test
pnpm --filter '@cotrain/backend' test

# Watch mode for development
pnpm test:watch
```

## 📦 Package Structure

### Shared Packages

- **`@cotrain/shared-types`**: TypeScript type definitions
- **`@cotrain/shared-utils`**: Common utility functions
- **`@cotrain/shared-config`**: Configuration management

### Applications

- **`@cotrain/frontend`**: Next.js web application
- **`@cotrain/backend`**: NestJS API server
- **`CotrainCore`**: Core AI training service (Python/FastAPI) with distributed training

## 📱 Applications

### Frontend Application

**Tech Stack**: Next.js 14, TypeScript, Tailwind CSS, shadcn/ui, Aptos Wallet Adapter

**Features**:
- Modern responsive UI with dark/light mode
- Aptos wallet integration with multiple wallet support
- Real-time training session monitoring
- Contributor dashboard and profile management
- Token reward tracking and history

**Development**:
```bash
cd apps/frontend
pnpm dev
```

### Backend API

**Tech Stack**: NestJS, TypeScript, PostgreSQL, Redis, TypeORM, JWT Authentication

**Features**:
- RESTful API with Swagger documentation
- User authentication and authorization
- Training session management
- Real-time WebSocket communication
- File upload for training data
- Blockchain integration with Aptos SDK

**Development**:
```bash
cd apps/backend
pnpm start:dev
```

**API Documentation**: Available at `http://localhost:3001/api/docs`

### CotrainCore Service

**Tech Stack**: Python, FastAPI, PyTorch, Transformers, Redis

**Features**:
- Core AI training functionality
- Training session management and monitoring
- Real-time training metrics and logging
- Configuration management for training parameters
- RESTful API for training operations
- Integration with distributed training frameworks

**Development**:
```bash
cd CotrainCore
pnpm dev:cotrain-core
```

**API Documentation**: Available at `http://localhost:8002/docs`

## 🚀 Deployment

### Development
```bash
pnpm deploy:dev
```

### Staging
```bash
pnpm deploy:staging
```

### Production
```bash
pnpm deploy:prod
```

Deployment supports:
- **Docker Compose**: Local and staging deployments
- **Kubernetes**: Production-ready orchestration
- **Manual**: Traditional server deployment

### Production Deployment

1. **Frontend**: Deploy to Vercel (see [Deployment Guide](./docs/deployment/vercel.md))
2. **Backend**: Deploy to your preferred cloud provider
3. **Database**: Use managed PostgreSQL and Redis services
4. **Smart Contracts**: Deploy to Aptos mainnet

### Docker Deployment

```bash
# Build and run with Docker Compose
docker-compose up --build
```

## 🤝 Contributing

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Make your changes**
4. **Run quality checks**
   ```bash
   pnpm quality
   pnpm test
   ```
5. **Commit your changes**
   ```bash
   git commit -m 'Add amazing feature'
   ```
6. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
7. **Open a Pull Request**

### Development Guidelines

- Follow TypeScript best practices
- Write tests for new features
- Use conventional commit messages
- Ensure all quality checks pass
- Update documentation as needed

## 📚 Documentation

- [API Documentation](./docs/api/README.md)
- [Frontend Guide](./apps/frontend/README.md)
- [Backend Guide](./apps/backend/README.md)
- [Smart Contracts](./move/README.md)
- [Integration Guide](./INTEGRATION.md)
- [Deployment Guide](./docs/deployment/vercel.md)
- [Quick Start Guide](./docs/quick-start.md)

## 🔍 Monitoring & Analytics

- **Application Monitoring**: Real-time performance metrics
- **Error Tracking**: Comprehensive error logging
- **User Analytics**: Usage patterns and insights
- **Blockchain Monitoring**: Transaction and contract events

## 🛡️ Security

- **Authentication**: JWT-based with refresh tokens
- **Authorization**: Role-based access control
- **Data Encryption**: At rest and in transit
- **Smart Contract Audits**: Regular security reviews
- **Dependency Scanning**: Automated vulnerability checks

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Aptos Labs](https://aptoslabs.com/) for the blockchain infrastructure
- [Next.js](https://nextjs.org/) for the frontend framework
- [NestJS](https://nestjs.com/) for the backend framework
- [shadcn/ui](https://ui.shadcn.com/) for the UI components
- The open-source community for amazing tools and libraries

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/BytebunnyLabs/co-train_aptos/issues)
- **Discussions**: [GitHub Discussions](https://github.com/BytebunnyLabs/co-train_aptos/discussions)
- **Email**: support@cotrain.ai
- **Discord**: [Join our community](https://discord.gg/cotrain)

---

<div align="center">
  <p>Built with ❤️ by the CoTrain Team</p>
  <p>Empowering collaborative AI through blockchain technology</p>
</div>
