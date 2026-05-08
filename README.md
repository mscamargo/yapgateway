# YAPGateway

A technical case study: building a full-featured payment gateway for the Brazilian market on serverless infrastructure.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## ⚠️ PCI DSS Scope A

This project intentionally handles raw card data and performs in-house tokenization to demonstrate **full PCI DSS Scope A** implementation. In production, this requires compliance audits, network segmentation, encryption standards, and access controls. This is a deliberate technical challenge for this case study.

---

## Why This Project Exists

This is a personal technical portfolio piece. The goal is to design and build a non-trivial system from scratch, demonstrating architectural decisions, trade-offs, and implementation depth across frontend, backend, security, and infrastructure. While working with AI coding agents.

## Goals

- Design a clean abstraction layer over multiple PSPs/acquirers
- Implement PCI DSS Scope A card tokenization in a serverless environment
- Build a functional merchant dashboard and checkout experience
- Handle reconciliation logic across different payment providers
- Demonstrate subscription/billing logic for recurring payments

## Technical Challenges

- **Multi-PSP Adapter Pattern** — Normalizing disparate APIs (Pagar.me, Stripe) into a single domain model
- **Serverless State Management** — Handling payment state machines without long-running processes
- **PCI Compliance in Serverless** — Secure card data handling on ephemeral infrastructure
- **Reconciliation** — Matching async settlement data from multiple sources
- **Brazilian Payment Methods** — PIX and Boleto have unique lifecycle semantics vs credit cards

## Architecture Decisions

- **Serverless-first (Vercel + Next.js)** — Forces stateless design, challenges traditional payment gateway assumptions
- **In-house Tokenization** — Opting into PCI Scope A to demonstrate security architecture, not to avoid PSP dependencies
- **Adapter Pattern for PSPs** — Business logic must never depend on a specific PSP's data model or behavior
- **Initial Adapters** — Pagar.me (Brazilian), Stripe (global baseline for comparison)

## Supported Payment Methods

| Method | Status | Notes |
|--------|--------|-------|
| Credit Card | Planned | In-house tokenization (PCI Scope A) |
| PIX | Planned | Instant payment, QR code + copy-paste |
| Boleto | Planned | Cash-based bank slip with expiration |

## Roadmap

### Phase 1: Foundation
- [ ] Project structure and core abstractions
- [ ] PSP adapter interface definition
- [ ] Database schema (transactions, customers, payment methods)
- [ ] Environment configuration and secrets management

### Phase 2: Core Payment Flow
- [ ] Credit card tokenization endpoint
- [ ] Charge/authorization flow
- [ ] Webhook handling for async state updates
- [ ] Transaction state machine

### Phase 3: Alternative Payment Methods
- [ ] PIX QR code generation and polling
- [ ] Boleto generation and expiration handling
- [ ] Unified payment intent abstraction

### Phase 4: Merchant Experience
- [ ] Dashboard: transaction list and detail view
- [ ] Dashboard: analytics and metrics
- [ ] Checkout page (hosted)
- [ ] Embedded checkout components

### Phase 5: Billing & Reconciliation
- [ ] Subscription plan creation
- [ ] Recurring charge scheduling
- [ ] Reconciliation engine: match settlements to transactions
- [ ] PSP fee tracking and reporting

## Current Status

**v0.1.0 — Foundation Phase**

Project structure being established. No working payment flows yet.

## Quick Start

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## License

[MIT](https://opensource.org/licenses/MIT)
