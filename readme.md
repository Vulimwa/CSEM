# Climate Smart Equity Mapper (CSEM)

Mapping Fairness in Climate Resilience

Version: 1.0  
Date: November 2025

---

## Table of Contents
- Overview
- Problem Context
- Problem Statement
- Goal
- Core Objectives
- Target Users
- Key Features
- Data Sources
- System Architecture
- Tech Stack
- Key Metrics (KPIs)
- Expected Impact
- Competitive Advantage
- Sustainability & Scalability
- Risks & Mitigation
- Roadmap
- Team & Collaboration
- Potential Partners
- Future Enhancements
- Getting Started (Development)
- Data Governance & Privacy
- Contributing
- Glossary
- Contact

---

## Overview
Climate Smart Equity Mapper (CSEM) is an integrated, open-access platform that maps climate risk alongside social vulnerability and health resilience to inform equitable climate-action decisions in Kenya. CSEM combines satellite data, institutional datasets, and community reports to highlight where risks are highest, resources are scarcest, and early-warning systems are not reaching people.

---

## Problem Context
Kenya faces compounding climate crises that disproportionately affect vulnerable populations. Between September and November 2025, data from KMD, ICPAC, and NDMA show:

- Erratic rainfall and prolonged droughts in arid and semi-arid lands (Turkana, Marsabit, Garissa, Kajiado).
- Flash floods in Kisumu, Baringo, Tana River, and coastal counties.
- Rising temperatures and climate-linked diseases (malaria, cholera, heat stress).
- Gaps in early-warning systems — alerts often fail to reach rural and low-income communities.

These risks are unevenly distributed, revealing an equity gap: some communities receive aid and information on time; others remain invisible in national data.

---

## Problem Statement
Kenya’s climate risks — droughts, floods, and heat extremes — are not equally experienced or addressed. Vulnerable groups (rural women, youth, pastoralists, informal-settlement residents) face the highest exposure yet have the least access to climate-resilience information, health services, and infrastructure. Lack of integrated, equity-based climate data hinders early warning, preparedness, and fair allocation of adaptation resources.

---

## Goal
Create an integrated digital platform that collects, maps, and visualizes climate-risk, social-vulnerability, and health data to guide equitable climate-action decisions at national and county levels.

---

## Core Objectives
| # | Objective | Description |
|---|-----------|-------------|
| 1 | Map climate-risk exposure | Integrate remote-sensing data (rainfall, flood risk, NDVI, heat anomalies) with socio-economic layers. |
| 2 | Identify equity gaps | Highlight counties/wards with low resilience resources (water points, clinics, alerts). |
| 3 | Strengthen early-warning access | Show areas unserved by existing EW systems; support localization of alert channels. |
| 4 | Integrate climate–health indicators | Overlay disease surveillance, water quality, and temperature trends to anticipate health stress zones. |
| 5 | Empower community data collection | Build a simple mobile-first web reporting tool for local data input by chiefs, youth volunteers, and CHVs. |

---

## Target Users
| User Segment | Role / Use Case |
|--------------|------------------|
| County Planners & NDMA officers | View climate-risk maps to prioritize interventions and budgets. |
| Health Departments (MoH, KEMRI) | Correlate climate data with outbreaks and plan adaptive measures. |
| NGOs & Donors | Identify data-poor or underserved communities for targeted funding. |
| Community Reporters / Chiefs / Youth groups | Upload local incidents, validate data, and visualize their area’s risk profile. |
| Researchers & Universities | Analyze climate-equity correlations using open data. |

---

## Key Features
| Category | Feature | Description |
|---------|---------|-------------|
| A. Climate Data Engine | Multi-layer map | Rainfall anomalies, flood plains, drought indices, and temperature trends using open APIs (CHIRPS, Copernicus, KMD feeds). |
| B. Equity Index Layer | Equity/vulnerability scoring | Combines socio-economic, demographic, and infrastructure data to score vulnerability per ward. |
| C. Health Resilience Dashboard | Climate–health overlays | Displays climate-sensitive diseases, facility capacity, and water-sanitation gaps. |
| D. Early-Warning Coverage Map | Alert reach visualization | Visualizes network reach (e.g., broadcast/SMS coverage where data is available). |
| E. Community Reporter App | Lightweight reporting | Mobile-first web/PWA tool for ground-truth reports (crop loss, flooding, heat illness). |
| F. Analytics & Insights Panel | Equity scores & reports | Generates equity scores, summary charts, and PDF briefs for decision-makers. |
| G. Open-Data API | Public endpoints | Enables third-party integration and academic use. |

