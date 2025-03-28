# HAI Bot Architecture Diagram

```
+--------------------------------------------------+
|                                                  |
|                 User Interfaces                  |
|                                                  |
|  +-------------+  +-------------+  +----------+  |
|  |             |  |             |  |          |  |
|  | Discord Bot |  | Web App     |  | Telegram |  |
|  | (Current)   |  | (Future)    |  | (Future) |  |
|  +-------------+  +-------------+  +----------+  |
|          |               |               |       |
+----------|---------------|---------------|-------+
           |               |               |
           v               v               v
+--------------------------------------------------+
|                                                  |
|               API Gateway & Router               |
|                                                  |
+---------------------|---------------------------+
                      |
                      v
+--------------------------------------------------+
|                                                  |
|                Core HAI Bot Services             |
|                                                  |
|  +-------------+  +-------------+  +----------+  |
|  | AI Model    |  | Credit      |  | User     |  |
|  | Aggregator  |  | Management  |  | Profiles  |  |
|  | (180+ Models)|  |             |  |          |  |
|  +-------------+  +-------------+  +----------+  |
|                      |                           |
|  +-------------+  +--|----------+  +----------+  |
|  | Content     |  |              |  | Credit   |  |
|  | Generation  |  | Commands &   |  | Dashboard|  |
|  | Orchestrator|  | Permissions  |  |          |  |
|  +-------------+  +--------------+  +----------+  |
|                      |                           |
+----------------------|---------------------------+
                       |
                       v
+--------------------------------------------------+
|                                                  |
|          Hedera Integration Layer (Future)       |
|                                                  |
|  +-------------+  +-------------+  +----------+  |
|  | HCS         |  | HBAR/HAI    |  |          |  |
|  | Credit      |  | Transaction |  | HCS-SQL  |  |
|  | System      |  | Processing  |  | System   |  |
|  +-------------+  +-------------+  +----------+  |
|          |               |               |       |
+----------|---------------|---------------|-------+
           |               |               |
           v               v               v
+--------------------------------------------------+
|                                                  |
|                 Hedera Network                   |
|                                                  |
|  +-------------+  +-------------+  +----------+  |
|  | Consensus   |  | Token       |  | Smart    |  |
|  | Service     |  | Service     |  | Contracts|  |
|  | (HCS)       |  | (HTS)       |  | Service  |  |
|  +-------------+  +-------------+  +----------+  |
|                                                  |
+--------------------------------------------------+
           |               |               |
           v               v               v
+--------------------------------------------------+
|                                                  |
|                   Data Storage                   |
|                                                  |
|  +-------------+  +-------------+  +----------+  |
|  | Primary     |  | HCS Backup  |  | Usage    |  |
|  | Database    |  | (Future)    |  | Analytics |  |
|  +-------------+  +-------------+  +----------+  |
|                                                  |
+--------------------------------------------------+
```

## Key Components

### User Interfaces
- **Discord Bot**: Current primary interface for HAI Bot
- **Web Application**: Planned (within 6 months) with node-based workflow system
- **Telegram Bot**: Potential future integration

### Core Services
- **AI Model Aggregator**: Manages connections to 180+ AI models
- **Credit Management**: Handles user credits and access to premium features
- **Content Generation Orchestrator**: Routes requests to appropriate AI models
- **Credit Dashboard**: Provides statistics on token usage and transactions

### Current Payment Flow
- User issues `/deposit credit` command
- System provides Hedera account ID and unique memo
- User sends HBAR or HAI to treasury account with memo
- Credits become available in the specific server/DM where deposit was initiated

### Hedera Integration Layer (Planned)
- **HCS Credit System**: Will maintain tamper-proof record of user credits
- **HBAR/HAI Transaction Processing**: Facilitates credit purchases and usage
- **HCS-SQL System**: Will provide real-time SQL database mirroring to Hedera

### Hedera Network
- **Consensus Service (HCS)**: Will be used for secure, tamper-proof transaction logging
- **Token Service (HTS)**: Currently used for accepting HBAR/HAI payments
- **Smart Contracts Service**: Potential future integration for advanced features

### Data Storage
- **Primary Database**: Main operational database for the platform
- **HCS Backup Database**: Future mirror of critical data secured via Hedera
- **Usage Analytics**: Tracks token usage and transaction statistics

## Current Implementation

### Discord Bot
- Full functionality via Discord commands
- Support for text, image, video, 3D, and other AI modalities
- Credit system with dashboard for tracking usage

### Credit System
- Server-specific or DM-specific credit pools
- Manual deposit process using Hedera wallets
- Credits consumed based on AI model usage

## Planned Enhancements

### Web Application (Within 6 Months)
- All Discord features available on web
- Node-based interface for complex workflows
- Deeper asset creation capabilities
- Cross-platform credit synchronization

### HCS-SQL Implementation
- Database backup solution using Hedera Consensus Service
- Will provide immutable backup of credit system
- Enhanced security and transparent tracking

### Analytics Platform
- Using HCS to identify trending AI models
- Tracking usage patterns without recording user prompts
- Monitoring transaction volume and system performance
- Providing insights into AI model popularity and performance
- Preserving user privacy while gathering valuable usage data

### Use Cases
- NFT community content creation
- Game development asset creation
- Digital art and creative workflows 