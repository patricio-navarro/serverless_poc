# 🐶 Dog Finder App — Serverless Codelab

[![Open in Cloud Shell](https://gstatic.com/cloudssh/images/open-btn.svg)](https://shell.cloud.google.com/cloudshell/editor?cloudshell_git_repo=https://github.com/patricio-navarro/serverless_poc.git)

Welcome to the **Building a Production-Ready Serverless App** Codelab repository!

This repository contains the starter code and resources you will need to build and deploy a fully functional serverless application on Google Cloud.

The application allows users to report lost dog sightings, capturing location data, dates, and photos. It leverages multiple Google Cloud services, including Cloud Run, Firestore, Cloud Storage, Pub/Sub, and BigQuery.

## 🚀 Getting Started

Clone this repository and follow the step-by-step instructions in the **[CODELAB.md](CODELAB.md)** guide.

```bash
git clone https://github.com/patricio-navarro/serverless_poc.git
cd serverless_poc
```

## 🏗️ Architecture Overview

```mermaid
flowchart TD
    User([User]) <--> Client["Frontend (Flask/Jinja)"]
    Client -- "OAuth 2.0" --> Auth["Google Identity Services"]
    Client -- "Submit Sighting (POST)" --> Backend["Flask Backend (Cloud Run)"]
    
    subgraph "Google Cloud Platform"
        Backend -- "Store Image" --> GCS["Cloud Storage"]
        Backend -- "Persist Data" --> Firestore[(Firestore)]
        Backend -- "Publish Event" --> PubSub["Pub/Sub"]
        PubSub -- "Subscription" --> BigQuery[(BigQuery)]
    end

    Auth --> Backend
```

## 🛠️ Repository Contents

| Path | Description |
|---|---|
| `app/` | Flask backend, routes, services, and Jinja2 templates |
| `schemas/` | Avro schema for Pub/Sub and JSON schema for BigQuery |
| `scripts/` | Helper scripts: `setup_resources.sh`, `deploy.sh`, `clean_up.sh`, `load_test.sh` |
| `Dockerfile` | Container definition for Cloud Run deployment |
| `requirements.txt` | Python dependencies |
| `.env.example` | Template for your environment configuration |
| `CODELAB.md` | Complete step-by-step codelab tutorial |

---

*Happy Coding!* ☁️
