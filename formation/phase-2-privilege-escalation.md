# Phase 2 — Privilege escalation Linux / Windows

[← Phase 1](phase-1-enumeration.md) · [Plan](plan-oscp.md) · [Phase 3 →](phase-3-active-directory.md)

**Compte :** **TryHackMe Premium déjà actif** — rooms PrivEsc accessibles tout de suite.

**Durée totale phase :** 50–70 h  
**Répartition :** ~35–40 % Linux / ~60–65 % Windows  
**Format :** ressource → timeboxing → **focus lecture (examen × ton niveau)**

---

## Objectif de phase

User → root / SYSTEM de façon systématique.

---

## Discipline commune

| | |
| --- | --- |
| **Ressource** | Checklists Tib3rius + [LinPEAS](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS) / [WinPEAS](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS) |
| **Timeboxing** | Enum manuelle **30–45 min** puis scripts **15–20 min** |
| **Focus examen — lire vraiment** | Ordre : manuel d'abord. Dans PEAS : sections *Interesting permissions*, *Credentials*, *Services*, *Sudo/SUID* — pas le dump entier. |
| **Vu ton niveau — accélérer / skip** | Skip « installer PEAS » tutorials longs. Tu sais transférer des fichiers (Phase 0). |

---

## 1. Linux privilege escalation

### Checklist / théorie guidée

| | |
| --- | --- |
| **Ressource** | [HackTricks — Linux Privilege Escalation](https://book.hacktricks.xyz/linux-hardening/privilege-escalation) + cheatsheets Tib3rius + **THM Premium** [Linux PrivEsc](https://tryhackme.com/room/linuxprivesc) |
| **Timeboxing** | **6–8 h** théorie/checklist + **4–5 h** room |
| **Focus examen — lire vraiment** | HackTricks : **sudo**, **SUID/SGID**, **capabilities**, **cron**, **PATH**, **NFS no_root_squash**, **kernel** (quand suggéré), files lisibles (`/etc/passwd` writable, configs creds). Room : **toutes** les tâches pratiques. |
| **Vu ton niveau — accélérer / skip** | Skip intro « qu'est-ce que root » (LPIC). Skip kernel exploit hunting encyclopédique — 1–2 cas stables max. Skip Docker breakout deep-dive (1 h max, tu connais Docker côté ops). Skip hardening CIS. |

### Drills vecteurs

| Vecteur | Timeboxing | Focus |
| --- | --- | --- |
| SUID / sudo / capabilities | Inclus room + **2 h** | Commandes `find`, `sudo -l`, `getcap` |
| Cron / PATH / wildcards / NFS | **2 h** drills | Comprendre *pourquoi* ça élève |
| Kernel (lab only) | **2 h** | Lire le README exploit avant exec |
| 10 escalades Linux | **45–90 min** chacune une fois user | Notes reproductibles |

---

## 2. Windows privilege escalation (prioritaire pour toi)

### Checklist / théorie guidée

| | |
| --- | --- |
| **Ressource** | [HackTricks — Windows Local Privilege Escalation](https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation) + Tib3rius + **THM Premium** [Windows PrivEsc](https://tryhackme.com/room/windows10privesc) |
| **Timeboxing** | **8–10 h** théorie/checklist + **5–6 h** room |
| **Focus examen — lire vraiment** | HackTricks sections : **Service misconfigurations**, **Unquoted service path**, **Weak permissions**, **AlwaysInstallElevated**, **Scheduled tasks**, **Token impersonation / Potato**, **Credential dumping** (SAM, DPAPI, autologon, history), **Privileges** (`SeImpersonatePrivilege`, etc.). Room Windows PrivEsc : compléter **100 %** des exercices. |
| **Vu ton niveau — accélérer / skip** | Skip UAC deep theory non actionnable. Skip kernel exploits Windows rares OSCP. Skip AD attacks ici (Phase 3) même si HackTricks les lie. Skip PowerShell remoting avancé tant que l'enum locale n'est pas fluide. |

### Tokens / Potato / credentials

| | |
| --- | --- |
| **Ressource** | HackTricks (privileges/tokens) + docs outils lab (GodPotato / JuicyPotato selon OS) + Impacket `secretsdump` examples |
| **Timeboxing** | **3–4 h** tokens + **3–4 h** creds |
| **Focus examen — lire vraiment** | Prérequis OS pour chaque Potato ; `whoami /priv` ; où chercher passwords (registry, web.config, history). `secretsdump` : usage local/remote basique. |
| **Vu ton niveau — accélérer / skip** | Skip reverse engineering des exploits Potato. Skip DPAPI math — savoir **où** et **avec quel outil**. |

### 10 escalades Windows

| | |
| --- | --- |
| **Ressource** | HTB / THM Premium / PG Windows |
| **Timeboxing** | **60–120 min** / escalade ; > 2 h → dead end + autre machine |
| **Focus examen — lire vraiment** | Tes checklists, pas de writeup. |
| **Vu ton niveau — accélérer / skip** | C'est ton gap : **ne pas** réduire ce volume. |

---

## 3. Sessions types

| Session | Focus | Timeboxing |
| --- | --- | --- |
| A | Linux cold enum sans script | **45 min** |
| B | Windows cold enum sans script | **45–60 min** |
| C | Machine complète user→root + notes rapport | **2,5–3,5 h** |

---

## Budget temps

| Bloc | Heures |
| --- | --- |
| Linux théorie + room | 12–15 h |
| Windows théorie + room | 16–20 h |
| Drills | 8–10 h |
| 10+10 escalades | 20–30 h |
| **Total** | **~55–75 h** |

---

## Critères de sortie

- [ ] Enum Linux/Windows à froid 30–45 min sans script
- [ ] 10 escalades Linux + 10 Windows documentées
- [ ] `linux-privesc.md` + `windows-privesc.md`

---

[← Phase 1](phase-1-enumeration.md) · **Suivant :** [Phase 3 — Active Directory](phase-3-active-directory.md)
