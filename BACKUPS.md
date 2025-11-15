# Backup Strategy – schlau AUTOMATION Infrastructure

---

## 1. Production Server (huener.net-main)

### Scope
- Odoo Production
- Rocket.Chat Production
- n8n Production
- Wekan Production
- XcaliDraw Production

### Policy
- Full daily backup
- Weekly retention
- Storage: Hetzner StorageBox
- Tool: Restic (recommended, final decision with Arc)

---

## 2. Playground Server (schlau.d3.net)

### Scope
- All playground Odoo instances
- Each playground database
- Each playground configuration set

### Policy
- Daily backup
- Retention: 3 days
- Storage: Hetzner StorageBox
- Tool: Restic

### Why short retention?
- Playgrounds are test environments
- Customers can break their instances
- Lightweight safety net is sufficient

---

## 3. LieferApp Server (IONOS)

### Policy
- Daily backup
- 7-day ring retention
- Managed directly on IONOS

