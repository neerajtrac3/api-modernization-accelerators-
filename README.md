# API Modernization Accelerators

This repository provides reusable API‑led connectivity patterns, integration accelerators, and governance standards used in modernization programs across financial institutions. The assets support the transition from point‑to‑point legacy integrations to structured, scalable, and secure API‑first architectures.

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
