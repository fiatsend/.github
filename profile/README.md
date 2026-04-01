<img width="1440" height="480" alt="fiatsend-hero-background" src="https://github.com/user-attachments/assets/4400a7b2-a9ad-4528-a09e-f108c4acad4e" />

<h3 align="center">Reliable mobile money payouts with stablecoins</h3>

<p align="center">
  Hold stablecoins and local currency in one account. Pay out instantly with clear confirmations.<br/>
  <strong>17,000+ active users · $6M+ volume processed · 99.9% uptime</strong>
</p>

<p align="center">
  <a href="https://fiatsend.com">Website</a> ·
  <a href="https://app.fiatsend.com">Console</a> ·
  <a href="https://docs.fiatsend.com">API Docs</a> ·
  <a href="https://github.com/fiatsend/litepaper">Litepaper</a>
</p>

---

## What is Fiatsend?

Fiatsend is payment infrastructure for Africa's digital economy. We bridge stablecoins and local mobile money networks so businesses and individuals can send, receive, and settle payments instantly — without losing money to failed transactions or reconciliation gaps.

**How it works:**

1. **Hold digital dollars and local currency** in a single Fiatsend account
2. **Send and receive** using just a phone number — across MTN, Telecel, AirtelTigo, and more
3. **Settle anywhere** — stablecoins convert to local fiat via mobile money in seconds

Every payment is programmable, traceable, and auditable on-chain. No bank required.

## Core Technology

| Component | Description |
|-----------|-------------|
| **MobileNumber NFT** | On-chain identity tied to your phone number. Minted at signup, upgradable through KYC tiers. Your phone number becomes your wallet address. |
| **Programmable Payments** | Smart-contract-powered transfers with full traceability — businesses always know who paid, when, and for what. |
| **Interoperable Settlement** | One account settles to any mobile money network. No more juggling multiple wallets or providers. |
| **Unified Ledger** | Single balance and reporting layer across all payout endpoints, with on-chain settlement and off-chain usability. |

## For Developers

Build programmable, traceable payments with phone-number accounts, payment requests, and on-chain settlement.

```ts
// Create a wallet and pay out to mobile money
const wallet = await fiatsend.wallets.create({
  owner: { phoneNumber: '+233XXXXXXXXX' },
  currency: 'USDC'
});

const payout = await fiatsend.payouts.create({
  walletId: wallet.id,
  destination: {
    type: 'mobile_money',
    phoneNumber: '+233YYYYYYYYY'
  },
  amount: 100,
  currency: 'GHS'
});
// → { status: 'sent', transactionId: '...', channel: 'mobile_money' }
```

**What you can build:**

- **Offramp platforms** — Let users cash out stablecoins to local mobile money
- **Payroll & disbursements** — Pay staff and agents across mobile money networks in one API call
- **Remittance apps** — Send money cross-border with instant local settlement
- **Merchant payments** — Accept payments from any phone number, any network

### SDKs & Libraries

