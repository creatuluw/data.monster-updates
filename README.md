# data.monster-updates

Public update feed and download home for the [Data Monster](https://github.com/creatuluw/data.monster) desktop app (private repo).

Installed apps check `releases/latest/download/latest.json` for new versions. Releases hold the signed installers + the update feed. No source code lives here.

## Install

1. **Download** the newest `Data.Monster_x.y.z_x64-setup.exe` from [the latest release](https://github.com/creatuluw/data.monster-updates/releases/latest).
2. **Run it** — a standard Windows 10/11 installer. Then launch **Data Monster**.
3. **Create a workspace** on first launch: pick an empty folder — your DuckDB database, ingested data, and all app content live there as plain files. The folder is portable: move it, back it up, switch workspaces any time.
4. **Connect data**: drop CSV / Parquet / JSON files onto the Connect page, or connect a PostgreSQL database and ingest tables.

## Set up the LLM (AI features)

AI features — the **Agent-P chat** (built-in coding agent), **analyst chat**, **metadata scans**, **wiki writing**, and the **data concierge** — need one OpenAI-compatible LLM endpoint.

**Option A — LLM settings (recommended)**

1. Open **Settings → LLM**.
2. Add a profile: **Name**, **API URL** (a `…/chat/completions` endpoint), **API key**, and a **model id**. Works with z.ai, DeepSeek, Moonshot, OpenRouter, Together, or any OpenAI-compatible provider.
3. Set the profile as the app default, then pick per-surface models where you want a different one (Agent-P, analyst, …).

**Option B — pi.dev (Agent-P's engine)**

Agent-P runs on [pi](https://pi.dev), a coding agent that lives on your machine:

1. Go to **Settings → LLM → Agents**.
2. Click **Install pi** — needs Node.js ≥ 22.19 on the machine. The app installs it globally via npm.
3. Click **Configure pi** — the app hands your Global LLM settings to pi, so it works without a separate login. You can also install pi.dev yourself and use its own `/login`; the app picks up pi's configured provider for Agent-P.

**How the app resolves an LLM**: Settings → LLM profile first, then `LLM_API_URL` / `LLM_API_KEY` / `LLM_API_MODEL` in the workspace `.env`, then pi's own config. If a feature needs an LLM and none is configured, a setup modal walks you through it.

## Updates

The app silently checks this feed after startup — never at launch. When a new version is published you get a changelog toast, and install is one click in **Settings → Updates**. Updates are always user-gated.
