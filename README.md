OpenClaw Web Gateway

[Python] [Flask] [License]

Interface

[Jarvis UI]

A clean and reusable Flask-based web interface for OpenClaw.

This version removes personal data from the repository, moves local
settings into configuration files, and keeps the project ready for
GitHub.

Features

-   Multi-user chat UI with per-user conversation history
-   OpenClaw HTTP integration
-   Lightweight local persistence for UI state
-   Simple persistent memory helper for household facts
-   Optional embedded Google Maps route and search windows
-   Configuration through .env and config/participants.json

Repository layout

openclaw-web-gateway/ ├── app.py ├── config.py ├── memory_store.py ├──
openclaw_client.py ├── prompts.py ├── requirements.txt ├── run.sh ├──
.env.example ├── config/ │ ├── participants.example.json ├── routes/ │
├── chat.py │ └── state.py ├── static/ │ ├── css/app.css │ └── js/ ├──
templates/ │ └── index.html ├── screenshots/ │ └── jarvis-ui.png └──
README.md

Quick start

1.  Clone the repository

git clone https://github.com/jeanne0r/openclaw-web-gateway.git cd
openclaw-web-gateway

2.  Create a virtual environment

python3 -m venv .venv source .venv/bin/activate pip install -r
requirements.txt

3.  Create your local configuration

cp .env.example .env cp config/participants.example.json
config/participants.json

Edit .env and set at least:

-   OPENCLAW_BASE_URL
-   OPENCLAW_TOKEN if your gateway requires it
-   DEFAULT_USER
-   GOOGLE_MAPS_EMBED_API_KEY if you want embedded maps

Edit config/participants.json to define your users.

4.  Run the app

./run.sh

or

python app.py

Then open:

http://127.0.0.1:5002

License

MIT License © 2026 Romain Jeanneret See the LICENSE file for details.
