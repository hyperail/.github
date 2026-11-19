# Welcome to Hyperail 👋

> **Next-Generation Multi-Chain Web3 Wallet & Autonomous Agent Financial Infrastructure**  
> Non-Custodial • MPC-Powered • Multi-Platform • AI Agent Native

---

## 🌟 About Hyperail

**Hyperail** is an enterprise-grade multi-chain Web3 wallet and autonomous AI financial infrastructure suite. Designed from the ground up for seamless asset management, high security, and programmatic on-chain operations, Hyperail bridges the gap between everyday crypto users and autonomous AI agents.

From consumer-facing web, mobile, and browser extension interfaces to native whitebox cryptographic engines and Model Context Protocol (MCP) servers, Hyperail delivers a unified, zero-compromise non-custodial experience.

---

## 🏗️ System Architecture

```mermaid
flowchart TD
    subgraph Clients ["Client & Interface Layer"]
        WEB["hyperail-wallet-frontend<br/>Web & Telegram Mini App"]
        EXT["hyperail-chrome-extension<br/>Chromium Extension (MV3)"]
        AOS["hyperail-mfe-aos<br/>Android Native App"]
        IOS["hyperail-mfe-ios<br/>iOS Native App"]
        AGENT["hyperail-agentic-wallet<br/>AI Agent CLI & MCP"]
    end

    subgraph Security_SDK ["Security, Cryptography & SDKs"]
        KIT1["hyperail-kit<br/>TalkenKit v1 Web3 UI & Connectors"]
        KIT2["hyperail-kit-v2<br/>V3 Auth, Session SDK & Grant Issuer"]
        TS_AOS["hyperail-ts-aos<br/>Android TrustSigner AAR"]
        TS_IOS["hyperail-ts-ios<br/>iOS TrustSigner XCFramework"]
    end

    subgraph Backend_MPC ["Backend & Infrastructure"]
        BE["hyperail-wallet-backend<br/>BFF, Read Gateway & Business API"]
        API["hyperail-api<br/>Multi-Chain, Read-Only & Relayer API"]
        DEVOPS["hyperail-devops<br/>NGINX Proxy & Docker Compose Stack"]
        WAAS["ABC WaaS MPC Engine<br/>Distributed Key Shares"]
    end

    WEB -->|Web3 UI & Connectors| KIT1
    WEB -->|Client Auth| KIT2
    WEB -->|BFF, PIN & Read Gateway| BE
    WEB -->|Multi-Chain Routes| API
    EXT -->|WaaS Direct| WAAS
    AOS -->|JNI Binding| TS_AOS
    AOS -->|Wallet API| BE
    IOS -->|Native Framework| TS_IOS
    IOS -->|Wallet API| BE
    AGENT -->|MCP Tools / RPC| WAAS
    AGENT -->|Execution & Quote| API
    BE -->|V3 Grants, PIN & Custody| KIT2
    BE -->|Read Lane & Key Sync| API
    BE -->|Key Share / Sync| WAAS
    KIT2 -->|Canonical /me & Auth| API
    DEVOPS -.->|Reverse Proxy & Isolation| BE
    DEVOPS -.->|Reverse Proxy & Isolation| API
    DEVOPS -.->|Reverse Proxy & Ingress| WEB
```

---

## 📦 Core Ecosystem Repositories

