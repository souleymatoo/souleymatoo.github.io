# Phase 5 — PEN-200 OffSec + labs officiels

[← Phase 4](phase-4-buffer-overflows.md) · [Plan](plan-oscp.md) · [Phase 6 →](phase-6-simulations.md)

**Durée totale phase :** 100–140 h  
**Format :** ressource → timeboxing → **focus lecture (examen × ton niveau)**

---

## Objectif de phase

Formalisme OffSec + labs + réflexe rapport.

---

## Docs officielles — quoi lire vraiment

### OSCP+ Exam Guide

| | |
| --- | --- |
| **Ressource** | https://help.offsec.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide |
| **Timeboxing** | **60–90 min** jour 1 pack ; **20 min** relecture J-7 |
| **Focus examen — lire vraiment** | **Section Exam Requirements** ; preuves `local.txt`/`proof.txt` + IP ; soumission control panel ; **restricted tools** ; règles proctoring ; ressources autorisées pendant l'exam. |
| **Vu ton niveau — accélérer / skip** | Skip intros marketing OSCP. Skip FAQ matérielle déjà connue après 1 lecture. |

### OSCP+ Exam FAQ

| | |
| --- | --- |
| **Ressource** | https://help.offsec.com/hc/en-us/articles/4412170923924-OSCP-Exam-FAQ |
| **Timeboxing** | **30–45 min** |
| **Focus examen — lire vraiment** | **Scénarios de points** (AD 40 + standalones) ; modules AD recommandés ; outils autorisés vs interdits ; ressources pendant exam (notes OK, LLM non). |
| **Vu ton niveau — accélérer / skip** | Skip questions logistiques VPN déjà résolues une fois le dry-run OK. |

### PEN-200 Onboarding

| | |
| --- | --- |
| **Ressource** | https://help.offsec.com/hc/en-us/articles/4406841351316-PEN-200-Onboarding-A-Learner-Introduction-Guide-to-the-OSCP |
| **Timeboxing** | **45–60 min** |
| **Focus examen — lire vraiment** | Lab precautions, note taking, mindset Try Harder, liens guides préparation (TJnull etc. en **complément**). |
| **Vu ton niveau — accélérer / skip** | Skip « qu'est-ce que le pentest ». Les guides communautaires : lire la méthodo temps, pas les writeups de machines. |

### Reporting Requirements + templates

| | |
| --- | --- |
| **Ressource** | https://help.offsec.com/hc/en-us/articles/360046787731-PEN-200-Reporting-Requirements |
| **Timeboxing** | **2–3 h** (lecture + 1 machine rédigée modèle) |
| **Focus examen — lire vraiment** | Format PDF, screenshots + commandes reproductibles, templates officiels, délai de soumission. |
| **Vu ton niveau — accélérer / skip** | Skip débats d'outils de reporting. Tu documentes déjà en pro : caler le **template OffSec**, pas inventer un style. |

---

## 1. Modules cours — stratégie de lecture

| Type de module | Timeboxing | Focus examen — lire vraiment | Vu ton niveau — accélérer / skip |
| --- | --- | --- | --- |
| Linux / networking / web basique | **45–90 min / module** | Exercices + commandes nouvelles seulement | Skim théorie déjà vue Phases 0–1 / LPIC / Master |
| Windows / priv-esc | **3–5 h / module** | Labs + checklists ; tout exercice | Ne pas skimmer — gap partiel |
| Active Directory | **4–6 h / module** | *Intro & Enum*, *Attacking AD Auth*, *Lateral Movement*, puis challenges AD | **Ralentir ici** — cœur du gap |
| Pivoting | **3–5 h** | Labs tunnel / pivot complets | Skip théorie réseau générale |
| Assembling the Pieces / Challenges | **8–15 h** | Sets AD + standalones comme mini-exam | Pas de writeups externes |
| Reporting | **2–3 h** | Template + 1 machine « examen » | — |

---

## 2. Discipline labs

| | |
| --- | --- |
| **Ressource** | Exam Guide restrictions + course labs + [PG Practice](https://www.offsec.com/labs/practice/) |
| **Timeboxing** | Machine : **max 2 h** sans progrès = switch ; draft rapport **20–40 min** après user/root |
| **Focus examen — lire vraiment** | Liste outils restreints avant d'ouvrir Metasploit ; PG : machines Windows/AD en priorité pour toi. |
| **Vu ton niveau — accélérer / skip** | Ne refais pas 20 machines Linux Easy « pour le plaisir » — volume sur **Windows/AD/Medium**. |

### Tracker

| Machine | OS | Points pot. | Statut | Date | Notes | Temps |
| --- | --- | --- | --- | --- | --- | --- |
| … | … | … | TODO/USER/ROOT | … | `machines/….md` | … |

---

## 3. Rythme hebdo

| Créneau | Objectif | Timeboxing |
| --- | --- | --- |
| 3 soirées | Module ou 1 machine | **2 h** |
| Samedi | AD/Windows ou PG | **4–5 h** |
| Dimanche | Notes + rapport draft | **2 h** |
| **Semaine** | | **~12–15 h** (idéalement 15–20 h) |

---

## Budget temps

| Bloc | Heures |
| --- | --- |
| Modules skimmés | 15–25 h |
| Windows/AD/pivot approfondis | 35–50 h |
| Challenges | 15–25 h |
| PG Practice | 25–40 h |
| Reporting | 8–12 h |
| **Total** | **~100–150 h** |

---

## Critères de sortie

- [ ] Modules PEN-200 complétés
- [ ] Labs Practice majoritairement documentés
- [ ] Template rapport prêt
- [ ] Checklist Exam Guide à jour
- [ ] Confort Intermediate / Medium sur échantillon

---

[← Phase 4](phase-4-buffer-overflows.md) · **Suivant :** [Phase 6 — Simulations](phase-6-simulations.md)
