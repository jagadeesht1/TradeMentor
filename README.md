# TradeMentor

**A Real-Time Stock Monitoring and Rule-Based Trading Assistance System**

Enterprise-grade AI fintech web application with Upstox-inspired UI — dark navy gradients, neon blue/emerald accents, glassmorphism cards, and professional trading dashboards.

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| Frontend | Next.js 14, React 18, TypeScript, Tailwind CSS, ShadCN-style UI, Framer Motion, Lightweight Charts, Recharts, Zustand |
| Backend | Node.js, Express.js, Prisma ORM, PostgreSQL, JWT, WebSockets |
| AI/Data | OpenAI GPT-4o-mini, Alpha Vantage, Finnhub, Yahoo Finance (mock fallback) |

## Features

- **30+ Premium UI Pages** — Dashboard, markets, portfolio, watchlist, analytics, AI assistant, admin panel, and more
- **Real-Time Quotes** — WebSocket streaming every 3 seconds
- **Candlestick Charts** — TradingView-style charts via Lightweight Charts
- **Technical Analysis** — RSI, MACD, MA20/50/200 with rule-based signals
- **AI Trading Assistant** — OpenAI-powered chat and buy/sell recommendations
- **Portfolio & Orders** — Holdings tracking, order placement, risk analysis
- **Subscription System** — FREE / PRO / ENTERPRISE tiers
- **Admin Panel** — User management and platform analytics

## Project Structure

```
TradeMentor/
├── frontend/          # Next.js 14 app (port 3000)
├── backend/           # Express API + WebSocket (port 4000)
├── docker-compose.yml # PostgreSQL database
└── package.json       # Monorepo scripts
```

## Quick Start

### Prerequisites

- Node.js 18+
- Docker (for PostgreSQL) or local PostgreSQL 16+
- API keys (optional): Alpha Vantage, Finnhub, OpenAI

### 1. Start Database

```bash
docker-compose up -d
```

### 2. Backend Setup

```bash
cd backend
cp .env.example .env
npm install
npx prisma generate
npx prisma db push
npm run db:seed
npm run dev
```

### 3. Frontend Setup

```bash
cd frontend
cp .env.example .env.local
npm install
npm run dev
```

### 4. Run Both (from root)

```bash
npm install
npm run dev
```

- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:4000/api
- **WebSocket:** ws://localhost:4000/ws

## Demo Accounts

| Role | Email | Password |
|------|-------|----------|
| User | demo@tradementor.com | User@123456 |
| Admin | admin@tradementor.com | Admin@123456 |

## Environment Variables

### Backend (`backend/.env`)

```env
DATABASE_URL="postgresql://tradementor:tradementor_secret@localhost:5432/tradementor?schema=public"
JWT_SECRET="your-super-secret-jwt-key"
PORT=4000
FRONTEND_URL="http://localhost:3000"
ALPHA_VANTAGE_API_KEY=""
FINNHUB_API_KEY=""
OPENAI_API_KEY=""
```

### Frontend (`frontend/.env.local`)

```env
NEXT_PUBLIC_API_URL=http://localhost:4000/api
NEXT_PUBLIC_WS_URL=ws://localhost:4000/ws
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register user |
| POST | `/api/auth/login` | Login |
| GET | `/api/stocks/quote/:symbol` | Stock quote |
| GET | `/api/stocks/candles/:symbol` | OHLCV candles |
| GET | `/api/stocks/analysis/:symbol` | Technical analysis |
| GET | `/api/stocks/recommendation/:symbol` | AI recommendation |
| GET | `/api/portfolio` | User portfolios |
| GET | `/api/watchlist` | User watchlists |
| GET | `/api/signals` | Trading signals |
| POST | `/api/chat` | AI chatbot |
| GET | `/api/news` | Financial news |
| GET | `/api/admin/stats` | Admin statistics |

## Pages (33+)

| Category | Pages |
|----------|-------|
| Public | Landing, Login, Register, About, Terms, Privacy |
| Trading | Dashboard, Markets, Stock Detail, Portfolio, Watchlist, Orders, Positions, Screener |
| Analytics | Analytics, Signals, RSI, MACD, Moving Averages, Risk, Heatmap |
| AI | AI Assistant, AI Recommendations, AI Insights |
| Account | Profile, Settings, Subscription, Notifications, News, Reports, Help |
| Admin | Admin Dashboard, Users, Analytics |

## Production Deployment

1. Set strong `JWT_SECRET` and production `DATABASE_URL`
2. Configure API keys for live market data
3. Build frontend: `cd frontend && npm run build`
4. Build backend: `cd backend && npm run build`
5. Run migrations: `npx prisma migrate deploy`
6. Deploy behind HTTPS with WebSocket proxy support

## License

MIT — For educational and demonstration purposes. Not financial advice.
