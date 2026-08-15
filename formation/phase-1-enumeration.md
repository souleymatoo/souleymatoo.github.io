# Phase 1 — Enumeration & exploitation manuelle

[← Phase 0](phase-0-fondations.md) · [Plan](plan-oscp.md) · [Phase 2 →](phase-2-privilege-escalation.md)

**Compte :** **TryHackMe Premium déjà actif** — rooms/paths Premium avant HTB.

**Durée totale phase :** 60–80 h  
**Format :** ressource → timeboxing → **focus lecture (examen × ton niveau)**

---

## Objectif de phase

Trouver le vecteur **sans** scanner « magic ».

---

## Pourquoi cette phase pour toi

- Levier Java/Spring/Keycloak : tu *comprends* les apps — il faut les *attaquer*
- Discipline OSCP : enum manuelle, pas réflexe Snyk/scanner

---

## 1. Enumeration service par service

### Méthodo + HackTricks (index)

| | |
| --- | --- |
| **Ressource** | [HackTricks](https://book.hacktricks.xyz/) — pages pentesting par port/service |
| **Timeboxing** | **2 h** pour squelette cheatsheet + consultations ciblées ensuite |
| **Focus examen — lire vraiment** | Pour chaque port ouvert en lab : la page service correspondante — sections **Enumeration**, **Default credentials**, **Attack / exploit** courtes. Construire `ports → checks → commandes`. |
| **Vu ton niveau — accélérer / skip** | Ne **pas** lire HackTricks de A à Z. Skip hardening / defense chapters. Skip cloud/K8s. Une page service = référence pendant le lab, pas un roman. |

### FTP / SSH / SMTP / SMB / NFS / DB / RDP / WinRM

| | |
| --- | --- |
| **Ressource** | **THM Premium** [Network Services](https://tryhackme.com/room/networkservices) · [Network Services 2](https://tryhackme.com/room/networkservices2) + pages HackTricks dédiées + [evil-winrm](https://github.com/Hackplayers/evil-winrm) README |
| **Timeboxing** | **10–13 h** cumulés |
| **Focus examen — lire vraiment** | Rooms : chaque tâche d'enum anonyme + foothold. evil-winrm README : connexion, upload/download, commandes utiles. HackTricks : uniquement le service du port devant toi. |
| **Vu ton niveau — accélérer / skip** | Skip théorie SMTP/SSH protocolaire. Skip tuning perf DB. Tu as Ops + Linux : va droit aux **checks offensifs**. |

**Règle :** **45–60 min** d'enum profonde max sur un service avant hypothèse ou switch de port.

---

## 2. Web offensive (priorité profil Java)

### PortSwigger Web Security Academy (socle)

| | |
| --- | --- |
| **Ressource** | [Web Security Academy](https://portswigger.net/web-security) + **THM Premium** [OWASP Top 10](https://tryhackme.com/room/owasptop10) |
| **Timeboxing** | **8–10 h** sur les labs Apprentice les plus OSCP-like |
| **Focus examen — lire vraiment** | Topics : **SQL injection**, **OS command injection**, **Directory traversal**, **File upload**, **Access control** (IDOR/bypass), **SSTI** (intro), **Auth** vulnerabilities. Dans chaque topic : paragraphe *Lab* + technique d'exploitation manuelle (Repeater), pas les quizzes business. |
| **Vu ton niveau — accélérer / skip** | Skip / survoler : CORS avancé, JWT attacks complexes, OAuth/OIDC deep-dive (tu les connais côté Keycloak — garde seulement les misconfig évidentes), GraphQL, race conditions, HTTP request smuggling (rare OSCP classique). Skip labs *Expert*. |

### SQLi

| | |
| --- | --- |
| **Ressource** | PortSwigger [SQL injection](https://portswigger.net/web-security/sql-injection) + **THM Premium** [SQL Injection](https://tryhackme.com/room/sqlinjectionlm) |
| **Timeboxing** | **4–5 h** |
| **Focus examen — lire vraiment** | UNION, auth bypass, blind boolean/time — **à la main**. Détection colonne, extraction data. |
| **Vu ton niveau — accélérer / skip** | Skip ORM theory, second-order très avancé. `sqlmap` seulement **après** une exploitation manuelle réussie (pour comparer), jamais en premier réflexe examen. |

### LFI / upload / command injection / SSTI

| | |
| --- | --- |
| **Ressource** | PortSwigger [Path traversal](https://portswigger.net/web-security/file-path-traversal) · [File upload](https://portswigger.net/web-security/file-upload) · [Command injection](https://portswigger.net/web-security/os-command-injection) · [SSTI](https://portswigger.net/web-security/server-side-template-injection) + THM [File Inclusion](https://tryhackme.com/room/fileinc) · [Upload Vulnerabilities](https://tryhackme.com/room/uploadvulns) |
| **Timeboxing** | **9–12 h** |
| **Focus examen — lire vraiment** | Wrappers LFI, log poisoning si abordé ; bypass upload (extension, content-type, double ext) ; inject `;`/`&&`/`\|` ; SSTI détection `{{7*7}}` puis RCE basique. |
| **Vu ton niveau — accélérer / skip** | Skip polyglot PDF/advanced filters. En SSTI : skip engines obscurs ; Jinja/Twig/Freemarker selon lab suffit. |

### Misconfig Spring / apps Java (levier CV)

| | |
| --- | --- |
| **Ressource** | [Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html) (endpoints) + checklist perso (`.env`, `web.xml`, `.git`, backups, heapdump) |
| **Timeboxing** | **2–3 h** |
| **Focus examen — lire vraiment** | Doc Actuator : **endpoints exposés** (`env`, `heapdump`, `mappings`, `beans`, `configprops`) et risque si non sécurisés. Pas l'API de production complète. |
| **Vu ton niveau — accélérer / skip** | Skip « comment configurer Actuator proprement en prod » (tu le sais côté défense). Transforme en : *si je vois `/actuator`, quoi tester ?* |

---

## 3. Password attacks

| Objectif | Ressource | Timeboxing | Focus examen | Vu ton niveau |
| --- | --- | --- | --- | --- |
| Spraying contrôlé | [NetExec wiki](https://www.netexec.wiki/) + Exam Guide restrictions | **2 h** | Syntaxe spray SMB/WinRM ; lockout ; in-scope only | Skip théorie passwords ; 1 lab suffit |
| Cracking | [Hashcat](https://hashcat.net/hashcat/) · [John](https://www.openwall.com/john/) | **3 h** | Identifier mode (`hashid`), `-m` courants (NTLM, kerberoast, md5/sha), wordlist rockyou | Skip attack modes exotiques (rule engineering lourde) au début |
| Centraliser creds | Tes notes | **5 min** / find | Toujours noter d'où vient le secret | — |

---

## 4. Exploitation publique

| | |
| --- | --- |
| **Ressource** | [Exploit-DB](https://www.exploit-db.com/) · `searchsploit` · [GitHub Advisories](https://github.com/advisories) |
| **Timeboxing** | **4–5 h** (2 CVE adaptées) |
| **Focus examen — lire vraiment** | POC : dépendances, IP/port hardcodés, path, auth requise. Adapter → shell **sans** Metasploit si possible. |
| **Vu ton niveau — accélérer / skip** | Skip writeups HTB pendant l'apprentissage machine. Si copy-paste échoue : **max 30 min** puis lecture ligne par ligne (ton niveau Java/Python aide). |

---

## 5. Pratique machines

| | |
| --- | --- |
| **Ressource** | **THM Premium** rooms web ci-dessus · [HTB Machines](https://app.hackthebox.com/machines) Easy |
| **Timeboxing** | **2–4 h / machine** ; bloqué **> 2–3 h** sans piste → switch |
| **Focus examen — lire vraiment** | Aucune doc longue : tes notes + man pages ciblées. En fin de machine : 10 min dead-ends. |
| **Vu ton niveau — accélérer / skip** | Ne pas lire le writeup avant d'être vraiment bloqué. Sur web Java-like, force l'enum app avant l'exploit public. |

### Session type 2–3 h

| Minute | Action |
| --- | --- |
| 0–20 | Scan + tri ports |
| 20–70 | Enum top services |
| 70–120 | Exploitation |
| 120–150 | Notes / dead ends / go-no-go |

---

## Budget temps

| Bloc | Heures |
| --- | --- |
| Enum services + cheatsheet | 12–15 h |
| Web (Academy + THM) | 22–28 h |
| Password / cracking | 5–6 h |
| Exploits adaptés | 4–5 h |
| 15–20 machines Easy | 30–45 h |
| **Total** | **~70–95 h** |

---

## Critères de sortie

- [ ] 15 machines Easy documentées
- [ ] ≥ 5 web shells sans Metasploit
- [ ] `enumeration.md` ports → actions
- [ ] Journal dead ends actif

---

[← Phase 0](phase-0-fondations.md) · **Suivant :** [Phase 2 — Privilege escalation](phase-2-privilege-escalation.md)
