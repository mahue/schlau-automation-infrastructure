# Huener.net – Infrastructure Overview

## 1. Production Server
### Domain: Huener.net
### Internal Hostname: huener.net-main (Hetzner)
### IP: 159.69.156.6

#### Role
Primary production server for Huener.net  
Hosts all internal, stable, business-critical services.

#### Hosted Services
| Service | URL |
|--------|-----|
| Odoo Production | https://odoo.huener.net |
| Rocket.Chat Production | https://rocketchat.huener.net |
| n8n Production | https://n8n.huener.net |
| paperclip Production | https://paperclip.huener.net |
| supabase Production | https://supabase.huener.net |
| API Production | https://api.huener.net |

#### Notes
- This server hosts only internal infrastructure.  
- No customer playgrounds or test systems.  

---

## 2. Huener.net Playground Server
### Domain: huener.cloud
### Server Name: (Netcup)
### IP: 159.195.27.238

#### Hosted Services
| Service | URL |
|--------|-----|
| paperclip playground | https://paperclip.huener.cloud |

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

---

## 4. OLD Playground Server

### !! TO BE DELETED !!

### Public Domain: schlau-playground.de
### Internal Hostname: schlau.d3.net (Hetzner)
### IP: 49.12.229.72

---

