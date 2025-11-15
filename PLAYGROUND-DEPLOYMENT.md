# Playground Deployment Guide (schlau-playground.de)

This document defines the automated deployment process for isolated Odoo playground instances on the server `schlau.d3.net`.

---

## 1. Goal
Each customer receives a fully isolated Odoo sandbox instance with:
- Isolated Linux user
- Isolated Odoo instance
- Isolated PostgreSQL database & PG user
- Dedicated port
- Dedicated subdomain under `.schlau-playground.de`
- Dedicated NGINX site configuration
- `list_db = False` (no multi-DB access)
- Zero manual server interaction

---

## 2. Naming Conventions

### Linux User
```
pg_<username>
```

### Systemd Service
```
pgodoo-<username>.service
```

### Subdomain
```
https://<username>.schlau-playground.de
```

### Ports
Starting at **11000**, increment +1 for each new instance:
```
11000, 11001, 11002, ...
```

---

## 3. Required Components
- Ubuntu server (schlau.d3.net)
- Global NGINX reverse proxy
- PostgreSQL instance
- Odoo 19 base installation template
- Deployment script (to be implemented)
- StorageBox for backup via Restic

---

## 4. Deployment Steps (Automated)

1. Create Linux user `pg_<username>`.
2. Create directory structure:
   ```
   /home/pg_<username>/odoo/
   /home/pg_<username>/logs/
   ```
3. Create PostgreSQL DB + user:
   ```
   db_<username>
   user_<username>
   ```
4. Generate Odoo config:
   - unique port
   - dedicated DB
   - list_db = False
5. Install systemd service `pgodoo-<username>.service`.
6. Enable & start service.
7. Generate NGINX site config:
   - SSL
   - Proxy to instance port
8. Reload NGINX.
9. Return URL to requester.

---

## 5. Internal Playground Example
```
URL: https://schlau-automation.schlau-playground.de
Linux User: pg_schlau-automation
Service: pgodoo-schlau-automation.service
Port: 11000
```

---

## 6. Isolation Rules
- No shared DBs  
- No shared configs  
- No shared service files  
- No cross-file access  
- One customer = one fully isolated environment

