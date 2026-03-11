# OpenClaw Web Gateway

![Python](https://img.shields.io/badge/python-3.10+-blue)
![Flask](https://img.shields.io/badge/flask-web--gateway-black)
![License](https://img.shields.io/badge/license-MIT-green)


A cleaned and reusable Flask-based web interface for OpenClaw.

This version removes personal data from the repository, moves local settings into configuration files, and keeps the project ready for GitHub.

## Features

- Multi-user chat UI with per-user conversation history
- OpenClaw HTTP integration
- Lightweight local persistence for UI state
- Simple persistent memory helper for household facts
- Optional embedded Google Maps route and search windows
- Configuration through `.env` and `config/participants.json`

## Repository layout

```text
openclaw-web-gateway/
├── app.py
├── config.py
├── memory_store.py
├── openclaw_client.py
├── prompts.py
├── requirements.txt
├── run.sh
├── .env.example
├── config/
│   ├── participants.example.json
│   └── participants.json
├── routes/
│   ├── chat.py
│   └── state.py
├── static/
│   ├── css/app.css
│   └── js/
├── templates/
│   └── index.html
└── README.md
```

## Quick start

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd openclaw-web-gateway
```

### 2. Create a virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
deactivate
```

### 3. Create your local configuration

```bash
cp .env.example .env
cp config/participants.example.json config/participants.json
```

Edit `.env` and set at least:

- `OPENCLAW_BASE_URL`
- `OPENCLAW_TOKEN` if your gateway requires it
- `DEFAULT_USER`
- `GOOGLE_MAPS_EMBED_API_KEY` if you want embedded maps

Edit `config/participants.json` to define your users.

Example:

```json
[
  {
    "key": "alex",
    "display_name": "Alex",
    "aliases": ["alex", "a"]
  },
  {
    "key": "sam",
    "display_name": "Sam",
    "aliases": ["sam", "s"]
  },
  {
    "key": "pedro",
    "display_name": "Pedro",
    "aliases": ["Pedro", "p"]
  }
]
```

### 4. Run the app

```bash
./run.sh
```

Or:

```bash
python app.py
```

Then open:

```text
http://127.0.0.1:5002
```

## Configuration

### `.env`

| Variable | Description | Default |
|---|---|---|
| `APP_TITLE` | UI title | `OpenClaw Web Gateway` |
| `APP_SUBTITLE` | UI subtitle | `Local chat UI for OpenClaw` |
| `HOST` | Flask bind address | `0.0.0.0` |
| `PORT` | Flask port | `5002` |
| `OPENCLAW_BASE_URL` | OpenClaw base URL | `http://127.0.0.1:18789` |
| `OPENCLAW_TOKEN` | Bearer token for OpenClaw | empty |
| `OPENCLAW_MODEL` | OpenClaw model name | `default` |
| `OPENCLAW_CHANNEL` | Message channel header | `web-gateway` |
| `GOOGLE_MAPS_EMBED_API_KEY` | Optional Google Maps Embed key | empty |
| `STATE_FILE` | Local UI state file | `./gateway_state.json` |
| `MEMORY_ROOT` | Persistent memory directory | `~/.openclaw/memory` |
| `PARTICIPANTS_FILE` | Participants JSON file | `./config/participants.json` |
| `DEFAULT_USER` | Default active participant | first configured user |

## Notes

- `.env` is ignored by Git.
- `config/participants.json` is ignored by Git.
- `gateway_state.json` is ignored by Git.
- The included memory helper writes to the same memory root used by OpenClaw by default. Change `MEMORY_ROOT` if you want complete isolation.

## Suggested next improvements

- Add authentication in front of the Flask app
- Replace local JSON state with a small database if needed
- Add tests for route extraction and memory parsing
- Make the UI theme selectable

## License

Add your preferred license before publishing.
