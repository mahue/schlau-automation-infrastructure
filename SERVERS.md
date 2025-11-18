# schlau AUTOMATION – Infrastructure Overview

## 1. Production Server
### Domain: schlau-automation.de
### Internal Hostname: huener.net-main (Hetzner)
### IP: 159.69.156.6 | 2a01:4f8:1c1a:133a::/64
### Database: schlau-automation

#### Role
Primary production server for the schlau AUTOMATION team.  
Hosts all internal, stable, business-critical services.

#### Public Domains
- schlau-automation.de  
- huener.net (mirrored domain)

#### Hosted Services
| Service | URL |
|--------|-----|
| Odoo Production | https://odoo.schlau-automation.de |
| Rocket.Chat Production | https://rocketchat.schlau-automation.de |
| n8n Production | https://n8n.schlau-automation.de |
| Wekan Production | https://wecan.schlau-automation.de |
| XcaliDraw Production | https://xcalidraw.schlau-automation.de |

#### Notes
- This server hosts only internal infrastructure.  
- No customer playgrounds or test systems.  
- huener.net must mirror all services 1:1.

---

## 2. Playground Server
### Public Domain: schlau-playground.de
### Internal Hostname: schlau.d3.net (Hetzner)
### IP: 49.12.229.72
### Instances:
1) schlau-automation.schlau-playground.de (our playground / sandbox)
2) energieausweis24.schlau-playground.de
3) r-industries.schlau-playground.de

#### Role
Dedicated sandbox server mostly for odoo test instances , client & internal playgrounds.

#### Playground Structure
Each isolated odoo instance is available under:
```
https://<username>.schlau-playground.de
```

Example internal sandbox:
```
https://schlau-automation.schlau-playground.de
```

#### Isolation Requirements
Each odoo playground instance must have:
- Dedicated Linux user: `pg_<username>`
- Dedicated systemd service: `pgodoo-<username>.service`
- Dedicated PostgreSQL database + PG user
- Dedicated port (starting at 11000, increment +1)
- Dedicated filesystem, configs, logs
- Database selector disabled (`list_db = False`)
- Odoo 19
- Reverse proxy via global NGINX with per-instance site config
- Zero manual server interaction during deployment

#### Notes
This server has a testing purpose and is isolated from the production infrastructure.

---

## 3. LieferApp Server
### Domain: lieferapp.app
### Server Name: lieferapp.app-01 (IONOS)
### IP: 212.132.99.56

#### Hosted Services
| Service | URL |
|--------|-----|
| LieferApp Backend/Frontend | https://lieferapp.app |
| Rocket.Chat (lieferapp/client team) | https://rocketchat.lieferapp.app |

#### Notes
This server is single-purpose and isolated from the automation infrastructure.

