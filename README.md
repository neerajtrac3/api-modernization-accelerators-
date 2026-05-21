# API Modernization Accelerators

This repository provides reusable API‑led connectivity patterns, integration accelerators, and governance standards used in modernization programs across financial institutions. The assets support the transition from point‑to‑point legacy integrations to structured, scalable, and secure API‑first architectures.

# API Modernization Accelerators

This repository provides reference architectures, patterns, and templates for API-led modernization in banking and financial services.

## Objectives

- Define layered API architecture (Experience, Process, System APIs)
- Provide reusable patterns for legacy-to-modern migration
- Standardize governance (versioning, naming, security)
- Offer OpenAPI-based samples for rapid adoption

## Repository structure

- `architecture/` – Reference architecture and diagrams
- `patterns/` – Modernization and integration patterns
- `governance/` – Policies for API lifecycle and security
- `samples/` – OpenAPI specifications and example APIs
- `use-cases/` – Applied scenarios in banking and lending

## Target audience

- Enterprise and solution architects  
- API platform teams  
- Modernization and integration squads


---

## Architecture Overview

```mermaid
flowchart LR
    subgraph Channels
        Web[Web / Mobile]
        Partner[Partner APIs]
        Ops[Ops Tools]
    end

    subgraph Exp[Experience APIs]
        ExpLend[Exp API - Lending]
        ExpPay[Exp API - Payments]
    end

    subgraph Proc[Process APIs]
        ProcKYC[Process API - KYC]
        ProcOnb[Process API - Onboarding]
        ProcPay[Process API - Payment Orchestration]
    end

    subgraph Sys[System APIs]
        SysCore[System API - Core Banking]
        SysCards[System API - Cards]
        SysAML[System API - AML]
        SysLegacy[System API - Legacy Host]
    end

    subgraph Legacy
        Core[Core System]
        Cards[Cards Platform]
        AML[AML Engine]
        Host[Mainframe / Legacy]
    end

    Web --> ExpLend
    Web --> ExpPay
    Partner --> ExpPay
    Ops --> ExpLend

    ExpLend --> ProcOnb
    ExpLend --> ProcKYC
    ExpPay --> ProcPay

    ProcOnb --> SysCore
    ProcKYC --> SysAML
    ProcPay --> SysCore
    ProcPay --> SysCards
    ProcPay --> SysLegacy

    SysCore --> Core
    SysCards --> Cards
    SysAML --> AML
    SysLegacy --> Host
