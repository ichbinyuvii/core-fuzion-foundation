# Fuzion Coaching Institute

A premium, production-grade Coaching ERP foundation.

[Open the Fuzion Coaching live site](https://fuzioncoaching.onrender.com/)

![Fuzion Coaching interface](https://yuvrajsinghnegi.vercel.app/images/projects/fuzion-coaching.webp)

> This repository is the **foundation phase**. Business modules (Student, Teacher, Parent, and Admin portals, CBT engine, Fee Management, etc.) will be built on top without modifying the architecture.

## Tech Stack

- **React 19** + **TypeScript** + **Vite**
- **Tailwind CSS v4** (CSS-first, oklch design tokens)
- **React Router v7** (SPA routing + route guards)
- **React Hook Form** (typed forms)
- **TanStack Query** (server-state cache)
- **Firebase**: Auth, Firestore, Storage, Cloud Functions, Firebase Hosting
- **Framer Motion** (motion system)
- **Chart.js** + **react-chartjs-2**
- **Sonner** (toasts)
- **Lucide** (icons)

## Getting Started

```bash
bun install
cp .env.example .env.local   # Fill in your Firebase project keys
bun dev
```

Open http://localhost:8080.

Without Firebase environment variables, the UI renders but authentication and database actions show a configuration error.

## Firebase Setup

1. Create a Firebase project.
2. Enable Authentication, Firestore, Storage, Cloud Functions, and Hosting.
3. Copy your web app configuration into `.env.local` (`VITE_FIREBASE_*`).
4. Deploy security rules and indexes:
   ```bash
   firebase deploy --only firestore:rules,firestore:indexes,storage
   ```
5. Build and deploy hosting:
   ```bash
   bun run build
   firebase deploy --only hosting
   ```

## Folder Structure

```
src/
├── app/                    App shell and provider composition
├── config/                 Environment and runtime configuration
├── constants/              App routes, roles, and settings
├── context/                Auth, theme, and sidebar contexts
├── features/               Feature modules
├── hooks/                  Reusable hooks
├── layouts/                App layouts
├── pages/                  Route components
├── routes/                 Router and route guards
├── services/               Firebase and application services
├── components/              UI, forms, charts, navigation, and media
├── theme/                  Design tokens
├── types/                  Shared types
└── utils/                  Small helpers
```

## Roles

The foundation defines student, teacher, parent, and admin roles in `src/types/user.ts` and `src/constants/roles.ts`.

## Adding a Feature Module

1. Create `src/features/<module>/` with components, hooks, services, and types.
2. Add pages under `src/pages/<module>/`.
3. Register guarded routes in `src/routes/AppRouter.tsx`.
4. Add navigation entries and required Firestore rules.

## Deployment

Firebase Hosting is preconfigured. Any static host serving `dist/` with an SPA fallback can also be used.
