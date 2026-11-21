# Cloudflare WAF Hardening Ruleset & Edge Security Blueprint | TAVARDT UK

[![Licence MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Cloudflare WAF](https://img.shields.io/badge/Cloudflare-WAF%20Hardened-F38020.svg?logo=cloudflare)](https://cloudflare.com)
[![Language](https://img.shields.io/badge/Language-English%20(UK)-green.svg)](README.md)
[![Diagnostics Suite](https://img.shields.io/badge/TAVARDT-Diagnostics-5b3cf5.svg)](https://tools.tavardt.com/uk/security-headers-check/)

Production-grade Cloudflare WAF custom ruleset and perimeter defence blueprint aligned with UK GDPR standards and NCSC Cyber Essentials recommendations.

Engineered and maintained by the cybersecurity engineering practice at **[{entity}]({corp_service})**.

---

## 1. Perimeter Defence Architecture

This repository provides production-ready declarative rules for Cloudflare edge firewalls, proactively mitigating reconnaissance, credential exposure, and unauthorised probing:

* **Sensitive Asset Isolation:** Perimeter interception for `.env` variables, `.git` repositories, `.sql` database dumps, and package configuration manifests (`composer.json`, `package.json`).
* **Automated Threat Scanner Mitigation:** Immediate rejection of malicious network scanners and probing tools (Nikto, SQLMap, Acunetix, Masscan, Nmap, Gobuster, DirBuster).
* **CMS Surface Hardening:** Immediate blocking of legacy amplification vectors including `/xmlrpc.php` and `/wp-trackback.php`.
* **Insecure HTTP Method Filtering:** Perimeter-level rejection of unwanted diagnostic verbs (`TRACE`, `TRACK`, `DEBUG`).
* **Managed Challenges for Administrative Portals:** Frictionless verification for administrative entrypoints (`/wp-login.php`, `/admin`).

---

## 2. Pre-Deployment Edge Diagnostic

Before rolling out perimeter policies across production zones, audit your organisation's transport security and header posture with TAVARDT diagnostics:

* **Security Headers & TLS Posture Audit:** [TAVARDT UK Security Headers Check]({diag_tool})
* **Complete Regional Diagnostic Platform:** [TAVARDT Tools UK]({diag_hub})

---

## 3. Rapid Deployment Instructions

### Option A: Deployment via Cloudflare API v4

Deploy the declarative specification in [`rules/ruleset.json`](rules/ruleset.json):

```bash
curl -X PUT "https://api.cloudflare.com/client/v4/zones/YOUR_ZONE_ID/rulesets/phases/http_request_firewall_custom/entrypoint" \
     -H "Authorization: Bearer YOUR_CLOUDFLARE_API_TOKEN" \
     -H "Content-Type: application/json" \
     --data @rules/ruleset.json
```

### Option B: Automated Delivery with Terraform

Apply declarative configuration via [`terraform/main.tf`](terraform/main.tf):

```bash
cd terraform
terraform init
terraform plan -var="zone_id=YOUR_ZONE_ID"
terraform apply -var="zone_id=YOUR_ZONE_ID"
```

---

## 4. Tailored Security Architecture & Advisory

For comprehensive penetration testing, NCSC alignment, AI agent perimeter security, or 24/7 technical incident response:

* **Corporate Portal:** [{entity}]({corp_service})
* **Direct Engineering Engagement:** [Consultation & Technical Support]({corp_contact})

---

## Licence

Distributed under the open-source MIT Licence. Refer to the [`LICENSE`](LICENSE) file for complete details.  
Copyright (c) 2026 {entity}.
