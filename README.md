# FactoryLink
### Global B2B Manufacturing Marketplace

**Discover Manufacturers. Build Partnerships.**

FactoryLink is a portfolio software engineering project that aims to connect manufacturers and factories with business buyers through a centralized B2B marketplace.

The platform is designed to help manufacturers showcase their products and production capabilities while allowing buyers to discover suppliers, submit Requests for Quotation (RFQs), and manage quotation discussions.

> **Project Status:** Planning and system design

---

## 1. Project Overview

Traditional product marketplaces primarily focus on ready-made products. However, manufacturing businesses often require more than a standard product listing.

Buyers may need to identify factories with specific production capabilities, request custom manufacturing, provide technical specifications, and compare quotations.

FactoryLink aims to address these requirements through two main sourcing workflows:

- **Ready-made Product Sourcing** — Discover products published by manufacturers.
- **Custom Manufacturing Sourcing** — Submit specifications and request quotations from suitable manufacturers.

## 2. Project Objectives

- Connect manufacturers with potential business buyers.
- Provide manufacturers with a platform to showcase their products and production capabilities.
- Enable buyers to discover and evaluate manufacturers.
- Support structured RFQ and quotation workflows.
- Provide manufacturer application review and administrative moderation.
- Develop web and mobile applications using a shared backend API.
- Explore AI and Web3 capabilities through future development phases.

## 3. Target Users

| User | Description |
|---|---|
| Guest | Browse public manufacturers and products. |
| Buyer | Discover manufacturers, submit RFQs and review quotations. |
| Manufacturer | Manage company profiles, product listings and quotation requests. |
| Administrator | Review manufacturer applications and manage platform content. |

## 4. Core Features

### Initial MVP

- User registration and authentication
- Business profile management
- Manufacturer application and approval
- Product catalogue management
- Manufacturing capability profiles
- Product search and filtering
- Manufacturer discovery
- Request for Quotation (RFQ)
- Quotation management
- Basic notifications
- Administrative dashboard
- Role-based access control

### Planned Enhancements

- Mobile application
- Purchase order and order tracking
- AI-assisted manufacturer discovery
- AI-assisted document and specification extraction
- Blockchain-based document integrity verification
- Docker-based deployment and CI/CD

## 5. Proposed Technology Stack

| Component | Technology |
|---|---|
| Web Frontend | Next.js, TypeScript |
| Mobile Application | React Native, Expo |
| Backend API | Laravel |
| Database | PostgreSQL |
| Cache / Queue | Redis |
| UI Styling | Tailwind CSS |
| API Testing | Postman |
| AI Service | Python, FastAPI |
| Smart Contracts | Solidity, Foundry |
| Containerization | Docker |
| Version Control | Git, GitHub |

Technology choices and versions may be refined during implementation.

## 6. System Architecture

FactoryLink is planned as a modular monolithic backend architecture.

The web and mobile applications will communicate with a shared Laravel REST API, which manages business rules, authentication, authorization and database operations.

AI and blockchain integrations will be introduced as optional capabilities in later phases.

## 7. Development Roadmap

| Phase | Description | Status |
|---|---|---|
| 1 | Requirements Analysis and System Design | In Progress |
| 2 | Core B2B Marketplace Development | Planned |
| 3 | Mobile Application Development | Planned |
| 4 | Order Management and Operations | Planned |
| 5 | AI Integration | Planned |
| 6 | Web3 Integration | Planned |
| 7 | Deployment, Testing and Optimization | Planned |

## 8. Repository Structure

```text
factorylink/
├── README.md
├── LICENSE
├── docs/
│   ├── requirements/
│   ├── architecture/
│   ├── diagrams/
│   ├── api/
│   ├── testing/
│   └── deployment/
├── apps/
│   ├── web/
│   └── mobile/
├── backend/
│   └── laravel-api/
├── services/
│   └── ai-service/
└── infrastructure/
    ├── docker/
    └── deployment/
```

Directories will be introduced as their corresponding development phases begin.

## 9. Documentation

Project documentation will be maintained in the `docs/` directory.

- Software Requirements Specification (SRS)
- System Architecture
- Database Design and Entity Relationship Diagram
- User Workflows and Use Cases
- API Documentation
- Testing Documentation
- Deployment Guide

## 10. Project Purpose

FactoryLink is developed as a personal software engineering portfolio project to demonstrate the ability to:

- Analyze business requirements and translate them into software solutions.
- Design relational databases and system architecture.
- Develop RESTful APIs and full-stack applications.
- Implement business workflows and access control.
- Build web and mobile applications.
- Apply software testing and deployment practices.
- Explore emerging technologies through practical implementation.

## 11. Current Limitations

FactoryLink is currently a development and demonstration project.

It does not currently provide real commercial transactions, payment processing, shipping integration, legally verified manufacturer certifications or production-grade trade compliance services.

All demonstration data should be synthetic.

---

**FactoryLink — Discover Manufacturers. Build Partnerships.**
