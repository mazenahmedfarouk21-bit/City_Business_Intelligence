# City_Business_Intelligence
Containerized data pipeline (Python 3.13 + Docker) that extracts, cleans, and loads data into a shared Supabase (PostgreSQL) database.

An ETL pipeline that **extracts** raw data, **cleans** it, and **loads** it into a shared
**Supabase (PostgreSQL)** database so the whole team can query a single source of truth.
The pipeline runs inside **Docker** for consistent environments across machines.

## Architecture

```
Source (API / Web) ──► Extract ──► Clean / Transform ──► Load ──► Supabase (PostgreSQL)
                         └──────────── Docker container ────────────┘
```

## Tech Stack

- Python 3.13
- Docker & Docker Compose
- Supabase (PostgreSQL)
- <pandas / requests / BeautifulSoup / ... >

## Project Structure

```
.
├── src/
│   ├── extract.py        # data collection
│   ├── clean.py          # cleaning & transformation
│   ├── load.py           # load into Supabase
│   └── main.py           # pipeline entry point
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

## Getting Started

### Prerequisites
- Docker Desktop
- A Supabase project (get the connection details from Project Settings → Database)

### 1. Clone the repo
```bash
git clone https://github.com/<username>/<repo>.git
cd <repo>
```

### 2. Configure environment variables
```bash
cp .env.example .env
```
Then fill in your values:
```
SUPABASE_URL=
SUPABASE_KEY=
DATABASE_URL=
```
> Never commit `.env` to Git.

### 3. Build and run
```bash
docker compose build
docker compose up
```

### Run locally (without Docker)
```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python src/main.py
```

## Database

Data is stored in Supabase. Main tables:

| Table | Description |
|-------|-------------|
| `<table_1>` | <description> |
| `<table_2>` | <description> |

## Team Workflow

1. Create a feature branch: `git checkout -b feature/<name>`
2. Commit and push your changes
3. Open a Pull Request for review

## Roadmap

- [ ] Scheduling (cron / GitHub Actions)
- [ ] Logging & error handling
- [ ] Data validation tests
- [ ] CI/CD

## License

<MIT / Private>
