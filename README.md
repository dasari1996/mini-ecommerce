# Mini E‑Commerce (Polished UI) — Django REST + React + Tailwind (SQLite)

A clean, modern e‑commerce sample with:
- **Backend:** Django 5, DRF, SimpleJWT, Celery (emails), SQLite DB (no Postgres).
- **Frontend:** React + Vite + Tailwind + shadcn‑style UI + lucide icons.
- **Features:** JWT auth, products, categories, cart, checkout, order history, admin CRUD, PDF receipts, optional Stripe.
- **Docker:** No database container required; SQLite file lives inside `backend/`.

## Quick Start (No Docker)

### Backend
```bash
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r backend/requirements.txt
cp backend/.env.example backend/.env
cd backend
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```
Backend: http://localhost:8000

### Frontend
```bash
cd frontend
npm install
npm run dev
```
Frontend: http://localhost:5173

Set `VITE_API_URL` in `.env` (default `http://localhost:8000/api`).

## Docker
```bash
cp backend/.env.example backend/.env
docker compose up --build
```
Services:
- API: http://localhost:8000
- Frontend: http://localhost:5173
- Redis (for Celery): port 6379

## Test (basic API)
```bash
cd backend
pytest -q
```

## Notes
- Admin write access: categories + products. Product owner also can edit/delete their own products.
- Checkout uses **mock** provider unless Stripe keys exist in `.env`.
- PDF receipt: `GET /api/orders/{id}/receipt/`.
