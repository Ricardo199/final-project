# Civic Issue Tracker

A full-stack web application that empowers residents, city staff, and community advocates to report, track, and resolve civic issues — from potholes to streetlights — in their neighborhoods.

---

## Features

- **Issue Reporting** — Submit civic issues with title, description, category, priority, and geolocation.
- **Issue Tracking** — View and filter issues by status, category, or reporter.
- **Role-Based Access Control** — Three roles with tailored permissions:
  - `resident` — report and track their own issues
  - `staff` — manage, assign, and resolve issues
  - `advocate` — monitor trends and community engagement
- **Dashboard Analytics** — Summary of open/resolved issues, high-priority items, and breakdowns by category.
- **AI Services** — Rule-based issue summarization, automatic classification, and trend insights.
- **Chatbot** — Answer questions about civic issues using an agent-powered Q&A interface.
- **Search** — Full-text search across reported issues.
- **JWT Authentication** — Secure sign-up and login with token-based sessions.

---

## Tech Stack

### Backend
| Layer | Technology |
|---|---|
| Runtime | Node.js |
| Framework | Express |
| API | GraphQL (Apollo Server 4) |
| Database | MongoDB (Mongoose) |
| Auth | JWT + bcryptjs |
| AI | Rule-based heuristics (Gemini/LangGraph ready) |

### Frontend
| Layer | Technology |
|---|---|
| UI Framework | React 19 + Vite |
| Routing | React Router DOM |
| GraphQL Client | Apollo Client |
| Styling | Tailwind CSS (planned) |

---

## Project Structure

```
civic-issue-tracker/
├── backend/
│   ├── graphQL/
│   │   ├── typeDefs.js       # GraphQL schema
│   │   └── resolvers.js      # Query & mutation resolvers
│   ├── model/
│   │   ├── user.js           # User model
│   │   └── issue.js          # Issue model
│   ├── services/
│   │   ├── aiService.js      # AI summarization, classification, trends
│   │   ├── auth.js           # Authentication helpers
│   │   └── issuesService.js  # Issue business logic
│   ├── utils/                # Utility functions
│   └── server.js             # Entry point
└── frontend/
    ├── src/                  # React application source
    ├── public/               # Static assets
    └── index.html
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [MongoDB](https://www.mongodb.com/) (local or Atlas)

### Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file in the `backend/` directory:

```env
MONGO_URI=mongodb://localhost:27017/civic-issues
JWT_SECRET=your_jwt_secret_here
PORT=4001
```

Start the server:

```bash
# Development (with hot reload)
npm run dev

# Production
npm start
```

The GraphQL API will be available at `http://localhost:4001/graphql`.

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

The development server starts at `http://localhost:5173`.

---

## API Overview

### Authentication

| Operation | Description |
|---|---|
| `signUp` | Register a new user (resident / staff / advocate) |
| `login` | Authenticate and receive a JWT access token |

### Issues

| Operation | Type | Description |
|---|---|---|
| `issues` | Query | List issues with optional filters (status, category, reporter) |
| `issue(id)` | Query | Get a single issue by ID |
| `searchIssues(text)` | Query | Full-text search across issues |
| `reportIssue` | Mutation | Submit a new civic issue |
| `updateIssue` | Mutation | Update status, priority, category, or assignment |
| `assignIssue` | Mutation | Assign an issue to a staff member |
| `resolveIssue` | Mutation | Mark an issue as resolved |

### Analytics & AI

| Operation | Type | Description |
|---|---|---|
| `dashboardSummary` | Query | Aggregate counts by status and category |
| `trendInsights` | Query | Category-level trend data |
| `aiSummary(issueId)` | Query | AI-generated summary of an issue |
| `agentAnswer(question)` | Query | Chatbot Q&A about civic issues |

---

## Issue Categories

`pothole` · `streetlight` · `flooding` · `safety` · `other`

## Issue Statuses

`reported` → `in_progress` → `resolved` → `closed`

## Priority Levels

`low` · `medium` · `high`

---

## Roadmap

- [ ] Micro-frontend architecture (Auth, Issue Reporting, Tracking, Staff Dashboard, Advocate Portal)
- [ ] Gemini API integration for AI classification and summarization
- [ ] LangGraph agent for advanced chatbot capabilities
- [ ] Real-time notifications
- [ ] Sentiment analysis on issue descriptions
- [ ] ML-powered trend detection

---

## License

MIT
