# Examen OSCP

[← Phase 6](phase-6-simulations.md) · [Plan](plan-oscp.md)

**Format :** action → ressource → timeboxing → **focus lecture (examen × ton niveau)**

---

## Objectif

Score suffisant **et** rapport accepté.

---

## Lectures Jour J — ciblées, pas encyclopédiques

### La veille / le matin

| Doc | Timeboxing | Focus examen — lire vraiment | Vu ton niveau — skip |
| --- | --- | --- | --- |
| [OSCP+ Exam Guide](https://help.offsec.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide) | **60–90 min** veille + **20 min** matin | Requirements, preuves, restrictions outils, proctoring, soumission | Tout le reste déjà annoté en Phase 5/6 |
| [OSCP+ Exam FAQ](https://help.offsec.com/hc/en-us/articles/4412170923924-OSCP-Exam-FAQ) | **30–45 min** veille | Scénarios de points ; AD vs standalones ; ressources autorisées | FAQ logistique déjà validée au dry-run |
| [Reporting Requirements](https://help.offsec.com/hc/en-us/articles/360046787731-PEN-200-Reporting-Requirements) | **45 min** veille | Screenshots, reproductibilité, délai upload, template | Style rédaction long |

**Livrable lecture :** ta checklist 1 page (autorisé / interdit / preuves / timeboxing) — plus aucun onglet doc pendant le rush sauf doute précis.

---

## Avant connexion lab

| Objectif | Timeboxing | Focus |
| --- | --- | --- |
| Sommeil | — | Pas de « dernière machine » jusqu'à 2 h |
| Kali + VPN dry-run | **30–45 min** veille | Opérationnel, pas lecture |
| Notes + template + plan timeboxing | **15–25 min** | Ouverts et prêts |

---

## Pendant les 24 h

| Fenêtre | Objectif | Secours autorisé | Timeboxing | Focus profil Mato |
| --- | --- | --- | --- | --- |
| 0:00–0:30 | Scans toutes cibles | Notes nmap | **30 min** | Ne pas over-engineer les scans |
| 0:30–2:00 | Triage + **AD early** | Notes AD Phase 3 | **90 min** | AD = gros points — ne pas le laisser pour la fin |
| 2:00–8:00 | Footholds | Notes enum/web | Blocs **90–120 min** | Web Java-like : enum app avant exploit public |
| 8:00–14:00 | Priv-esc + AD paths | Notes priv-esc / BloodHound | Blocs **90–120 min** | Windows priv-esc : suivre checklist, pas l'inspiration |
| 14:00–18:00 | Points restants | Control panel | **4 h** | Sécuriser partial points |
| 18:00–22:00 | Preuves IP+flags | Reporting Requirements (rappel) | **4 h** | Captures pendant que le shell vit |
| 22:00–24:00 | Rapport | Template OffSec | **2 h** | Stop hacking « espoir » |

**Switch :** > 90–120 min sans progrès → autre machine.  
**Outils :** strictement Exam Guide du jour J.

---

## Après les 24 h — rapport

| Objectif | Ressource | Timeboxing | Focus lecture | Vu ton niveau |
| --- | --- | --- | --- | --- |
| PDF reproductible | Reporting Requirements + template | Délai officiel post-exam (**confirmer** Guide) | Chaque étape rejouable | Structure > prose |
| Preuves flags + IP | Exam Guide proof files | **60–90 min** pass | local.txt/proof.txt + `ip a`/`ipconfig` | — |
| Upload final | Panel + instructions | **30–45 min** fin | Nommage/compression si exigés | Ne pas finir à la dernière minute |

### Contenu minimal par machine

1. Identification · 2. Enum pertinente · 3. Vecteur d'entrée · 4. User · 5. Priv-esc · 6. Root/SYSTEM · 7. Pivots/creds utiles

---

## Si échec

| Objectif | Ressource | Timeboxing | Focus |
| --- | --- | --- | --- |
| Rétro points vs rapport | Feedback OffSec | **2–3 h** | Identifier le vrai frein |
| Correctif | Phases 2 / 3 / 6 | **15–40 h** | Souvent AD, Windows priv-esc, ou rapport |
| Simu corrective | PG / challenges | **1× 24 h** min | Avant re-attempt |

---

## Après réussite

| Objectif | Timeboxing | Note |
| --- | --- | --- |
| Valoriser OSCP sur CV | **1–2 h** | Dépôt `cv/` |
| Suite OSEP / cloud pentest | Plus tard | Hors scope immédiat |

---

## Navigation

| Étape | Page |
| --- | --- |
| Index | [Plan OSCP](plan-oscp.md) |
| Phase 0 | [Fondations](phase-0-fondations.md) |
| Phase 1 | [Enumeration](phase-1-enumeration.md) |
| Phase 2 | [Privilege escalation](phase-2-privilege-escalation.md) |
| Phase 3 | [Active Directory](phase-3-active-directory.md) |
| Phase 4 | [Buffer overflows](phase-4-buffer-overflows.md) |
| Phase 5 | [PEN-200](phase-5-pen-200.md) |
| Phase 6 | [Simulations](phase-6-simulations.md) |
| Examen | **Cette page** |
