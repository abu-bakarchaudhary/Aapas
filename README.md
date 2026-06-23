# Aapas — Neighbourhood Mutual Aid Platform

Aapas is a single-page web application where community members share skills and resources — for free. No money ever changes hands.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Python 3 + Flask |
| **Frontend** | Vanilla HTML/CSS/JS (single-page) |
| **Storage** | Excel (.xlsx) via openpyxl |
| **API Style** | REST (JSON) |

## Project Structure

```
aapas/
├── excel_api.py          # Flask API server (4 endpoints)
├── website.html          # Single-page frontend (~1600 lines)
├── requirements.txt      # Python dependencies
├── data/
│   ├── .gitkeep
│   └── user_records.xlsx # Auto-created on first run
└── README.md
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/save-signup` | Register a new member |
| POST | `/api/save-login` | Record a login attempt |
| POST | `/api/save-post` | Create an offer/request listing |
| POST | `/api/save-report` | Submit a community report |

## How to Run on Your Machine

1. **Clone the repo**
   ```bash
   git clone https://github.com/abu-bakarchaudhary/Aapas.git
   cd Aapas
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   venv\Scripts\activate    # Windows
   source venv/bin/activate # macOS/Linux
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Start the API server**
   ```bash
   python excel_api.py
   ```
   The server starts at `http://127.0.0.1:5000`. The Excel file is created automatically in `data/`.

5. **Open the frontend**
   Open `website.html` in a browser. No build step needed — it's pure HTML/JS.

6. **Login**
   Use your email address to log in. If your email name matches a demo member, you'll log in as that member; otherwise, a new profile is created on the fly.

## Features

- Browse offers and requests from neighbours
- Post new listings (skills/items/resources you offer or need)
- View member profiles with their exchanges and listings
- Personal dashboard showing your active exchanges
- Community guidelines and safety page
- Report system for issues
- All data persisted to Excel via the API

## Design Notes

- The frontend renders listing cards and profile data from a hardcoded `MEMBERS` array for demo purposes. In production, replace this with data fetched from an API.
- Password validation is enforced client-side (minimum 4 characters). The backend records login attempts but does not store passwords — this is a trust-based community platform.
- Barter exchanges are tracked in-memory via `EXCHANGES` array and rendered on the dashboard.
