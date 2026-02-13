# Clinic POS Backend (Thin Slice)

## Overview

This project is a minimal backend slice of a Clinic POS system.

Tech stack:
- .NET Web API
- PostgreSQL (Docker)
- EF Core

This version focuses on a single vertical slice:
→ Create Patient API connected to real database

---

## What is Implemented

###  Database
- PostgreSQL running in Docker
- Database connection configured via `appsettings.json`
- Patients table created via EF migration

###  Patient API

Endpoint:
POST /api/Patients

Example request:

{
  "firstName": "Somchai",
  "lastName": "Jaidee",
  "phone": "0812345678"
}

Response:
- 201 Created
- Returns created patient object with id

Verified via:
- curl
- Swagger
- Direct DB query via psql

---

## How to Run

### 1. Start PostgreSQL via Docker

docker run -d --name clinic-postgres \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=postgres \
  -e POSTGRES_DB=clinicdb \
  -p 5432:5432 postgres:16

### 2. Run API

dotnet run

API runs at:
http://localhost:5050

---

## Database Verification

Connect:

docker exec -it clinic-postgres psql -U postgres -d clinicdb

Check tables:

\dt

---

## Design Notes

- Simple CRUD structure
- Direct EF Core integration
- No authentication yet
- No multi-tenant enforcement yet
- Focused on working database-backed API slice

---

## Next Steps (Planned)

- Add TenantId to Patient
- Add tenant isolation
- Add validation
- Add role-based authorization
- Introduce Redis and RabbitMQ