---

## Data Sources
| Type | Source | Example |
|------|--------|---------|
| Climate & Environment | Kenya Meteorological Department (KMD), CHIRPS rainfall, MODIS NDVI, Sentinel-2, Copernicus ERA5 | Rainfall anomalies, drought indices |
| Social & Economic | KNBS, WorldPop, OpenStreetMap, DHS | Poverty, population density, infrastructure |
| Health | MoH DHIS2, KEMRI, WHO Climate–Health datasets | Malaria, cholera, heat stress |
| Community | Web/PWA field submissions | Localized impact & hazard data |

---

## System Architecture
High-level components and data flow (MERN stack):

- Frontend: Web-based interactive dashboard (React + Vite + MapLibre GL). Mobile-first responsive design. PWA support for offline resilience.
- Backend: Node.js (Express, CommonJS) REST API; MongoDB (Atlas or local) with geospatial indexes (`2dsphere`) for spatial queries.
- Data Pipeline: Node-based jobs (e.g., `node-cron` or queue workers) to fetch → preprocess → store (daily/weekly); compute vulnerability and equity indices; update dashboard and generate summaries.
- Community Interface: Mobile-first web/PWA reporter for ground-truth submissions (no USSD).

Suggested monorepo layout:
```
csem/
  apps/
    web/                # React + Vite + MapLibre GL dashboard
    api/                # Node/Express (CommonJS) REST API (MongoDB)
    worker/             # Node jobs for data ingestion/processing
  packages/
    ui/                 # Shared UI components
    utils/              # Cross-app utilities
    models/             # Mongoose models, validation, indexes
  infra/
    workflows/          # CI workflows (GitHub Actions)
  docs/
    design/             # Architecture diagrams, data dictionary
  .env.example          # Environment variables template
  README.md             # This file
```

---

## Tech Stack
- Mapping: MapLibre GL, Turf.js; optional vector tiles if needed
- Frontend: React, Vite, JavaScript, PWA,Tailwind
- Backend: Node.js (Express, CommonJS), MongoDB (Mongoose)
- Data jobs: Node scripts with `node-cron` or a queue 
- Auth & RBAC: JWT-based auth; role checks in Express middleware
- CI/CD: GitHub Actions (no Docker)

---

## Key Metrics (KPIs)
| Metric | Description |
|--------|-------------|
| Coverage | Number of counties/wards mapped with active data layers. |
| Equity Index Accuracy | Correlation between predicted vulnerability and verified ground truth. |
| Community Participation Rate | Percentage of local users submitting incident data. |
| Response Time | Time from hazard report to dashboard update. |
| Adoption | Number of institutional partners actively using CSEM. |

---

## Expected Impact
| Domain | Short-Term (6 months) | Long-Term (2 years) |
|--------|------------------------|----------------------|
| Planning | County officers access disaggregated maps for drought/flood risk. | Equitable resource allocation and adaptation funding. |
| Preparedness | Communities receive tailored alerts based on location. | Reduced losses and faster disaster response. |
| Health | Health agencies visualize hotspots of disease vulnerability. | Climate-resilient health-system planning. |
| Data Culture | Integrates government, citizen, and satellite data. | Institutional adoption of data-driven decision-making. |

---

## Competitive Advantage
- Equity Lens: Goes beyond risk to highlight fairness and inclusion.
- Hybrid Data Model: Merges satellite, institutional, and community inputs.
- Offline-Friendly: PWA for low-connectivity areas (no USSD requirement).
- Open-Access Dashboard: Democratizes resilience data for citizens and counties.

---

## Sustainability & Scalability
| Phase | Strategy |
|-------|----------|
| Pilot (Year 1) | Test in 3 counties (Kajiado, Tana River, Kisumu)- diverse hazards. |
| Scale (Year 2) | Expand to all 47 counties; integrate with NDMA and MoH systems. |
| Sustain (Year 3+) | Offer analytics API to NGOs/donors; subscription for insights while keeping public data open. |

