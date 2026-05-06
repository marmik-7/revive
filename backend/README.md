# 🌱 Freedom Journey — Backend API

A production-ready Node.js + Express backend for a motivational addiction recovery web application. Built with Supabase (PostgreSQL + Auth + Realtime), Google Gemini/Groq AI, and email services.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Environment Variables](#environment-variables)
- [Database Schema](#database-schema)
- [API Endpoints](#api-endpoints)
- [Development](#development)
- [Deployment](#deployment)
- [Contributing](#contributing)

---

## Overview

Freedom Journey is a comprehensive backend API designed to support addiction recovery users by providing:

- **User Management**: Authentication, profiles, and account management
- **Addiction Tracking**: Track multiple addictions with streaks and insights
- **AI Support**: Daily motivation, chat support, and personalized recovery plans
- **Daily Check-ins**: Track mood, energy, urges, and progress
- **Journal Entries**: Reflective journaling with mood tracking
- **Recovery Plans**: AI-generated 21-day personalized recovery plans
- **Dashboard Analytics**: Comprehensive progress tracking and analytics

---

## Tech Stack

| Technology | Purpose |
|-----------|---------|
| **Node.js** (≥18.0.0) | Runtime environment |
| **Express.js** | Web framework |
| **Supabase** | PostgreSQL database + Auth + Realtime |
| **Google Gemini** / **Groq** | AI services for chat & plans |
| **Resend** / **Gmail** | Email delivery |
| **JWT** | Token-based authentication |
| **Joi** | Schema validation |
| **Helmet** | Security middleware |
| **Morgan** | Request logging |
| **express-rate-limit** | Rate limiting |

---

## Features

✅ **Authentication**
- Email/password signup & login
- OAuth integration (Google, GitHub)
- JWT token management
- Password reset functionality

✅ **User Profile Management**
- Profile creation and updates
- Avatar upload support
- Timezone preferences
- Email notification preferences

✅ **Addiction Tracking**
- Track up to 3 active addictions per user
- Supported types: porn, gaming, substance, smoking, drinking
- Streak management (current & longest)
- Last use timestamps
- Daily spend/hours tracking
- Motivation level tracking

✅ **Recovery Plans**
- AI-generated 21-day personalized recovery plans
- Milestone tracking
- Daily action items

✅ **Daily Check-ins**
- Daily mood, energy, and urge tracking
- Streak management
- Progress visualization

✅ **Journal**
- Create, read, update, delete journal entries
- Mood tracking
- Tag-based organization

✅ **Urge Logging**
- Log urges with intensity levels
- AI-powered coping strategies
- Historical urge tracking

✅ **AI Features**
- Daily motivational messages
- Real-time chat support
- Reflection prompts
- Coping strategy suggestions

✅ **Security**
- CORS protection
- Rate limiting (general, auth, AI)
- Helmet security headers
- Input validation
- JWT authentication

---

## Project Structure

```
backend/
├── src/
│   ├── server.js                     # Application entry point
│   ├── app.js                        # Express setup & middleware
│   │
│   ├── config/
│   │   └── supabase.js               # Supabase client initialization
│   │
│   ├── controllers/                  # Request handlers
│   │   ├── auth.controller.js        # Authentication logic
│   │   ├── user.controller.js        # User profile management
│   │   ├── addiction.controller.js   # Addiction CRUD operations
│   │   ├── plan.controller.js        # Recovery plan management
│   │   ├── journal.controller.js     # Journal entry CRUD
│   │   ├── checkin.controller.js     # Daily check-ins
│   │   ├── urge.controller.js        # Urge logging
│   │   ├── dashboard.controller.js   # Dashboard data aggregation
│   │   └── ai.controller.js          # AI features (chat, plans, motivation)
│   │
│   ├── middleware/
│   │   ├── auth.js                   # JWT verification middleware
│   │   ├── errorHandler.js           # Global error handling
│   │   ├── notFound.js               # 404 handler
│   │   ├── rateLimiter.js            # Rate limiting configuration
│   │   └── validate.js               # Request validation middleware
│   │
│   ├── routes/                       # API route definitions
│   │   ├── auth.routes.js
│   │   ├── user.routes.js
│   │   ├── addiction.routes.js
│   │   ├── plan.routes.js
│   │   ├── journal.routes.js
│   │   ├── checkin.routes.js
│   │   ├── urge.routes.js
│   │   ├── dashboard.routes.js
│   │   └── ai.routes.js
│   │
│   ├── services/                     # Business logic layer
│   │   ├── ai.service.js             # AI provider abstraction (Gemini/Groq)
│   │   ├── email.service.js          # Email sending (Resend/Gmail)
│   │   └── rai.engine.js             # Recovery AI Engine
│   │
│   └── utils/
│       └── helpers.js                # Utility functions
│
├── sql/
│   └── schema.sql                    # PostgreSQL database schema
│
├── .env.example                      # Environment variables template
├── check-db.js                       # Database connection checker
├── nodemon.json                      # Nodemon configuration
├── package.json
└── README.md
```

---

## Installation & Setup

### 1. Clone & Install Dependencies

```bash
cd backend
npm install
```

### 2. Create Environment File

```bash
cp .env.example .env.local
```

### 3. Set Up Database

Create a Supabase project and run the schema:

```bash
# Using Supabase CLI (recommended)
supabase db push

# Or manually run sql/schema.sql in Supabase SQL editor
```

### 4. Configure Environment Variables

See [Environment Variables](#environment-variables) section below.

### 5. Start Development Server

```bash
npm run dev
```

Server runs on `http://localhost:5000` (or port in `.env`)

---

## Environment Variables

Create a `.env.local` file in the `backend/` directory:

```env
# Server Configuration
NODE_ENV=development
PORT=5000
HOST=localhost

# Supabase Configuration
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_ANON_KEY=your_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

# Frontend URL
FRONTEND_URL=http://localhost:5173

# AI Provider Configuration
# Choose one: gemini or groq
AI_PROVIDER=gemini

# Google Gemini Configuration (if using Gemini)
GOOGLE_API_KEY=your_google_api_key

# Groq Configuration (if using Groq)
GROQ_API_KEY=your_groq_api_key

# Email Configuration
EMAIL_PROVIDER=resend  # or 'gmail'

# Resend Configuration (if using Resend)
RESEND_API_KEY=your_resend_api_key

# Gmail SMTP Configuration (if using Gmail)
GMAIL_USER=your_email@gmail.com
GMAIL_APP_PASSWORD=your_app_password

# Sender Email
SENDER_EMAIL=noreply@freedomjourney.com

# Database Check Configuration
DB_CHECK_ENABLED=true

# CORS Configuration
CORS_ORIGIN=http://localhost:5173,https://yourdomain.com
```

---

## Database Schema

### Core Tables

#### `profiles`
- User profile information
- Email, name, avatar, bio, timezone preferences
- Email notification settings

#### `addictions`
- User addiction records (max 3 active per user)
- Types: porn, gaming, substance, smoking, drinking
- Streak tracking, motivation levels, daily metrics

#### `plans`
- AI-generated 21-day recovery plans
- Milestones and daily action items
- One plan per addiction

#### `journal_entries`
- User journal entries
- Mood tracking, tags, content
- Linked to specific addiction

#### `checkins`
- Daily check-ins (one per user/addiction/day)
- Mood, energy, urge level, sleep quality
- Completion tracking

#### `urge_logs`
- Urge logging with intensity and coping strategies
- AI-suggested responses
- Timestamp tracking

#### `ai_interactions` (optional)
- Track AI chat history and interactions
- User feedback on suggestions

---

## API Endpoints

### Authentication
```
POST   /api/auth/signup              # Create new account
POST   /api/auth/login               # Login with email/password
POST   /api/auth/logout              # Logout
POST   /api/auth/forgot-password     # Request password reset
POST   /api/auth/reset-password      # Confirm password reset
GET    /api/auth/callback            # OAuth callback
```

### User Management
```
GET    /api/users/profile            # Get user profile
PUT    /api/users/profile            # Update profile
DELETE /api/users                    # Delete account
```

### Addictions
```
GET    /api/addictions               # List user's addictions
POST   /api/addictions               # Create addiction
PUT    /api/addictions/:id           # Update addiction
DELETE /api/addictions/:id           # Delete addiction
POST   /api/addictions/:id/relapse   # Log a relapse
```

### Plans
```
GET    /api/plans/:addictionId       # Get recovery plan
POST   /api/plans                    # Generate new plan via AI
```

### Daily Check-ins
```
GET    /api/checkins                 # Get check-ins
POST   /api/checkins                 # Create check-in
GET    /api/checkins/today           # Get today's check-in
```

### Journal
```
GET    /api/journal                  # List journal entries
POST   /api/journal                  # Create entry
PUT    /api/journal/:id              # Update entry
DELETE /api/journal/:id              # Delete entry
```

### Urges
```
GET    /api/urges                    # List urges
POST   /api/urges                    # Log new urge
GET    /api/urges/:id/strategies     # Get coping strategies
```

### AI Features
```
POST   /api/ai/chat                  # Send chat message
POST   /api/ai/motivation            # Get daily motivation
POST   /api/ai/reflection            # Get reflection prompt
```

### Dashboard
```
GET    /api/dashboard                # Get dashboard summary
GET    /api/dashboard/stats          # Get detailed statistics
```

### Health Check
```
GET    /health                       # Server health status
```

---

## Development

### Available Scripts

```bash
# Start development server with auto-reload
npm run dev

# Start production server
npm start

# Run ESLint
npm run lint

# Check database connection
node check-db.js
```

### Development Workflow

1. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature
   ```

2. Make changes and test locally:
   ```bash
   npm run dev
   ```

3. Lint your code:
   ```bash
   npm run lint
   ```

4. Commit and push:
   ```bash
   git add .
   git commit -m "feat: description of changes"
   git push origin feature/your-feature
   ```

### Error Handling

The API uses a standardized error response format:

```json
{
  "success": false,
  "error": "Error message",
  "status": 400
}
```

Common status codes:
- `200` - Success
- `400` - Bad Request (validation error)
- `401` - Unauthorized (invalid/missing token)
- `403` - Forbidden (insufficient permissions)
- `404` - Not Found
- `429` - Too Many Requests (rate limited)
- `500` - Internal Server Error

---

## Deployment

### Build for Production

```bash
# No build step needed for Node.js backend
# Simply ensure dependencies are installed
npm install --production
```

### Environment Setup

Set all environment variables in your hosting platform:

- Vercel, Heroku, AWS Lambda, DigitalOcean, etc.

### Deployment Options

1. **Vercel** (Recommended for full-stack)
2. **Heroku**
3. **Railway**
4. **AWS Lambda + API Gateway**
5. **DigitalOcean App Platform**

### Database Migrations

```bash
# Run schema on new Supabase project
supabase db push
```

---

## Contributing

### Code Standards

- Use consistent naming conventions
- Add comments for complex logic
- Follow the controller → service → repository pattern
- Add input validation for all endpoints
- Test edge cases

### Pull Request Process

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit PR with clear description
6. Address review comments

### Reporting Issues

Please include:
- Clear description of the issue
- Steps to reproduce
- Expected vs actual behavior
- Environment details (Node version, OS, etc.)

---

## License

This project is part of the Freedom Journey initiative for addiction recovery support.

---

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Contact: support@freedomjourney.com

---

**Made with ❤️ to support addiction recovery journeys.**
