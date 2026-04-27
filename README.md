# AssetForge

ASSETFORGE: DEVELOPMENT BLUEPRINT & ROADMAP
A Comprehensive SaaS Resource Management Platform for Digital Creators

## 1. PROJECT OVERVIEW
AssetForge is a specialized Single Page Application (SPA) designed to manage the digital lifecycle of creative assets. Unlike generic cloud storage, AssetForge functions as a relational database for media, mapping raw files to licensing agreements, project versions, and AI-generated metadata tags. It is designed to be fully containerized using Docker to ensure environment parity and scalability.

## 2. TECHNICAL ARCHITECTURE (DOCKERIZED)
The project utilizes a multi-container architecture orchestrated via Docker Compose:
- Frontend Container: Angular (Latest) - Component-based UI served via Nginx.
- API Container: Node.js/Express - Handles business logic and cloud communication.
- Database Container: PostgreSQL - Relational storage for asset/license mapping.
- Worker Container: Node.js/Python - Asynchronous processing for AI tagging and metadata extraction.
- Storage: AWS S3 (or compatible) via Signed URLs for secure binary management.

## 3. SCALABILITY CONSIDERATIONS
As asset volume increases, the containerized architecture allows for independent scaling of the Worker and API containers. Use of a CDN for global asset previewing and Row-Level Security in PostgreSQL ensures both speed and data isolation for all users.

---

## 4. DEVELOPER ONBOARDING

### A. Prerequisites & Environment Setup
*   **Tools Required:** Ensure you have the following installed: Docker Desktop, Node.js v20+, Angular CLI, and Python 3.10+.
*   **Environment Variables:** Create an `.env` file at the root of the project. Use the provided `.env.example` as a template and obtain necessary API keys (AWS credentials, JWT secrets, AI service keys) from your team lead.

### B. Local Development & Quickstart Guide
*   **Spinning up the environment:** Run `docker-compose up --build` to start all necessary services locally.
*   **Seeding Data:** Run `npm run seed:db` in the API container to populate your local PostgreSQL database with mock test assets.

### C. Architecture & Data Flow Diagrams
*(Note: Mermaid.js architecture diagrams representing the Docker network topology and asset upload flow will be placed here.)*

### D. Testing & CI/CD Guidelines
*   **Running Tests:** Execute `npm test` within the specific container context (e.g., frontend or API) to run unit and integration tests.
*   **Deployment Flow:** Code is merged via PRs. The CI/CD pipeline handles building Docker images and deploying to staging, with production deployments managed via specific release tags.

### E. Code Conventions & Linting
*   **Internal Standards:** Follow the established Prettier/ESLint configurations for the Angular and Node.js codebases, and PEP8 for any Python worker scripts.
