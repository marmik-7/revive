# 🎨 Freedom Journey — Frontend

A modern, responsive React web application for supporting addiction recovery. Built with Vite, React Router, Tailwind CSS, and Supabase.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Environment Variables](#environment-variables)
- [Development](#development)
- [Building & Deployment](#building--deployment)
- [Architecture](#architecture)
- [Contributing](#contributing)

---

## Overview

Freedom Journey Frontend is a modern web application designed to provide:

- **User Authentication**: Secure signup, login, and OAuth integration
- **Onboarding Flow**: Guided setup for new users
- **Dashboard**: Real-time progress tracking and analytics
- **Daily Check-ins**: Quick mood, energy, and urge tracking
- **Journal**: Reflective journaling with mood tracking
- **Recovery Plans**: AI-generated 21-day personalized plans
- **AI Chat**: Real-time support and motivation
- **Settings**: Profile management and preferences

---

## Tech Stack

| Technology | Purpose |
|-----------|---------|
| **React** (18.3.1) | UI library |
| **Vite** | Fast build tool & dev server |
| **React Router** (v6) | Client-side routing |
| **Tailwind CSS** | Utility-first styling |
| **Supabase** | Backend authentication & database |
| **Zustand** | State management |
| **React Hook Form** | Form handling |
| **Framer Motion** | Animations |
| **Recharts** | Data visualization |
| **Axios** | HTTP client |
| **Zod** | Schema validation |
| **Lucide React** | Icon library |
| **Sonner** | Toast notifications |
| **date-fns** | Date utilities |

---

## Features

✅ **Authentication**
- Email/password signup and login
- OAuth (Google, GitHub)
- Persistent sessions via Supabase Auth
- Password reset functionality

✅ **Onboarding**
- Choose addiction type (porn, gaming, substance, smoking, drinking)
- Enter addiction details (motivation, spend, hours)
- AI-powered plan generation
- Setup completion

✅ **Dashboard**
- Overview of all tracked addictions
- Current streaks and progress
- Quick access to daily features
- Analytics and statistics

✅ **Daily Features**
- **Check-in**: Log mood, energy, urge level, sleep quality
- **Journal**: Write reflective entries with mood tracking
- **Log Urge**: Record urges with AI-suggested coping strategies
- **Plan View**: Track daily recovery plan milestones

✅ **AI Features**
- Real-time chat with AI coach
- Daily motivational messages
- Reflection prompts
- Coping strategy suggestions

✅ **Settings**
- Profile management
- Avatar upload
- Timezone preferences
- Email notification settings
- Account deletion

✅ **Progress Tracking**
- Streak management
- Historical analytics
- Charts and visualizations
- Mood trends

✅ **Responsive Design**
- Mobile-first approach
- Works on desktop, tablet, mobile
- Touch-friendly interface
- Fast performance

---

## Project Structure

```
frontend/
├── src/
│   ├── main.jsx                      # React entry point
│   ├── App.jsx                       # Root component
│   ├── index.css                     # Global styles
│   │
│   ├── components/
│   │   └── ui/
│   │       └── index.jsx             # Reusable UI components
│   │
│   ├── layouts/
│   │   ├── AuthLayout.jsx            # Layout for auth pages
│   │   └── DashboardLayout.jsx       # Layout for app pages
│   │
│   ├── lib/
│   │   ├── api.js                    # API client & endpoints
│   │   ├── supabase.js               # Supabase client init
│   │   ├── utils.js                  # Utility functions
│   │   └── motionVariants.js         # Framer Motion animations
│   │
│   ├── pages/
│   │   ├── Landing.jsx               # Landing page
│   │   │
│   │   ├── auth/
│   │   │   ├── Login.jsx             # Login page
│   │   │   ├── Signup.jsx            # Signup page
│   │   │   ├── ForgotPassword.jsx    # Password reset
│   │   │   └── AuthCallback.jsx      # OAuth callback handler
│   │   │
│   │   ├── onboarding/
│   │   │   ├── ChooseAddiction.jsx   # Select addiction type
│   │   │   ├── AddictionDetails.jsx  # Enter details
│   │   │   └── PlanGenerating.jsx    # Loading state
│   │   │
│   │   ├── daily/
│   │   │   ├── Checkin.jsx           # Daily check-in
│   │   │   ├── Journal.jsx           # Journal entry
│   │   │   └── LogUrge.jsx           # Log urge
│   │   │
│   │   ├── dashboard/
│   │   │   ├── Dashboard.jsx         # Main dashboard
│   │   │   ├── Plan.jsx              # View recovery plan
│   │   │   └── Progress.jsx          # View analytics
│   │   │
│   │   ├── ai/
│   │   │   └── Chat.jsx              # AI chat interface
│   │   │
│   │   └── settings/
│   │       ├── Settings.jsx          # Settings page
│   │       └── ResetPassword.jsx     # Change password
│   │
│   ├── store/
│   │   ├── authStore.js              # Authentication state (Zustand)
│   │   └── appStore.js               # Application state (Zustand)
│   │
│   ├── tailwind.config.js            # Tailwind configuration
│   ├── postcss.config.js             # PostCSS configuration
│   ├── vite.config.js                # Vite configuration
│   └── vercel.json                   # Vercel deployment config
│
├── index.html                        # HTML entry point
├── package.json
└── README.md
```

---

## Installation & Setup

### 1. Clone & Install Dependencies

```bash
cd frontend
npm install
```

### 2. Create Environment File

```bash
cp .env.example .env.local
```

### 3. Configure Environment Variables

See [Environment Variables](#environment-variables) section below.

### 4. Start Development Server

```bash
npm run dev
```

App runs on `http://localhost:5173` (Vite default)

---

## Environment Variables

Create a `.env.local` file in the `frontend/` directory:

```env
# Supabase Configuration
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your_anon_key

# Backend API Configuration
VITE_API_URL=http://localhost:5000
VITE_API_TIMEOUT=10000

# Environment
VITE_ENV=development

# Feature Flags (optional)
VITE_ENABLE_AI_CHAT=true
VITE_ENABLE_ANALYTICS=true
```

**Note**: All Vite environment variables must be prefixed with `VITE_` to be accessible in the browser.

---

## Development

### Available Scripts

```bash
# Start development server with hot reload
npm run dev

# Build for production
npm build

# Preview production build locally
npm preview
```

### Development Workflow

1. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature
   ```

2. Start dev server:
   ```bash
   npm run dev
   ```

3. Make changes and test in browser
   - Changes auto-reload thanks to Vite
   - Open browser DevTools for debugging

4. Commit and push:
   ```bash
   git add .
   git commit -m "feat: description of changes"
   git push origin feature/your-feature
   ```

### Hot Module Replacement (HMR)

Vite provides instant HMR:
- React component changes reflect immediately
- State is preserved during hot reload
- CSS changes apply without full refresh

### Debugging Tips

1. **React DevTools**: Install Chrome/Firefox extension
2. **Network Tab**: Monitor API calls in DevTools
3. **Supabase Logs**: Check realtime events in Supabase dashboard
4. **Console Logging**: Use `console.log()` for debugging
5. **Breakpoints**: Set breakpoints in DevTools

---

## Building & Deployment

### Build for Production

```bash
npm run build
```

This creates an optimized production build in the `dist/` folder:
- Bundled and minified code
- Optimized images
- Source maps for debugging

### Preview Production Build

```bash
npm preview
```

Serves the production build locally for testing.

### Deployment Options

#### 1. **Vercel** (Recommended)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Set environment variables in Vercel dashboard
```

The `vercel.json` is pre-configured for optimal settings.

#### 2. **GitHub Pages**

```bash
# Update vite.config.js base path
# Then push to gh-pages branch
npm run build
git add dist
git commit -m "build: deploy to GitHub Pages"
git push origin main
```

#### 3. **Netlify**

Connect your GitHub repository to Netlify:
- Build command: `npm run build`
- Publish directory: `dist/`
- Set environment variables in Netlify dashboard

#### 4. **Self-Hosted**

```bash
# Build and serve with any static server
npm run build
npx serve dist

# Or use nginx, Apache, etc.
```

---

## Architecture

### State Management

Uses **Zustand** for lightweight, scalable state:

```javascript
// authStore.js - Authentication state
export const useAuthStore = create((set) => ({
  user: null,
  isLoading: false,
  login: async (email, password) => { /* ... */ },
  logout: () => { /* ... */ },
}));

// appStore.js - Application state
export const useAppStore = create((set) => ({
  addictions: [],
  currentAddiction: null,
  fetchAddictions: async () => { /* ... */ },
}));
```

### API Communication

Centralized API client in `lib/api.js`:

```javascript
import axios from 'axios';

const api = axios.create({
  baseURL: import.meta.env.VITE_API_URL,
  timeout: import.meta.env.VITE_API_TIMEOUT,
});

// Automatically attach auth token
api.interceptors.request.use((config) => {
  // Add JWT token from Supabase
  return config;
});

export default api;
```

### Authentication Flow

1. User logs in via Supabase
2. Supabase returns JWT token
3. Token stored in browser (auto via Supabase)
4. API requests include `Authorization: Bearer <token>`
5. Backend verifies token with Supabase

### Form Handling

Uses **React Hook Form** + **Zod** for robust forms:

```javascript
const { register, handleSubmit, formState: { errors } } = useForm({
  resolver: zodResolver(schema),
});
```

---

## Performance Optimization

### Code Splitting

React Router automatically code-splits pages:

```javascript
const Dashboard = lazy(() => import('./pages/dashboard/Dashboard'));
```

### Image Optimization

- Use `.webp` format when possible
- Lazy load images with `loading="lazy"`
- Compress images before uploading

### Bundle Analysis

```bash
# Install plugin (optional)
npm install --save-dev rollup-plugin-visualizer

# Analyze bundle in vite.config.js
```

### Lighthouse Improvements

- ✅ Minimal JavaScript bundle
- ✅ Optimized CSS (Tailwind)
- ✅ Fast API responses (edge)
- ✅ Caching strategies

---

## Contributing

### Code Standards

- Use functional components with hooks
- Keep components small and focused
- Use meaningful variable/function names
- Add comments for complex logic
- Follow Tailwind CSS conventions

### Component Guidelines

```javascript
// Good component structure
export default function ComponentName() {
  const [state, setState] = useState(null);
  const { user } = useAuthStore();

  useEffect(() => {
    // Side effects here
  }, []);

  const handleAction = () => {
    // Event handlers
  };

  return (
    <div className="flex flex-col gap-4">
      {/* JSX */}
    </div>
  );
}
```

### Pull Request Process

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Make your changes
4. Test thoroughly (`npm run dev`)
5. Build for production (`npm run build`)
6. Submit PR with clear description

### Reporting Issues

Include:
- Clear description of the issue
- Steps to reproduce
- Expected vs actual behavior
- Browser/OS information
- Screenshots if applicable

---

## Troubleshooting

### Common Issues

#### Blank page on load
- Check browser console for errors
- Ensure `.env.local` has correct Supabase credentials
- Verify backend API is running

#### CORS errors
- Backend CORS must allow frontend URL
- Check `FRONTEND_URL` in backend `.env`

#### Authentication not persisting
- Supabase auth should auto-persist
- Check browser localStorage
- Verify Supabase client initialization

#### Slow build
- Clear `node_modules` and reinstall
- Check for large dependencies
- Use `npm run build -- --debug` for details

---

## Performance Metrics

Target metrics:
- **FCP** (First Contentful Paint): < 1.5s
- **LCP** (Largest Contentful Paint): < 2.5s
- **CLS** (Cumulative Layout Shift): < 0.1
- **Bundle Size**: < 200KB (gzipped)

Monitor with:
- Lighthouse (Chrome DevTools)
- WebPageTest
- New Relic
- Sentry

---

## Browser Support

- Chrome/Edge: Latest 2 versions
- Firefox: Latest 2 versions
- Safari: Latest 2 versions
- iOS Safari: iOS 13+
- Mobile Chrome: Latest

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
