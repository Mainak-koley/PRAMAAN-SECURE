# PRAMAAN Backend — README
## SIH PS 26190 | Secure Digital Evidence Management System

## Quick Start

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Set up PostgreSQL database
Create a database named `pramaan_db` in PostgreSQL:
```sql
CREATE DATABASE pramaan_db;
```

### 3. Configure environment
Copy `.env.example` to `.env` and update credentials:
```bash
copy .env.example .env
```
Edit `.env` with your PostgreSQL password.

### 4. Run migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Seed demo users
```bash
python manage.py seed_demo
```

### 6. Start the server
```bash
python manage.py runserver
```

Server runs at: http://127.0.0.1:8000

---

## Demo Credentials

| Role  | Username           | Password    |
|-------|--------------------|-------------|
| ADMIN | admin              | Admin@1234  |
| IO    | inspector_sharma   | IO@12345    |
| COURT | court_user         | Court@1234  |

---

## API Endpoints

### Auth
| Method | URL | Description |
|--------|-----|-------------|
| POST | /api/v1/auth/login/ | Login → JWT token |
| POST | /api/v1/auth/refresh/ | Refresh access token |
| POST | /api/v1/auth/logout/ | Blacklist refresh token |
| POST | /api/v1/auth/register/ | Create user (ADMIN only) |
| GET | /api/v1/auth/profile/ | Current user profile |
| GET | /api/v1/auth/users/ | List all users (ADMIN) |

### Documents
| Method | URL | Description |
|--------|-----|-------------|
| POST | /api/v1/documents/upload/ | Upload + auto SHA-256 hash |
| GET | /api/v1/documents/ | List all documents |
| GET | /api/v1/documents/{id}/ | Document detail |
| GET | /api/v1/documents/{id}/download/ | Download file |
| DELETE | /api/v1/documents/{id}/ | Delete (ADMIN) |

### Verification
| Method | URL | Description |
|--------|-----|-------------|
| POST | /api/v1/verification/{doc_id}/verify/ | Tamper check |
| GET | /api/v1/verification/ | All verification results |
| GET | /api/v1/verification/{id}/ | Single result |

### Audit
| Method | URL | Description |
|--------|-----|-------------|
| GET | /api/v1/audit/ | Audit logs (filterable) |
| GET | /api/v1/audit/stats/ | Summary stats |
| GET | /api/v1/audit/{id}/ | Single log entry |

---

## Demo Flow (for video)
```bash
python demo_flow.py
```

Steps:
1. Login as IO (Inspector Sharma)
2. Upload FIR document → SHA-256 computed + stored
3. List documents → hash visible
4. Verify → ✅ VERIFIED (hashes match)
5. File tampered (bytes modified on disk)
6. Verify again → 🚨 TAMPERED (hash mismatch)
7. View audit logs → all actions logged with timestamps

---

## Tech Stack
- **Backend**: Python 3.13 + Django 5.2
- **API**: Django REST Framework 3.16
- **Auth**: JWT via SimpleJWT
- **Database**: PostgreSQL
- **Hashing**: Python hashlib — SHA-256
- **Storage**: Local filesystem (media/)
- **CORS**: django-cors-headers
