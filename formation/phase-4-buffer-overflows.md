# Phase 4 — Buffer overflows & client-side

[← Phase 3](phase-3-active-directory.md) · [Plan](plan-oscp.md) · [Phase 5 →](phase-5-pen-200.md)

**Compte :** **TryHackMe Premium déjà actif** — *Buffer Overflow Prep*, *Brainpan*.

**Durée totale phase :** 30–40 h  
**Format :** ressource → timeboxing → **focus lecture (examen × ton niveau)**

> Vérifier le syllabus **de ton** PEN-200 : le poids BO évolue. Entraîne-toi sur le format officiel de ton parcours.

---

## Objectif de phase

Exploit BO from scratch sous chrono — points mécaniques fiables.

---

## 1. Socle

### x86 / stack / EIP

| | |
| --- | --- |
| **Ressource** | **THM Premium** [Buffer Overflow Prep](https://tryhackme.com/room/bufferoverflowprep) (intro) + notes schémas |
| **Timeboxing** | **3–4 h** |
| **Focus examen — lire vraiment** | Room intro : stack layout, overwrite EIP, notion de bad chars, endianness little-endian. Assez pour *piloter* le debugger, pas pour un cours d'archi CPU. |
| **Vu ton niveau — accélérer / skip** | Skip livres d'assembleur complets. Skip x64 / PIE / ASLR bypass modernes si ton parcours est stack BO classique lab (ASLR off). Ton profil Java ne remplace pas cette mécanique : **faire les labs**, ne pas seulement lire. |

### Shellcode / msfvenom (génération lab)

| | |
| --- | --- |
| **Ressource** | Doc [msfvenom](https://www.offsec.com/metasploit-unleashed/msfvenom/) (génération payload) + room |
| **Timeboxing** | **1–2 h** |
| **Focus examen — lire vraiment** | Payload reverse shell, exclusion bad chars (`-b`), format python/c ; listener associé. |
| **Vu ton niveau — accélérer / skip** | Skip catalogue payloads exotiques. Metasploit *exploitation* multi-module ≠ génération shellcode — rester dans les règles examen. |

---

## 2. Pipeline d'exploit

| Étape | Ressource | Timeboxing / run | Focus examen | Vu ton niveau |
| --- | --- | --- | --- | --- |
| Fuzz → crash | THM BO Prep + [Vulnserver](https://github.com/stephenbradshaw/vulnserver) | **15–25 min** | Pattern de crash reproductible | Ne pas optimiser le fuzzer |
| EIP + offset | `pattern_create` / `pattern_offset` | **15–20 min** | Offset exact | — |
| Bad chars | mona / comparaison | **20–40 min** | Liste complète bad chars | Skip théorie encoding longue |
| JMP / shellcode | Immunity/x32dbg + mona | **20–30 min** | `jmp esp` (ou équiv.) + placement | — |
| Shell | `nc`/`rlwrap` | **10–15 min** | Preuve shell | — |
| **Run complet** | Notes perso only | **< 60–90 min** | Comme à l'examen | Cible go : ≤ 75 min |

---

## 3. Outils debugger

| | |
| --- | --- |
| **Ressource** | [Immunity Debugger](https://www.immunityinc.com/products/debugger/) / [x32dbg](https://x64dbg.com/) · [mona.py](https://github.com/corelan/mona) |
| **Timeboxing** | **2 h** debugger + **1–1,5 h** mona |
| **Focus examen — lire vraiment** | Breakpoints, registres, stack pane ; mona : `config`, `jmp`, `bytearray`, `compare`. Corelan : uniquement les tutos alignés sur **ton** type de BO syllabus. |
| **Vu ton niveau — accélérer / skip** | Skip reverse engineering malware / unpacking. Skip plugins hors mona. |

---

## 4. Labs & variantes

| | |
| --- | --- |
| **Ressource** | **THM Premium** Buffer Overflow Prep (tous les bins) · [Brainpan 1](https://tryhackme.com/room/brainpan) · modules PEN-200 si SEH/egghunter requis |
| **Timeboxing** | **12–16 h** stack BO + **0–6 h** variantes syllabus |
| **Focus examen — lire vraiment** | Chaque binaire : refaire le pipeline sans tutoriel ouvert dès le 3ᵉ. Si SEH/egghunter dans PEN-200 : module OffSec correspondant — sections procédure pas à pas. |
| **Vu ton niveau — accélérer / skip** | Skip heap overflows, use-after-free, exploit moderne browser. Skip client-side sauf si ton pack l'inclut explicitement. |

---

## 5. Hygiène & reporting

| | |
| --- | --- |
| **Ressource** | [PEN-200 Reporting Requirements](https://help.offsec.com/hc/en-us/articles/360046787731-PEN-200-Reporting-Requirements) |
| **Timeboxing** | **30 min** setup VM + **30–45 min** doc après chaque exploit |
| **Focus examen — lire vraiment** | Preuves reproductibles : fuzz → offset → bad chars → shell ; captures EIP control. |
| **Vu ton niveau — accélérer / skip** | Skip rédaction prose longue — structure technique claire suffit. |

---

## Runs chronométrés

| Run | Contrainte | Timeboxing |
| --- | --- | --- |
| 1 | Room/tutoriel ouvert | Apprentissage |
| 2 | Notes perso | **≤ 120 min** |
| 3 | Zéro tutoriel | **≤ 90 min** |
| 4 | Exam-like | **≤ 60–75 min** |

---

## Budget temps

| Bloc | Heures |
| --- | --- |
| Socle + outils | 7–9 h |
| 3–5 overflows + Brainpan | 12–16 h |
| Variantes syllabus | 0–6 h |
| Runs chrono | 6–8 h |
| **Total** | **~30–40 h** |

---

## Critères de sortie

- [ ] Exploit BO sans tutoriel
- [ ] < 60–90 min
- [ ] Template notes BO
- [ ] ≥ 3 exploits from scratch

---

[← Phase 3](phase-3-active-directory.md) · **Suivant :** [Phase 5 — PEN-200](phase-5-pen-200.md)
