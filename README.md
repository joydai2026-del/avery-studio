# avery-studio

> An autonomous overnight digital product factory. Agents research, create, and publish while you sleep.

[![Claude](https://img.shields.io/badge/Claude-CC785C?style=flat-square&logo=anthropic&logoColor=white)](https://anthropic.com)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Gumroad](https://img.shields.io/badge/Gumroad-36a9ae?style=flat-square)](https://gumroad.com)
[![Etsy](https://img.shields.io/badge/Etsy-F56400?style=flat-square&logo=etsy&logoColor=white)](https://etsy.com)
[![Notion](https://img.shields.io/badge/Notion-000000?style=flat-square&logo=notion&logoColor=white)](https://notion.so)
[![Status: Live](https://img.shields.io/badge/status-live-brightgreen?style=flat-square)]()

Avery Studio is a multi-agent system that runs an autonomous digital product business. Every night, a team of AI agents researches market gaps, creates Notion templates and prompt packs, writes listings, and publishes across four platforms — with no human in the loop until the morning report lands.

---

## Agent team

```mermaid
graph TD
    JJ["👤 JJ  ·  Board / Owner\nMorning review · Escalation decisions"]

    CEO["🤖 CEO Agent\nStrategic direction\nMarket research · Issue creation\nAgent coordination · Pricing decisions\nPublish approval after QA"]

    DSN["🎨 Designer Agent\nProduct creation\nNotion templates · PDF packs\nCover images · Listing copy\nChinese teaching resources"]

    PUB["📦 Publisher Agent\nCross-platform publishing\nGumroad · Etsy · TPT · Notion"]

    QA["✅ QA Loop\n$29 template checklist\n12-point quality bar\nBlocks publish if fails"]

    BRAIN["🧠 Paperclip API\nBusiness management layer\nIssues · Goals · Agent registry\nCost tracking · Sales data"]

    JJ -->|"escalation only"| CEO
    CEO -->|"product brief"| DSN
    DSN -->|"product ready"| QA
    QA -->|"QA pass"| PUB
    QA -->|"QA fail"| DSN
    CEO <-->|"issues · goals · tasks"| BRAIN
    PUB <-->|"publish + status"| BRAIN
```

---

## Overnight pipeline

Every night from 11PM to 5AM ET, the factory runs autonomously:

```mermaid
gantt
    title Overnight Factory  ·  11PM – 5AM ET
    dateFormat HH:mm
    axisFormat %H:%M

    section Research
    Market scan · gap analysis · competitor pricing  :11:00, 60m

    section Create
    Notion templates (MCP)                           :00:00, 60m
    PDF products · prompt packs · planners           :01:00, 60m
    Visual products · Canva exports                  :02:00, 60m
    Chinese teaching resources                       :03:00, 60m

    section Ship
    Generate listings + QA check                     :04:00, 60m
    Write morning report → queue/nightly-report.md   :05:00, 30m
```

---

## Publisher API

A FastAPI service that abstracts publishing across four marketplaces. Each platform has its own route — Gumroad via REST API, Etsy and TPT via browser automation.

```mermaid
flowchart LR
    AGENT["🤖 CEO Agent\n(publish command)"]

    subgraph api["Publisher API  ·  FastAPI"]
        AUTH["Auth middleware\nBearer token"]
        ROUTER["Route by platform"]
        GM["Gumroad service\nREST API v2"]
        ET["Etsy service\nbrowser automation"]
        TPT["TPT service\nbrowser automation"]
        NM["Notion Marketplace\nMCP"]
    end

    PRODUCT["📁 products/<slug>/\nPRODUCT.md manifest\n+ deliverable files"]

    AGENT --> AUTH --> ROUTER
    ROUTER --> GM
    ROUTER --> ET
    ROUTER --> TPT
    ROUTER --> NM
    PRODUCT -->|"reads manifest"| ROUTER
```

---

## Product quality bar

Nothing ships without passing the **$29 template checklist**. 12 required elements including:

| Requirement | Why |
|---|---|
| Multiple interconnected databases with relations | Demonstrates real Notion expertise |
| Pre-built views: Table + Board + Calendar + Gallery | Immediate usability out of the box |
| Rich sample data that tells a story | Lets buyers evaluate fit before buying |
| Dashboard page with embedded views + metrics | The "wow" moment that justifies the price |
| Step-by-step onboarding guide | Reduces support tickets, increases reviews |
| Custom cover image (brand-matched) | First impression in marketplace search |

The QA loop blocks publishing if any of the 12 checks fail. The Designer agent revises until it passes.

---

## Platform reach

| Platform | Product type | Audience |
|---|---|---|
| Notion Marketplace | Notion templates | Notion power users |
| Gumroad | Templates · prompt packs · planners | Indie creators |
| Etsy | Digital downloads | Small business owners |
| Teachers Pay Teachers | Chinese teaching resources | K-12 educators |

---

## Tech stack

[![Claude](https://img.shields.io/badge/Claude-CC785C?style=flat-square&logo=anthropic&logoColor=white)](https://anthropic.com)
[![Python 3.12](https://img.shields.io/badge/Python_3.12-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Notion MCP](https://img.shields.io/badge/Notion_MCP-000000?style=flat-square&logo=notion&logoColor=white)](https://notion.so)
[![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)](https://playwright.dev)
[![Paperclip API](https://img.shields.io/badge/Paperclip_API-agent--native-blueviolet?style=flat-square)]()

---

Built by [Joy Dong](https://www.joydong.org) · [ownlyagent.com](https://ownlyagent.com)