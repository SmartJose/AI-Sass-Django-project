# 🚀 PolicyFlow - AI-Powered Tax Compliance Assistant



## :warning: Security & Open Source Notice

**This repository is safe for public viewing. All credentials, API keys, and secrets have been removed.**

- Do NOT commit your real credentials, secrets, or .env files to version control.
- Use the provided `.env.example` and `credentials.json.example` to create your own configuration files.
- See the [Setup](#getting-started) section for instructions on configuring your environment.
---

<div align="center">

**An intelligent AI assistant that helps businesses navigate complex tax regulations with confidence.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Django](https://img.shields.io/badge/Django-5.0+-green.svg)](https://www.djangoproject.com/)
[![React](https://img.shields.io/badge/React-18.0+-blue.svg)](https://reactjs.org/)
[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue.svg)](https://www.typescriptlang.org/)

[Features](#features) • [Quick Start](#quick-start) • [Documentation](#documentation) • [Contributing](#contributing)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

PolicyFlow is a modern AI-powered tax compliance assistant designed to help businesses, tax professionals, and individuals navigate the complex world of tax regulations. Using advanced natural language processing and Google's Vertex AI, PolicyFlow provides intelligent answers to tax queries, analyzes compliance documents, and automatically monitors regulatory changes.

### Why PolicyFlow?

- 🤖 **AI-Powered Intelligence**: Leverages Google's Gemini 2.0 and Vertex AI for accurate, context-aware responses
- 📚 **Knowledge Base**: Built on a comprehensive database of tax acts, circulars, and notifications
- 🔍 **Smart Document Analysis**: Automatically extracts and analyzes compliance requirements from uploaded documents
- 🔔 **Proactive Monitoring**: Tracks regulatory changes and sends intelligent notifications
- 💼 **Professional Grade**: Designed for tax consultants, CFOs, and compliance teams
- 🌐 **User-Friendly Interface**: Modern React frontend with real-time chat and document upload

---

## ✨ Key Features

### 1. 🗨️ Intelligent Chat Interface
- Natural language query processing for tax and compliance questions
- Multi-turn conversations with context awareness
- Citation-backed responses with source references
- Suggested follow-up questions

### 2. 📄 Document Processing
- Upload invoices, circulars, and compliance documents
- Automatic OCR and text extraction using Google Document AI
- Compliance validation and risk flagging
- Document-specific chat for detailed analysis

### 3. 🤖 Autonomous Compliance Agent
- Monitors Google Drive for new regulatory documents
- Automatic impact assessment (HIGH/MEDIUM/LOW)
- Generates draft client communications
- Creates actionable compliance checklists

### 4. 🔔 Smart Notifications
- Real-time alerts for regulatory changes
- Impact level categorization
- Auto-generated action items
- Integration with document repository

### 5. 👤 User Management
- Google OAuth authentication
- Personalized user profiles
- Chat history and document management

### 6. 🔍 Vector-Based Search
- Semantic search powered by pgvector
- Retrieval-Augmented Generation (RAG) for accurate responses
- Embeddings using Vertex AI
- Fast and efficient knowledge retrieval

---

## 🛠️ Technology Stack

### Backend
- **Framework**: Django 5.0+ with Django REST Framework
- **Database**: PostgreSQL with pgvector extension (Supabase)
- **AI/ML**: 
  - Google Vertex AI (Gemini 2.0 Flash)
  - Google Document AI for OCR
  - LangChain for document processing
- **Authentication**: Google OAuth 2.0, JWT tokens
- **Storage**: Google Cloud Storage

### Frontend
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite
- **UI Library**: shadcn/ui + Tailwind CSS
- **State Management**: React Context API
- **HTTP Client**: Fetch API
- **Routing**: React Router

### Infrastructure
- **Containerization**: Docker
- **Cloud Platform**: Google Cloud Platform (GCP)
- **Database**: Supabase (PostgreSQL)
- **File Storage**: Google Cloud Storage

---

## 🏗️ Architecture

```
┌─────────────────┐
│  React Frontend │
│   (Vite + TS)   │
└────────┬────────┘
         │ REST API
         ▼
┌─────────────────┐
│  Django Backend │
│   + REST API    │
└────────┬────────┘
         │
    ┌────┴────┬──────────┬──────────┐
    ▼         ▼          ▼          ▼
┌────────┐ ┌──────┐ ┌────────┐ ┌─────────┐
│Postgres│ │ GCS  │ │Vertex  │ │Doc AI   │
│pgvector│ │Files │ │  AI    │ │  OCR    │
└────────┘ └──────┘ └────────┘ └─────────┘
```

### Data Flow

1. **User Query** → Frontend → Django REST API
2. **RAG Pipeline**: 
   - Query → Vertex AI Embeddings
   - Search → pgvector semantic search
   - Retrieved docs → Context for LLM
   - Gemini 2.0 → Generate response
3. **Document Upload**:
   - File → GCS Storage
   - OCR → Document AI
   - Text → Chunking → Embeddings → pgvector
4. **Autonomous Agent**:
   - Google Drive Monitor → New documents
   - Document AI → Extract text
   - Vertex AI → Impact analysis
   - Notification → User dashboard

---

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following:

- **Python 3.10+** ([Download](https://www.python.org/downloads/))
- **Node.js 18+** and npm ([Download](https://nodejs.org/))
- **PostgreSQL 14+** or Supabase account ([Sign up](https://supabase.com/))
- **Google Cloud Account** with:
  - Vertex AI API enabled
  - Document AI API enabled
  - Cloud Storage bucket created
  - Service account credentials
- **Git** ([Download](https://git-scm.com/downloads))

### Quick Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/sdeevanapalli/PolicyFlow-public.git
cd PolicyFlow
```

#### 2. Backend Setup

```bash
# Create and activate virtual environment
python -m venv .venv

# Activate:
# Windows: .venv\Scripts\activate
# Mac/Linux: source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Copy environment template
cp .env.example .env
# Edit .env with your credentials

# Run migrations
python manage.py migrate

# Start backend
python manage.py runserver
```

#### 3. Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Copy environment template
cp .env.example .env
# Edit .env with your credentials

# Start development server
npm run dev
```

### Detailed Setup Guide

For detailed setup instructions including Google Cloud configuration, database setup, and deployment, please see:
- [Deployment & Security Guide](docs/DEPLOYMENT_SECURITY.md) - Complete production setup
- [Setup Guide](SETUP.md) - Step-by-step local development setup
- [Open Source Guide](docs/OPEN_SOURCE_GUIDE.md) - Best practices for open source use

---

## 📖 Usage

### Basic Workflow

1. **Sign Up/Login**: Click "Sign in with Google"
2. **Ask Questions**: Navigate to Chat page and ask tax compliance questions
3. **Upload Documents**: Go to Upload page to analyze invoices and compliance docs
4. **Monitor Notifications**: Check notification bell for regulatory updates

### Example Queries

```
"What are the GST implications for intermediary services?"
"Am I required to charge GST on consulting services to foreign clients?"
"What is the reverse charge mechanism under GST?"
"Explain the input tax credit restrictions in the latest circular"
```

---

## 📁 Project Structure

```
PolicyFlow/
├── compliance/                 # Main Django app
│   ├── agent_logic.py         # Autonomous agent
│   ├── google_drive_monitor.py # Drive monitoring
│   ├── ingest_to_db.py        # Document ingestion
│   ├── retriever.py           # RAG retrieval
│   ├── vertex_embeddings.py   # Embeddings wrapper
│   ├── views.py               # API endpoints
│   └── models.py              # Database models
│
├── PolicyFlow_backend/        # Django settings
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
├── frontend/                  # React frontend
│   ├── src/
│   │   ├── components/        # React components
│   │   ├── pages/             # Page components
│   │   ├── services/          # API services
│   │   └── hooks/             # Custom hooks
│   └── package.json
│
├── data/                      # Data directory
│   └── raw_pdfs/              # Source documents
│
├── .env.example               # Environment template
├── .gitignore                 # Git ignore rules
├── requirements.txt           # Python dependencies
├── manage.py                  # Django CLI
└── README.md                  # This file
```

---

## 🔌 API Documentation

### Authentication

All API endpoints require authentication via Google OAuth or JWT token.

**Headers**:
```
Authorization: Bearer <your-google-token>
```

### Core Endpoints

#### Chat API
**POST** `/api/chat/`

Send a message to the AI assistant.

#### Document Upload
**POST** `/api/documents/upload/`

Upload a document for compliance analysis.

#### User Profile
**GET/PUT** `/api/user/profile/`

Get or update user profile.

For complete API documentation, including authentication, request/response examples, and error handling, see [API Documentation](docs/API.md).

---

## 🚀 Deployment

### Docker Deployment

```bash
# Build image
docker build -t PolicyFlow .

# Run container
docker run -p 8000:8000 --env-file .env PolicyFlow
```

### Production Checklist

- [ ] Set `DEBUG=False` in `.env`
- [ ] Generate secure `SECRET_KEY`
- [ ] Configure `ALLOWED_HOSTS`
- [ ] Set up proper CORS origins
- [ ] Use production database
- [ ] Configure static file serving
- [ ] Set up SSL/TLS certificates
- [ ] Enable logging and monitoring

### Recommended Platforms

- **Backend**: Render, Railway, Google Cloud Run
- **Frontend**: Vercel, Netlify, Cloudflare Pages
- **Database**: Supabase, Railway PostgreSQL

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests and linting
5. Submit a Pull Request

### Code Style

- **Python**: Follow PEP 8, use Black formatter
- **TypeScript**: Follow project ESLint configuration
- **Commits**: Use conventional commits format

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## �🙏 Acknowledgments

- **Google Cloud Platform** for Vertex AI and Document AI
- **Django** and **React** communities
- **shadcn/ui** for beautiful UI components
- **LangChain** for document processing framework
- **Supabase** for database infrastructure

---

## 📞 Contact & Support

- **Issues**: Open an issue on GitHub
- **Security**: Report vulnerabilities privately to the maintainers

---

## 🗺️ Roadmap

- [ ] Multi-language support
- [ ] Export compliance reports
- [ ] Advanced analytics dashboard
- [ ] Integration with accounting software
- [ ] Mobile app (React Native)
- [ ] Custom knowledge base upload
- [ ] Team collaboration features

---

## 🔒 Security

- **No credentials or secrets are included in this repository.**
- All sensitive data must be configured via environment variables.
- See [docs/OPEN_SOURCE_GUIDE.md](docs/OPEN_SOURCE_GUIDE.md) for best practices.

---

<div align="center">

**Built with Django, React, Google Vertex AI, and open source passion.**

**[⬆ back to top](#-PolicyFlow---ai-powered-tax-compliance-assistant)**

</div>