| Repository | Role & Layer | Primary Tech Stack |
|---|---|---|
| [**`hyperail-wallet-frontend`**](https://github.com/hyperail/hyperail-wallet-frontend) | Responsive Web Wallet (Ti-style Sign-In, HPKE PIN Custody, EVM & Solana) & Telegram Mini App | Next.js (Pages), React 18, Tailwind, TypeScript |
| [**`hyperail-chrome-extension`**](https://github.com/hyperail/hyperail-chrome-extension) | Standalone Chrome Extension Wallet | Vite 6, React 18, TypeScript, Manifest V3 |
| [**`hyperail-wallet-backend`**](https://github.com/hyperail/hyperail-wallet-backend) | Wallet API, Indexing, Read Gateway (`/api/read/v1`) & PIN-Relay BFF | Express, TypeScript, TypeORM, PostgreSQL, Redis |
| [**`hyperail-api`**](https://github.com/hyperail/hyperail-api) | Multi-Chain Swap, Relayer, Read-Only Lane & Canonical `/me` API | NestJS 10.4, TypeScript 5, Prisma 7, PostgreSQL, Redis |
| [**`hyperail-agentic-wallet`**](https://github.com/hyperail/hyperail-agentic-wallet) | Autonomous AI Agent CLI & MCP Server | TypeScript, tsup, viem v2, Commander, MCP SDK |
| [**`hyperail-kit`**](https://github.com/hyperail/hyperail-kit) | TalkenKit v1 Web3 UI, Multi-Wallet Connectors & Provider SDK | TypeScript, React, pnpm monorepo, Vitest |
| [**`hyperail-kit-v2`**](https://github.com/hyperail/hyperail-kit-v2) | Headless V3 Auth, Zero-Storage Session SDK & PIN-Enforced Grant Issuer | TypeScript, React, Vite, Playwright |
| [**`hyperail-mfe-aos`**](https://github.com/hyperail/hyperail-mfe-aos) | Native Android Mobile Wallet App | Kotlin/Java, Gradle 8.9, AGP 8.6.1, Hilt, Realm |
| [**`hyperail-mfe-ios`**](https://github.com/hyperail/hyperail-mfe-ios) | Native iOS Mobile Wallet App | Swift 5.0, Xcode workspace, CocoaPods |
| [**`hyperail-ts-aos`**](https://github.com/hyperail/hyperail-ts-aos) | Android Native Cryptographic Module (AAR) | C++17, JNI, NTL 9.6.2, Boost 1.68, CMake, NDK 28 |
| [**`hyperail-ts-ios`**](https://github.com/hyperail/hyperail-ts-ios) | iOS Native Cryptographic Framework (XCFramework) | C++17, Swift, NTL 9.6.2, Boost 1.69, Clang++ |
| [**`hyperail-devops`**](https://github.com/hyperail/hyperail-devops) | Deployment Orchestration, Image Pinning & NGINX Proxy | Docker Compose v2, NGINX, PostgreSQL 17, Redis |

---

## ⚡ Key Capabilities

### 🌐 Multi-Chain Ecosystem
- **EVM Networks**: Ethereum, Arbitrum, Polygon, BSC, Kaia, and custom EVM chain integration.
- **Non-EVM Networks**: Bitcoin (SegWit/Taproot), Solana (SOL & SPL transfers), Tron, and Hyperliquid.
- **Cross-Chain Interoperability**: Seamless asset transfers powered by Circle CCTP, LayerZero, and Wormhole (with Rhino bridge routes disabled by default).

### 🔐 Enterprise-Grade Non-Custodial Security
- **MPC Architecture**: Multi-Party Computation eliminates single points of failure. Users never expose raw seed phrases.
- **Hardware & Whitebox Cryptography**: Native TrustSigner engines on Android (AAR) and iOS (XCFramework) enforce BIP-32/BIP-39 HD key derivation and fail-closed cryptographic entropy.
- **Dual SDK Strategy**:
  - `hyperail-kit`: TalkenKit v1 기반 멀티체인 Web3 UI, 모달 및 지갑 커넥터 SDK (`@talken/talkenkit`).
  - `hyperail-kit-v2`: Same-origin BFF HTTP-only 쿠키 기반 제로 스토리지 세션 및 V3 Custody Grant Issuer. 브라우저에서 해싱된 PIN을 고정된 Issuer 공개키로 암호화(HPKE)하여 BFF 감사 로깅과 함께 릴레이하며, V3 Issuer에서 리스(lease) 기반 요청 포워딩, 정지 스위치, 서명/갱신 캡, v2→v3 키 갱신 및 표준 `/me` 라우트를 강제합니다.
- **Read-Only Gateway Isolation**: BFF 계층에서 `/api/read/v1` 게이트웨이를 노출하고, 서명 권한이 완전히 배제된 읽기 전용 `hyperail-api` 인스턴스로 격리 라우팅하여 조회 트래픽을 안전하게 분리.
- **Supply-Chain & Runtime Guards**:
  - 프론트엔드 내 취약 종속성(`picomatch` 계열 CVE)을 격리된 사설 어댑터(`@talken/anymatch-minimatch`)로 대체하여 무결성 보장.
  - 모바일(AOS/iOS) 네이티브 런타임에 심볼릭 링크 악용 차단 가드 도입 및 OAuth 클라이언트 시크릿 마스킹 적용.
  - NGINX 리버스 프록시 및 프론트엔드 헤더에 strict CSP, `frame-ancestors 'none'`, `X-Robots-Tag: noindex`, `nosniff`, 외부 폰트 요청 차단 적용.
  - 백엔드 서비스의 최소 권한(Least-privilege) DB 시작 정책 및 멱등성 보장.

### 🤖 Autonomous AI Agent Infrastructure
- **Agentic Wallet & MCP Server**: Direct integration with AI agent workflows via the Model Context Protocol (MCP).
- **Automated Trading & Staking**: Programmatic trading on Hyperliquid (perps/spot), Polymarket prediction markets, and Arcus orderbooks.
- **Gasless Transactions**: Native support for EIP-7702 account abstraction and gasless relayers.

### 🔄 Integrated DeFi & Gamification
- **DEX Aggregation**: Multi-route swaps powered by 1inch (EVM) and Jupiter (Solana).
- **Liquid Staking**: Built-in staking workflows for Lido (stETH/wstETH), KAIA (Kommune), and StakeWeight.
- **Gamified Rewards & Quests**: Faucet, daily roulette, prediction challenges, and leaderboard point systems.

---

## 🔒 Security & Code Quality Standards

Every repository in the Hyperail organization adheres to strict engineering guidelines:
- **Zero Critical/High Vulnerabilities**: Clean dependency audits across NPM, Maven, and CocoaPods graphs (verified against production build locks).
- **Sanitized Git History**: Permanent elimination of hardcoded credentials, test seeds, and sensitive RPC keys across all branches and history.
- **Strict Testing Gates**: Comprehensive unit, integration, offline, and containerized isolated E2E suites across all layers.
- **Disaster Recovery & Reconciliation**: Automated encrypted backup, OCI blob integrity verification, and state reconciliation runbooks.

---

## 📬 Contact & Community

- **GitHub**: [github.com/hyperail](https://github.com/hyperail)
- **Organization**: Hyperail Team
- **License**: Proprietary / MIT (per component license declarations)
