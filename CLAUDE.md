# CLAUDE.md — MiroFish Multi-Agent Swarm Prediction Engine

## Overview
MiroFish is a multi-agent swarm intelligence prediction engine that simulates societal, political, and narrative evolution from ingested documents. Stack: Python 3.11/3.12 (Flask, `camel-oasis`, `camel-ai`, `zep-cloud`), Vue 3 + Vite + D3 frontend, orchestrated with `npm` and `uv`.

## Commands
- Setup all dependencies: `npm run setup:all`
- Run full dev environment (port 3000 & 5001): `npm run dev`
- Run backend only: `npm run backend` (or `cd backend && uv run python run.py`)
- Run frontend only: `npm run frontend` (or `cd frontend && npm run dev`)
- Build frontend: `npm run build`
- Docker deploy: `docker compose up -d`

## Conventions
- Backend code follows standard Flask service patterns with snake_case naming.
- Frontend uses Vue 3 Composition API with `<script setup>`, ES modules, and D3 graph visualizations.
```python
# Backend service convention
class SimulationManager:
    def execute_round(self, round_idx: int) -> dict[str, Any]:
        return {"round": round_idx, "status": "completed"}
```

## Boundaries
- **NEVER** commit live `.env` files or hardcode API keys/tokens.
- **NEVER** expose unauthenticated admin or simulation mutation endpoints to public networks.
- **ALWAYS** sanitize file uploads before passing to PyMuPDF and text extractors.
- **IMPORTANT**: Simulation round loops consume significant LLM tokens; guard max rounds explicitly.

## Dependencies
- `camel-oasis` / `camel-ai`: Multi-agent social media simulation framework.
- `zep-cloud`: Graph memory and temporal knowledge graph engine.
- `vue` / `vite` / `d3`: Reactive frontend UI and interactive swarm network visualization.
- `flask` / `flask-cors`: REST API communication between UI and simulation runner.

## Config
Copy `.env.example` to `.env`:
- `LLM_API_KEY`: `<YOUR_LLM_API_KEY>`
- `LLM_BASE_URL`: `<YOUR_OPENAI_COMPATIBLE_BASE_URL>` (e.g. DashScope, 9Router, DeepSeek)
- `LLM_MODEL_NAME`: `<MODEL_IDENTIFIER>` (e.g. `qwen-plus`)
- `ZEP_API_KEY`: `<YOUR_ZEP_CLOUD_API_KEY>`

## Error Handling
- LLM timeouts and quota exhaustion are logged to backend stderr; wrap runner calls with exponential retries.
- Zep Cloud rate limits return HTTP 429; fail gracefully to cached graph snapshots where available.

## Troubleshooting
- Missing Python dependencies: run `cd backend && uv sync` to recreate the virtual environment.
- Port conflict on 5001 or 3000: check running processes via `ss -tulpn | grep -E '3000|5001'`.
- Simulation hang on step 2: verify `ZEP_API_KEY` validity and network connectivity to Zep Cloud.