| Package | Description | Status |
|---------|-------------|--------|
| [`@fiatsend/sdk`](https://github.com/fiatsend/fiatsend-js) | JavaScript / TypeScript SDK | 🟢 Available |
| [`fiatsend-python`](https://github.com/fiatsend/fiatsend-python) | Python SDK | 🔜 Coming soon |
| [`fiatsend-go`](https://github.com/fiatsend/fiatsend-go) | Go SDK | 🔜 Coming soon |

> **Get started:** [Read the API docs →](https://docs.fiatsend.com)

## Open Source

We believe in building in the open. Our SDKs, smart contracts, and developer tools are open source so the community can inspect, contribute, and build on top of Fiatsend.

| Repository | Description |
|------------|-------------|
| [`fiatsend-js`](https://github.com/fiatsend/fiatsend-js) | TypeScript/JavaScript SDK for the Fiatsend API |
| [`fiatsend-python`](https://github.com/fiatsend/fiatsend-python) | Python SDK for the Fiatsend API |
| [`fiatsend-go`](https://github.com/fiatsend/fiatsend-go) | Go SDK for the Fiatsend API |
| [`contracts`](https://github.com/fiatsend/contracts) | Smart contracts — MobileNumber NFT, payment settlement, liquidity pools |
| [`openapi`](https://github.com/fiatsend/openapi) | OpenAPI specification for the Fiatsend API |
| [`docs`](https://github.com/fiatsend/docs) | Developer documentation and guides |
| [`litepaper`](https://github.com/fiatsend/litepaper) | Fiatsend Litepaper |
| [`examples`](https://github.com/fiatsend/examples) | Integration examples and starter templates |

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                      Fiatsend Platform                  │
│                                                         │
│  ┌─────────────┐  ┌──────────────┐  ┌───────────────┐  │
│  │  Mobile App  │  │  Web Console │  │   REST API    │  │
│  │ (React Native│  │  (Next.js)   │  │  /api/v1/*    │  │
│  │  + Expo)     │  │              │  │               │  │
│  └──────┬───────┘  └──────┬───────┘  └───────┬───────┘  │
│         │                 │                   │          │
│         └────────────┬────┘───────────────────┘          │
│                      ▼                                   │
│         ┌────────────────────────┐                       │
│         │    Payment Engine      │                       │
│         │  (Orchestration Layer) │                       │
│         └────────────┬───────────┘                       │
│                      │                                   │
│         ┌────────┬───┴───┬──────────┐                    │
│         ▼        ▼       ▼          ▼                    │
│  ┌──────────┐┌───────┐┌──────┐┌──────────┐              │
│  │Blockchain││  KYC  ││ Fiat ││Notification│             │
│  │ (EVM     ││ & AML ││Rails ││  Service  │              │
│  │ Chains)  ││       ││      ││           │              │
│  └────┬─────┘└───────┘└──┬───┘└───────────┘              │
│       │                   │                              │
└───────┼───────────────────┼──────────────────────────────┘
        │                   │
        ▼                   ▼
   ┌─────────┐    ┌──────────────────┐
   │ BSC /   │    │  Mobile Money     │
   │ Polygon │    │  MTN · Telecel    │
   │ Ethereum│    │  AirtelTigo · ... │
   └─────────┘    └──────────────────┘
```

## Use Cases

**For Individuals**
- Send money to family and friends using just a phone number
- Save up to 90% on transfer fees compared to traditional banks
- Hold multiple currencies in one wallet
- Cash out stablecoins to local mobile money — no bank required

**For Businesses**
- Reliable payouts to staff, agents, and suppliers across mobile money networks
- Centralized balances in digital dollars and local currency
- Full payment traceability from request to confirmation
- One API for global coverage with local access

## Security & Compliance

- **Bank-grade encryption** — AES-256 at rest, TLS 1.3+ in transit
- **Tiered KYC** — MobileNumber NFT upgrades through KYC levels (0 → 2)
- **Multi-sig wallets** — Institutional-grade fund protection
- **Regulatory compliance** — Meets international AML/KYC requirements
- **Auditable** — Every financial and identity action immutably logged

## Community & Support

- 📖 [Documentation](https://docs.fiatsend.com)
- 💬 [Community Chat](https://discord.gg/fiatsend)
- 🐦 [Twitter / X](https://x.com/fiaborhot)
- 📧 [support@fiatsend.com](mailto:support@fiatsend.com)
- 🏢 [LinkedIn](https://linkedin.com/company/fiatsend)

## Contributing

We welcome contributions to our open-source repositories. Please see the `CONTRIBUTING.md` in each repo for guidelines.

If you're building on Fiatsend and want to share your project, open an issue in the [`examples`](https://github.com/fiatsend/examples) repo — we'd love to feature it.

---

<p align="center">
  <strong>Built in Accra 🇬🇭 for Africa and the world</strong><br/>
  <sub>© 2026 Fiatsend Network. All rights reserved.</sub>
</p>

