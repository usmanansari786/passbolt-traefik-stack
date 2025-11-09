# Passbolt + Traefik + MariaDB Deployment Stack

This is a self-hosted password manager stack deployed via Portainer, secured through HTTPS using Traefik with customizable external ports routed via an ASUS router.

---

## Stack Components

| Service    | Description                                  |
|------------|----------------------------------------------|
| `passbolt` | Secure team password manager                 |
| `mariadb`  | Database backend for Passbolt                |
| `traefik`  | Reverse proxy + Let's Encrypt SSL termination |

---

## Access URLs

Port forwarding is configured as:

- `https://passbolt.rage00786.com:2443` → routes to Traefik’s internal port 443
- `http://passbolt.rage00786.com:2080` → routes to Traefik’s internal port 80

DNS must resolve to your public IP, with Cloudflare proxy **disabled** unless tunneling is used.

---

## Deployed via Portainer Stacks

This stack uses Portainer’s GUI-based deployment method instead of CLI Docker Compose.

> Be sure to include:
> - Traefik labels specifying the service (`traefik.http.routers.passbolt.service=passbolt`)
> - Correct APP URL with port in `APP_FULL_BASE_URL`
> - `traefik.enable=false` for containers not meant to be routed

---

## Quick Setup Reference

```yaml
environment:
  APP_FULL_BASE_URL: https://passbolt.rage00786.com:2443




Router NAT rules:
| External Port | Internal IP | Internal Port | 
| 2443 | 192.168.1.74 | 443 | 
| 2080 | 192.168.1.74 | 80 | 


Ready for Expansion
Future containers can be layered easily:
- Just assign a unique subdomain (e.g. grafana.rage00786.com)
- Route via Traefik labels + entrypoints
- Define NAT rules for external port translation

Admin Provisioning
Passbolt user setup via CLI:
cake passbolt register_user -u your@email.com -f First -l Last -r admin


If account exists:
cake passbolt recover_user --username your@email.com


Ready for Expansion
Future containers can be layered easily:
- Just assign a unique subdomain (e.g. grafana.rage00786.com)
- Route via Traefik labels + entrypoints
- Define NAT rules for external port translation



Admin Provisioning
Passbolt user setup via CLI:


cake passbolt register_user -u your@email.com -f First -l Last -r admin

If account exists:

cake passbolt recover_user --username your@email.com
---

Ready for Expansion
Future containers can be layered easily:
- Just assign a unique subdomain (e.g. grafana.rage00786.com)
- Route via Traefik labels + entrypoints
- Define NAT rules for external port translation

Admin Provisioning
Passbolt user setup via CLI:
cake passbolt register_user -u your@email.com -f First -l Last -r admin


If account exists:
cake passbolt recover_user --username your@email.com



Maintainer
Usman Ansari
GitHub: @usmanansari786

License
This repository reflects a secure and modular deployment pattern for private infrastructure. Use at your discretion.



