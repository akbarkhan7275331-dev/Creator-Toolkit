# Creator Toolkit

AI-powered SaaS platform that helps content creators repurpose long-form content into viral short-form content for YouTube Shorts, TikTok, and Instagram Reels.

## Architecture

- **Frontend**: React + TypeScript with Wouter routing, TanStack Query, Shadcn UI
- **Backend**: Express.js with Passport.js local auth, PostgreSQL via Drizzle ORM
- **AI**: OpenAI via Replit AI Integrations (gpt-5-nano for text generation)
- **Styling**: Tailwind CSS with custom theme tokens

## Project Structure

```
client/src/
  App.tsx           - Main app with routing and auth gate
  lib/auth.tsx      - Auth context provider (login/register/logout)
  lib/queryClient.ts - TanStack Query config
  components/
    dashboard-layout.tsx - Sidebar + main content layout
    copy-button.tsx      - Copy-to-clipboard button
    result-card.tsx      - Reusable result display card
  pages/
    auth-page.tsx        - Login/register page
    dashboard.tsx        - Tool overview dashboard
    hook-generator.tsx   - Viral hook generator
    caption-generator.tsx - Social media caption generator
    hashtag-generator.tsx - Trending hashtag generator
    title-generator.tsx  - YouTube title generator
    clip-generator.tsx   - Video clip timestamp finder
    idea-generator.tsx   - Content idea generator
    script-generator.tsx - Short-form video script generator

server/
  index.ts    - Express server setup
  routes.ts   - All API routes (auth + AI generation)
  auth.ts     - Passport.js local auth setup with sessions
  storage.ts  - Database storage layer
  db.ts       - Drizzle ORM + PostgreSQL pool

shared/
  schema.ts   - Drizzle schemas (users, generations)
```

## Database Schema

- **users**: id (serial), username, password (hashed), createdAt
- **generations**: id (serial), userId, tool, input, output, createdAt

## Features

1. User auth (register/login with hashed passwords, sessions)
2. 7 AI-powered content tools with daily free limits (20/day)
3. Sidebar navigation with usage tracking
4. Copy-to-clipboard on all generated content
5. Mobile responsive design

## Environment

- DATABASE_URL - PostgreSQL connection
- SESSION_SECRET - Session encryption key
- AI_INTEGRATIONS_OPENAI_API_KEY / AI_INTEGRATIONS_OPENAI_BASE_URL - Auto-configured by Replit AI Integrations
