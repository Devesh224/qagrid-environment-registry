# Environment Registry Service

Owns the environments table and exposes /api/v1/environments. It has no dependency on Scheduler. Its separate repository should contain this folder's files only.

Set DATABASE_URL to a PostgreSQL URL. On Windows, copy .env.example values into your PowerShell session:

    $env:DATABASE_URL = "postgresql+psycopg://YOUR_DB_USER:YOUR_DB_PASSWORD@localhost:5433/registry"
    py -3.12 -m venv .venv
    .\.venv\Scripts\python.exe -m pip install -r requirements.txt
    .\.venv\Scripts\python.exe -m uvicorn app.main:app --reload --port 8001

Start a PostgreSQL database initialized with db/schema.sql before launching. The root compose.yaml does this automatically. Run unit tests from this folder:

    .\.venv\Scripts\python.exe -m pytest tests -q

Database changes should be made in this service repository. The schema.sql file is an initialization script for new databases, not an upgrade migration.
