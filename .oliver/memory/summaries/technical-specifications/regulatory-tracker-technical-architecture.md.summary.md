# Regulatory Tracker - Technical Architecture Documentation

**Source**: repository/technical-specifications/regulatory-tracker-technical-architecture.md
**Type**: Technical Specification
**Upload Date**: 2026-02-09
**Source SHA**: Not provided

## Key Points

- Three-tier cloud-ready architecture with asynchronous background processing for AI-powered regulatory analysis using Next.js 14 frontend, FastAPI backend, and SQLite database
- Seven-stage scan pipeline orchestrator that manages state transitions from initialization through source retrieval, change detection, Claude API analysis, scoring, artifact generation, and finalization
- LLMService integrates with Anthropic Claude API (Sonnet 4 model) using structured prompt engineering to analyze regulatory documents and return JSON-formatted compliance assessments
- ChangeDetectionService identifies material regulatory changes through SHA-256 content hashing, keyword pattern matching, and demo mode for testing
- Comprehensive data flow from scan submission through background task execution, result review workflow, and document export functionality
- Docker Compose deployment with containerized frontend (Node.js) and backend (Python 3.11) services connected via bridge network
- Scalability roadmap includes horizontal scaling with load balancers, migration from SQLite to PostgreSQL, Redis caching, and distributed task queue using Celery

## Entities and Topics

- **Next.js 14**: Frontend framework with App Router for file-based routing, React components, and server-side data fetching
- **FastAPI**: Modern Python web framework providing RESTful API endpoints for scans, results, workflow management, and knowledge store
- **ScanOrchestrator**: Core service managing the 7-stage pipeline with error handling, retry logic, and real-time status updates
- **Claude API (Sonnet 4)**: External AI service performing regulatory document analysis with configurable token limits and prompt engineering
- **SQLite Database**: File-based relational database storing scans, results, sources, and maintaining workflow status states
- **ArtifactGenerator**: Service creating professional markdown and Word document (.docx) outputs from analysis results
- **ChangeDetectionService**: Detects material changes via content hashing, keyword detection, and supports demo mode
- **Mock Sources Directory**: JSON files simulating regulatory agency data (FinCEN, OCC, Federal Reserve) for development and testing
- **Docker Compose**: Orchestrates containerized deployment with volume management for data persistence
- **Monitoring Stack**: Prometheus, Grafana, Sentry, and ELK for comprehensive observability and alerting

## Relevance to Project

This technical specification document provides the complete architectural blueprint for the Regulatory Tracker system, essential for understanding how all technical components integrate to deliver AI-powered regulatory analysis and compliance workflow management. It directly supports project implementation by detailing API contracts, data schemas, service responsibilities, deployment procedures, and scalability considerations needed for development and production deployment.