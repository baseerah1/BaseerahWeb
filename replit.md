# OnSpace - AI-Powered E-Commerce Platform

## Overview
An AI-powered e-commerce utility platform. Provides tools to generate product descriptions, analyze customer sentiment, create video scripts, and calculate pricing. No longer includes store integrations—focus is on product import and AI-powered content generation.

## Tech Stack
- **Frontend**: React 18 + TypeScript
- **Build System**: Vite 5 with @vitejs/plugin-react-swc
- **Styling**: Tailwind CSS + shadcn/ui (Radix UI)
- **State**: Redux Toolkit + Zustand + TanStack Query
- **Routing**: React Router DOM v6
- **Backend/Auth**: Supabase (BaaS)
- **AI**: Supabase Edge Functions + Gemini Flash
- **Package Manager**: npm

## Project Structure
- `src/` - Main application source
  - `components/` - UI and feature components
  - `hooks/` - Custom React hooks
  - `lib/` - Core services (supabase, AI, export)
  - `pages/` - Route-level page components
  - `types/` - TypeScript definitions
- `supabase/functions/` - Deno-based Edge Functions for AI operations
- `public/` - Static assets

## Core Features
1. **Product Description Generator** (`/product-description`):
   - AI-powered title and description generation
   - SEO keyword extraction
   - Key features/bullet points generation
   - Store product import (Shopify, YouCan, WooCommerce)

2. **Store Integration** (integrated in product description):
   - **Shopify** (requires Access Token)
   - **YouCan** (requires API Token)
   - **WooCommerce** (requires Consumer Key/Secret)
   - Direct API key authentication
   - One-click product selection for AI generation

3. **Other Tools**:
   - Sentiment analysis (customer review analysis)
   - Video script generator (TikTok/Reels content)
   - Pricing calculator (smart pricing)

## Branding
- **Name**: بُصَيْرَة (with vowel marks)
- **New Logo**: `/public/logo.png` (hand/eye design)
- Logo displayed in Sidebar, Landing Page, and Login pages

## Authentication
- **Backend**: Supabase Auth (cloud-based, works from any device)
- **Flow**: Email + password signup/login via Supabase
- **Session**: Managed by Supabase — persistent JWT tokens, no localStorage
- **Password Reset**: Real email via Supabase with secure reset link
- **Auth Context**: `src/contexts/AuthContext.tsx` — reactive session state via `useAuth()` hook
- **Protected Routes**: Show loading spinner until session resolves, then redirect if unauthenticated

## Removed Features
- Product import standalone page (`/product-import`)
- OAuth 2.0 authentication flows
- localStorage-based authentication (replaced by Supabase Auth)
- Direct product publishing to stores
- Store connection persistence (connections are session-only)

## Environment Variables
- `VITE_SUPABASE_URL` - Supabase project URL (set in .env)
- `VITE_SUPABASE_ANON_KEY` - Supabase anonymous key (set in .env)

## Development
- Run: `npm run dev` (port 5000, host 0.0.0.0)
- Build: `npm run build`

## Deployment
- Target: Static site
- Build command: `npm run build`
- Public directory: `dist`

## Replit Configuration
- Workflow: "Start application" → `npm run dev` on port 5000
- Vite configured with `allowedHosts: true` and host `0.0.0.0` for Replit proxy compatibility

## Recent Changes (Latest)
- Removed: ProductImport.tsx standalone page
- Updated: Sidebar menu (removed product import page link)
- Updated: App.tsx routes (removed /product-import route)
- Added: New logo (`/public/logo.png`) in Sidebar and Landing Page
- Store import feature remains integrated in ProductDescription page

Previous changes:
- Removed OAuth and store integration pages
- Added store import service for direct API access
- Integrated StoreImportDialog into ProductDescription
