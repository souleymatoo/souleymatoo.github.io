# Phase 6 — Simulations d'examen + rapport

[← Phase 5](phase-5-pen-200.md) · [Plan](plan-oscp.md) · [Examen OSCP →](examen-oscp.md)

**Durée totale phase :** 40–60 h  
**Format :** ressource → timeboxing → **focus lecture (examen × ton niveau)**

---

## Objectif de phase

Points + rapport dans les délais, sans writeups.

---

## Docs à relire (pas tout le catalogue)

### Exam Guide + FAQ (relecture ciblée)

| | |
| --- | --- |
| **Ressource** | [OSCP+ Exam Guide](https://help.offsec.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide) · [Exam FAQ](https://help.offsec.com/hc/en-us/articles/4412170923924-OSCP-Exam-FAQ) |
| **Timeboxing** | **90–120 min** en J-7 (pas 1ʳᵉ découverte) |
| **Focus examen — lire vraiment** | Scénarios de score ; restrictions outils ; preuves ; délai rapport ; ce qui est autorisé comme ressource pendant l'exam. |
| **Vu ton niveau — accélérer / skip** | Tu as déjà lu en Phase 5 : **relecture annotée** de ta checklist perso, pas relecture intégrale passive. |

### Reporting Requirements + templates

| | |
| --- | --- |
| **Ressource** | [PEN-200 Reporting Requirements](https://help.offsec.com/hc/en-us/articles/360046787731-PEN-200-Reporting-Requirements) |
| **Timeboxing** | **60–90 min** personnaliser template + **45–75 min** chrono sur 1 machine déjà root |
| **Focus examen — lire vraiment** | Exigences screenshots, reproductibilité, nommage/upload, templates officiels. |
| **Vu ton niveau — accélérer / skip** | Skip conseils rédaction « style consultant » longs. Structure claire + preuves > prose. |

### Guides communautaires (complément)

| | |
| --- | --- |
| **Ressource** | Liens listés dans [PEN-200 Onboarding](https://help.offsec.com/hc/en-us/articles/4406841351316-PEN-200-Onboarding-A-Learner-Introduction-Guide-to-the-OSCP) (ex. TJnull) |
| **Timeboxing** | **60–90 min** total |
| **Focus examen — lire vraiment** | Stratégie de temps, ordre AD vs standalones, hygiène notes — **pas** les walkthroughs de boxes. |
| **Vu ton niveau — accélérer / skip** | Skip sections « from zero / no Linux experience ». Ton point de départ est plus haut. |

---

## 1. Simulations

| Objectif | Ressource lab | Timeboxing | Focus | Vu ton niveau |
| --- | --- | --- | --- | --- |
| Simu #1 diagnostic | PG / challenges PEN-200 | **12 h** ou **24 h** | Mesurer enum + AD + notes | Identifier si le frein = AD ou rapport |
| Simu #2 correction | Nouveau set | **24 h** | Corriger le frein #1 | Drills Windows/AD si besoin avant |
| Simu #3 go/no-go | Set le plus exam-like | **24 h** + rapport délai | Décision booking | Ne pas forcer si NO-GO |

### Timeboxing interne 24 h

| Fenêtre | Focus |
| --- | --- |
| 0:00–0:30 | Scope, scans, template |
| 0:30–2:00 | Enum large + triage (**AD early**) |
| 2:00–8:00 | Footholds |
| 8:00–14:00 | Priv-esc + AD |
| 14:00–18:00 | Points restants |
| 18:00–22:00 | Preuves / trous notes |
| 22:00–24:00 | Rapport |
| Post | PDF dans délai OffSec (**confirmer** Exam Guide) |

**Switch :** 90–120 min sans progrès → changer de machine.

---

## 2. Conditions & rétro

| Objectif | Timeboxing | Focus |
| --- | --- | --- |
| Notes perso + portal only (pas LLM) | Continu | Aligné Exam FAQ |
| Pauses 5–10 min / 2 h | Continu | Tenir 24 h |
| ≥ 48 h entre deux simus 24 h | Récupération | Profil Lead Dev : ne pas s'épuiser avant le vrai exam |
| Rétro structurée | **45–60 min** lendemain | Machines ratées, enum lente, AD, rapport |
| Correctif ciblé | **4–10 h** | Retour Phase 2/3/5 selon rétro |

---

## 3. Checklist J-7

| Objectif | Ressource | Timeboxing | Focus lecture |
| --- | --- | --- | --- |
| Relire règles | Exam Guide + FAQ | **90–120 min** | Restrictions + preuves + score |
| Dry-run outils/VPN | Lab local + portal | **2–3 h** | Pas de doc longue — validation opérationnelle |
| Template PDF OK | Reporting Requirements | **30 min** | Export/upload |
| Plan d'attaque écrit | Cette page | **45 min** | Ordre machines + timeboxing |

---

## Budget temps

| Bloc | Heures |
| --- | --- |
| Simulations + rapports | 30–45 h |
| Drills correctifs | 6–12 h |
| Template + rédaction | 4–6 h |
| J-7 | 4–6 h |
| **Total** | **~45–65 h** |

---

## Go / No-Go

- [ ] ≥ 1 simu au-dessus du seuil
- [ ] Rapport dans les délais
- [ ] Plan d'attaque écrit
- [ ] J-7 OK

**GO** : simu OK + rapport propre + AD/Windows stables.  
**NO-GO** : writeups, rapport incomplet, panique AD → simu corrective.

---

[← Phase 5](phase-5-pen-200.md) · **Suivant :** [Examen OSCP](examen-oscp.md)
