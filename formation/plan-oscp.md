# Plan de formation OSCP — Souleymane Harouna Mato

Plan personnalisé à partir du CV (Lead Dev Java/Spring, Master 2 Transmission de données et sécurité de l'information, LPIC-1/2, AWS Developer Associate, expérience DevSecOps bancaire).

**Objectif :** réussir l'examen Offensive Security Certified Professional (PEN-200 / OSCP).

**Comptes déjà disponibles :** **TryHackMe Premium** — paths, rooms Premium et labs guidés accessibles sans friction pour les phases 0–4 (prioriser THM avant d'acheter d'autres abonnements).

**Positionnement :** profil **avancé en fondations** (Linux, réseaux, sécu applicative défensive, cloud), **débutant/intermédiaire en offensive**. Le plan accélère les bases déjà maîtrisées et concentre l'effort sur la méthodologie d'attaque, l'Active Directory, l'élévation de privilèges et la pratique sous contrainte de temps.

---

## Parcours (une page par étape)

| Étape | Page |
| --- | --- |
| Phase 0 | [Fondations offensives accélérées](phase-0-fondations.md) |
| Phase 1 | [Enumeration & exploitation manuelle](phase-1-enumeration.md) |
| Phase 2 | [Privilege escalation Linux/Windows](phase-2-privilege-escalation.md) |
| Phase 3 | [Active Directory (cœur du gap)](phase-3-active-directory.md) |
| Phase 4 | [Buffer overflows & client-side](phase-4-buffer-overflows.md) |
| Phase 5 | [PEN-200 OffSec + labs officiels](phase-5-pen-200.md) |
| Phase 6 | [Simulations d'examen + rapport](phase-6-simulations.md) |
| Examen | [Examen OSCP](examen-oscp.md) |

```text
Phase 0 → Phase 1 → Phase 2 → Phase 3 → Phase 4 → Phase 5 → Phase 6 → Examen OSCP
```

**Règle d'or pour ton profil :** ne pas refaire un cours Linux complet. Transformer la connaissance sysadmin/dev en **réflexes d'attaquant**.

**Convention de chaque page de phase :** pour chaque objectif → **1) ressource** → **2) timeboxing** → **3) focus lecture** (parties à lire vraiment pour l'examen × ce que tu peux accélérer vu LPIC / Master sécu / Lead Java).

---

## Diagnostic à partir du CV

### Atouts à capitaliser

| Domaine | Preuve CV | Impact OSCP |
| --- | --- | --- |
| Linux avancé | LPIC-1, LPIC-2 | Accélération forte sur shell, services, privilege escalation Linux |
| Fondations sécurité | Master 2 Sécurité de l'information | Accélération sur crypto, réseaux, concepts sécu |
| Compréhension applicative | 10+ ans Java/Spring, Spring Security, Keycloak | Avantage net sur web apps, auth, JWT/OAuth |
| Ops / diagnostic | Rôle Ops Atos (recette → prod) | Transfert utile vers enumeration & priv-esc |
| Scripting | Python, SQL, TypeScript | Capacité à écrire des helpers / payloads rapidement |
| DevSecOps | Snyk, pratiques DevSecOps BNC | Connaissance des failles — à **retourner** en mode attaquant |

### Écarts à combler (priorité haute)

1. **Méthodologie offensive** (recon → enum → exploit → pivot → report)
2. **Active Directory** (Kerberos, BloodHound, ACL, lateral movement)
3. **Privilege escalation Windows**
4. **Buffer overflows**
5. **Pratique CTF / labs** sous contrainte
6. **Rédaction de rapport** style OffSec
7. **Discipline « no automated scanners »**

### Ce qu'il ne faut pas surinvestir

- Kubernetes / AWS / microservices : utiles en carrière, **peu centraux** à l'examen OSCP.
- Outils purement DevSecOps (Snyk, SCA) : garder le réflexe « quelle faille exploitable ? ».

---

## Rythme indicatif

- Intensité soutenable (Lead Dev) : **10–15 h / semaine**
- Intensité accélérée : **25–35 h / semaine**
- Volume total estimé : **environ 350–450 h** de pratique utile

---

## Environnement de travail (dès le jour 1)

### Lab local

- Machine attaquante : **Kali Linux** (VM) ou équivalent
- Hyperviseur : VirtualBox ou VMware
- Snapshots avant chaque lab sensible
- VM Windows 10/11 + Windows Server (AD) pour les labs plus tard

### Plateformes

| Plateforme | Usage | Priorité |
| --- | --- | --- |
| **TryHackMe Premium** *(compte déjà actif)* | Montée guidée, paths, rooms Premium | Phase 0–4 (socle) |
| Hack The Box | Enumeration réelle, machines Easy/Medium | Phase 1–4 |
| Proving Grounds Practice | Style proche OSCP | Phase 4–6 |
| PEN-200 (OffSec) | Cours + labs officiels | Phase 5 |
| Notes Git / Obsidian | Cheatsheets perso | Continu |

### Structure de notes

```text
notes/
  methodology/
  enumeration/
  linux-privesc/
  windows-privesc/
  active-directory/
  web/
  buffer-overflow/
  machines/
    YYYY-MM-DD-nom-machine.md
  report-templates/
```

---

## Semaine type (~12 h)

| Créneau | Activité |
| --- | --- |
| 2 soirées × 2 h | Théorie courte + lab guidé (**THM Premium**) |
| 1 soirée × 2 h | Machine HTB/PG sans writeup |
| Samedi 4 h | Deep work (priv-esc ou AD) |
| Dimanche 2 h | Notes, cheatsheets, dead ends |

---

## Matrice CV → OSCP

| Compétence CV | Module OSCP | Action |
| --- | --- | --- |
| LPIC-1/2 | Linux enum / priv-esc | Accélérer |
| Master 2 sécu | Networking, crypto | Skip intro ; focus offensive |
| Java / Spring Security | Web attacks, auth | Attaquer ce que tu sécurises |
| Python | Tooling / exploits | Écrire tes helpers |
| Docker / K8s / AWS | Hors cœur OSCP | Limiter aux misconfigs Docker |
| Snyk / DevSecOps | Mindset | Convertir findings en exploits |
| Ops Atos | Troubleshooting | Réutiliser pour l'enumeration |

---

## Budget pédagogique

| Élément | Notes |
| --- | --- |
| **TryHackMe Premium** | **Déjà en place** — exploiter paths/rooms Premium en phases 0–4 |
| Hack The Box (VIP) | Utile phases 1–4 (à prévoir si pas encore abonné) |
| PEN-200 | Indispensable |
| Proving Grounds Practice | Fortement recommandé |
| Matériel | RAM ≥ 16 Go (32 Go confort AD) |

---

## Indicateurs globaux

| Indicateur | Cible avant examen |
| --- | --- |
| Machines Easy documentées | ≥ 30 |
| Machines Medium documentées | ≥ 15 |
| Escalades Windows | ≥ 15 |
| Chemins AD complets | ≥ 5 |
| Buffer overflows from scratch | ≥ 3 |
| Simulations 24 h | ≥ 2 |

**Commencer ici →** [Phase 0 — Fondations offensives accélérées](phase-0-fondations.md)
