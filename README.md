# zqmlabs-backend

FastAPI backend serving [zqmlabs.com](https://zqmlabs.com) API routes.

## Domain: zqmlabs.com / api.zqmlabs.com

| Endpoint | Function |
|----------|----------|
| `/health` | Health check |
| `/latest` | Latest indicator data |
| `/data/indicators.json` | All 50 indicators |
| `/refresh` | Manual data refresh |
| `/gamification/*` | Proxied to zqmlabs-gamification |

## Architecture

This is the **backend layer** of the ZQM modular architecture. It provides:
- 50 indicators across 11 categories (economic, tourism, demographics, etc.)
- Data refresh pipeline
- API proxy to gamification service

## Domain Mapping

```
api.zqmlabs.com → zqmlabs-backend (FastAPI :8000)
zqmlabs.com → zqmlabs-frontend (React SPA) → zqmlabs-backend (API calls)
volusia.zqmlabs.com → volusia-zqmlabs (separate backend)
```

## Development

```bash
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000
```

## Repo Map

```
zqmlabs-frontend ←→ zqmlabs-backend (API calls)
zqmlabs-gamification ←→ zqmlabs-backend (proxy)
zqmlabs-backend ←→ volusia-zqmlabs (data sharing)
```
