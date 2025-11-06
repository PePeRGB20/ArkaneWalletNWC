# 💜 Purple Arkade Wallet

**Bitcoin on Nostr with native Arkade Zaps**

Purple Arkade Wallet is a fork of [Arkade Wallet](https://github.com/arkade-os/wallet) with integrated **Nostr Wallet Connect (NIP-47)** support, enabling native Arkade vtxo payments via Nostr without Lightning.

## ✨ Features

### Arkade Wallet Core
- ✅ **Non-custodial Bitcoin wallet** with Arkade vtxos
- ✅ Instant, private off-chain transfers
- ✅ On-chain compatibility
- ✅ Atomic swaps via Boltz
- ✅ DLC lending integration

### 💜 Purple Edition - Nostr Integration
- ✅ **NIP-47 Nostr Wallet Connect** server
- ✅ **Native Arkade Zaps** - Send vtxos via Nostr
- ✅ **No Lightning required** - Direct Arkade address payments
- ✅ QR code pairing with Nostr apps
- ✅ Multi-relay support (relay.damus.io, nos.lol, relay.primal.net)
- ✅ Connection management UI
- ✅ Compatible with Nostr clients (tested with jumble)

## 🚀 Quick Start

### Prerequisites
- Node.js v18+
- npm

### Installation

```bash
# Clone the repository
git clone https://github.com/PePeRGB20/ArkaneWalletNWC.git
cd ArkaneWalletNWC

# Install dependencies
npm install

# Build
npm run build

# Start development server
npm start
```

### Using Arkade Zaps

1. Open Purple Arkade Wallet
2. Go to **Settings > Wallet Connect**
3. Scan the QR code with your Nostr app (e.g., jumble)
4. Send a zap - it will use Arkade vtxos instead of Lightning!

## 🏗️ Architecture

### NWC Server
The wallet runs a NIP-47 compliant server that:
- Publishes kind 13194 wallet info events
- Listens for kind 23194 payment requests
- Responds with kind 23195 payment responses
- Supports methods: `pay_invoice`, `get_balance`, `get_info`, `make_invoice`

### Arkade Zaps Flow
1. Nostr app requests payment via NWC
2. Purple Arkade Wallet receives Arkade address
3. Wallet sends vtxos directly (no Lightning!)
4. Transaction confirmed on Arkade network

## 📁 Project Structure

```
src/
├── nwc/                    # Nostr Wallet Connect implementation
│   ├── server.ts           # NIP-47 server
│   ├── pairing.ts          # QR code & pairing logic
│   ├── storage.ts          # Connection persistence
│   └── README.md           # NWC documentation
├── providers/
│   └── nwc.tsx             # React context for NWC
└── screens/Settings/
    └── WalletConnect.tsx   # Connection management UI
```

## 🎨 Branding

Purple Arkade Wallet uses **violet/purple** as the dominant color to align with the Nostr ecosystem and nostriches community.

**Colors:**
- Primary: `#7C3AED` (Vibrant Violet)
- Background: `#1E1B4B` (Deep Purple)
- Accent: Purple variations

## 🔧 Development

### Key Technologies
- React + TypeScript
- Ionic Framework
- @arkade-os/sdk (Arkade network)
- nostr-tools (Nostr protocol)
- Vite

### Build Commands
```bash
npm run build          # Production build
npm run build:worker   # Build service worker
npm start              # Development server
```

## 🧪 Testing

Tested and working with:
- [jumble](https://jumble.social) - Nostr client
- Successful 42 sat zap transfer confirmed

## 📝 NIP-47 Implementation

Purple Arkade Wallet implements NIP-47 with Arkade-specific adaptations:

| NIP-47 Field | Arkade Implementation |
|--------------|----------------------|
| `invoice` | Arkade address (ark1...) |
| `amount` | Millisats → Sats conversion |
| `preimage` | vtxo transaction ID |

## Environment Variables

| Variable                    | Description                                                         | Example Value                                     |
| --------------------------- | ------------------------------------------------------------------- | ------------------------------------------------- |
| `VITE_ARK_SERVER`           | Override the default Arkade server URL                              | `VITE_ARK_SERVER=http://localhost:7070`           |
| `VITE_BOLTZ_URL`            | Override the default Boltz swap provider URL for Lightning          | `VITE_BOLTZ_URL=https://boltz-provider-url.com`   |
| `VITE_PSA_MESSAGE`          | Manage message to show in wallet index page                         | `VITE_PSA_MESSAGE=@arkade_os on TG for support`   |
| `VITE_SENTRY_DSN`           | Enable Sentry error tracking (only in production, not on localhost) | `VITE_SENTRY_DSN=your-sentry-dsn`                 |
| `CI`                        | Set to `true` for Continuous Integration environments               | `CI=true`                                         |
| `GENERATE_SOURCEMAP`        | Disable source map generation during build                          | `GENERATE_SOURCEMAP=false`                        |

## 🔮 Future Plans

- 🟣 RGB protocol integration (R&D)
- 🟣 Custom Nostr client with native Arkade support
- 🟣 Enhanced purple theming
- 🟣 Community-driven features

## 🤝 Contributing

Contributions welcome! This is a research & development fork exploring:
- Nostr + Arkade integration
- RGB protocol on Arkade
- Non-Lightning zap alternatives

## 📄 License

MIT License

## 🙏 Credits

- Original [Arkade Wallet](https://github.com/arkade-os/wallet) by Arkade Labs
- Nostr protocol by Nostr community
- NIP-47 specification
- Testing with [jumble](https://jumble.social)

## 📞 Contact

- GitHub: [@PePeRGB20](https://github.com/PePeRGB20)
- Repository: https://github.com/PePeRGB20/ArkaneWalletNWC

---

**💜 Made for the Nostr ecosystem 💜**

*Purple Arkade Wallet - Bitcoin on Nostr, the way it should be.*