---

## Risks & Mitigation
| Risk | Mitigation |
|------|-----------|
| Data inconsistencies | Cross-verify with multiple open datasets. |
| Limited digital literacy | Simplified interfaces; multilingual UI and training. |
| Low institutional adoption | Co-design with county planning offices from the start. |
| Privacy of health data | Anonymize sensitive layers; follow Kenya Data Protection Act. |

---

## Roadmap
| Phase | Timeline | Deliverables |
|-------|----------|-------------|
| Phase 1: Prototype | Nov 2025 – Feb 2026 | MVP dashboard + 3 data layers + web reporting form |
| Phase 2: Pilot Deployment | Mar – Aug 2026 | County-level roll-out + stakeholder training |
| Phase 3: National Scale-Up | Sep 2026 – 2027 | Integration with NDMA, MoH, KMD; full Kenya coverage |
| Phase 4: Regional Replication | 2028 + | Export model to other East-African countries |

---

## Team & Collaboration
| Role | Key Responsibility |
|------|--------------------|
| Project Lead (Urban/Regional Planner) | Oversees design, coordination, and stakeholder partnerships. |
| Data Scientist | Builds vulnerability models and analytics pipelines. |
| GIS Developer | Develops map interface and spatial queries. |
| Backend Engineer | Handles APIs, databases, and automation. |
| Community Lead | Manages data-collection networks & training. |
| Health Liaison | Ensures health-data integration. |

---

## Potential Partners
- Government: KMD, NDMA, MoH, NEMA, KNBS
- Research: KEMRI, RCMRD, universities
- Private/Tech: Safaricom, Esri EA
- Development: UNDP, FAO, WWF, Red Cross Climate Centre

---

## Future Enhancements
- AI-based forecast visualization (predictive risk layers)
- Carbon-credit overlay to link adaptation with climate finance
- Voice-based accessibility for visually impaired and elderly
- Machine-learning classifier for text-to-map incident categorization

---

## Getting Started (Development)
Proposed initial setup for a MERN monorepo. Adjust as the implementation evolves.

1) Prerequisites
- Node.js 20+, npm or pnpm
- MongoDB 6+ (local) or MongoDB Atlas

2) Clone and bootstrap (placeholder)
```
git clone <repo-url> csem
cd csem
# Initialize workspaces once apps are scaffolded
```

3) Environment variables
Copy `.env.example` to `.env` in each app and set:
- Database: `MONGO_URI`
- Auth: `JWT_SECRET`
- Maps: `MAPTILER_KEY` or self-hosted tiles URL
- Ingestion keys: API keys or credentials for CHIRPS/Copernicus/KMD feeds as applicable

4) Suggested scripts (to be added when scaffolded)
```
# apps/web
npm run dev           # Start the React dashboard

# apps/api
npm run dev           # Start Node/Express API (CommonJS)

# apps/worker
npm run start         # Run scheduled/queued data jobs
```

5) Database & Geospatial
- Use MongoDB with `2dsphere` indexes for spatial queries.
- Define Mongoose models and indexes under `packages/models`.
- Seed reference layers (admin boundaries, water points, facilities) via scripts.

---

## Data Governance & Privacy
- Use anonymized or aggregated health data; suppress small counts in public views.
- Enforce role-based access in Express; validate inputs with Mongoose schemas.
- Comply with Kenya Data Protection Act and relevant GDPR principles.
- Provide consent and data-use notices in web/PWA flows.

---

## Contributing
- Propose changes via pull requests with a clear problem statement and screenshots where relevant.
- For data layers, include source metadata, license, spatial reference, and preprocessing steps.
- Follow repository coding standards and use meaningful commit messages.

---

## Glossary
- ASAL: Arid and Semi-Arid Lands
- CHIRPS: Climate Hazards Group InfraRed Precipitation with Station data
- NDVI: Normalized Difference Vegetation Index
- JWT: JSON Web Token

---

## Contact
- Project: Climate Smart Equity Mapper (CSEM)
- Inquiries:vulimwabravin@gmail.com

