# Phase 0 — Fondations offensives accélérées

[← Plan OSCP](plan-oscp.md) · [Phase 1 →](phase-1-enumeration.md)

Profil cible : LPIC + Master sécu — accélérer les bases, basculer en mode attaquant.

**Compte :** **TryHackMe Premium déjà actif** — paths/rooms Premium sans attendre.

**Durée totale phase :** 40–60 h  
**Format :** objectif → ressource → timeboxing → **focus lecture** (examen × ton niveau)

---

## Objectif de phase

Passer de « je sécurise / je diagnostique en ops » à « j'attaque méthodiquement ».

---

## Pourquoi cette phase pour toi

- LPIC-1/2 et Master 2 sécu → **pas** de refresh Linux/réseau complet
- Gap réel : mindset offensive, Windows basics, outils attaquant au clavier
- Temps gagné → **cmd / PowerShell / services Windows**

---

## 1. Mindset OSCP

### Scope, rules of engagement, éthique

| | |
| --- | --- |
| **Ressource** | [OSCP+ Exam Guide](https://help.offsec.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide) · [PEN-200 Onboarding](https://help.offsec.com/hc/en-us/articles/4406841351316-PEN-200-Onboarding-A-Learner-Introduction-Guide-to-the-OSCP) · [PTES — Rules of Engagement](https://pentest-standard.readthedocs.io/en/latest/preengagement_interactions.html#rules-of-engagement) *(miroir ReadTheDocs ; l'ancienne URL `pentest-standard.org/.../Rules_of_Engagement` est en 404)* |
| **Timeboxing** | **60–90 min** lecture annotée → checklist perso in-scope / out-of-scope / interdit |
| **Focus examen — lire vraiment** | Exam Guide : **Exam Requirements**, **proof files** (`local.txt` / `proof.txt` + IP), **exam restrictions / outils interdits**, règles de proctoring et ressources autorisées (notes OK, LLM interdits). Onboarding : **Lab Precautions**, **Best Practices in Labs**, **Lab Tip: Note Taking**. PTES : section **Rules of Engagement** seulement (scope vs RoE, timeline, permissions) — vocabulaire pro, pas noté point par point à l'OSCP. |
| **Vu ton niveau — accélérer / skip** | Skip les intros « qu'est-ce qu'un pentest » / éthique générale (Master 2 sécu). Ne pas lire tout le chapitre Pre-engagement PTES (quotes, legal, NDAs). Extraire une **demi-page** de règles examen OffSec, pas un cours de compliance. |

### Documentation continue (notes)

| | |
| --- | --- |
| **Ressource** | PEN-200 Onboarding § **Lab Tip: Note Taking** + Obsidian / CherryTree |
| **Timeboxing** | **45 min** structure dossiers + **30 min** template machine |
| **Focus examen — lire vraiment** | « Document everything », segmentation *Enumeration / Exploitation / PrivEsc*, idée du rapport final pendant le lab. |
| **Vu ton niveau — accélérer / skip** | Skip les débats d'outils de notes. Tu gères déjà la doc pro (Lead Dev) : copie la structure, ne philosophe pas. Template minimal : `enum / foothold / privesc / credentials / dead-ends`. |

### Discipline timeboxing lab

| | |
| --- | --- |
| **Ressource** | Exam Guide (gestion du temps implicite) + règle perso |
| **Timeboxing** | **20 min** écrire ta règle (ex. 90–120 min sans progrès = switch) |
| **Focus examen — lire vraiment** | FAQ / Guide : scénarios de points (AD vs standalones) pour savoir **quoi prioriser**, pas seulement « travailler dur ». |
| **Vu ton niveau — accélérer / skip** | Pas de lecture longue : une règle écrite + un rappel « AD early ». |

---

## 2. TCP/IP côté attaquant

### Nmap / ports / banners

| | |
| --- | --- |
| **Ressource** | **THM Premium** [Nmap](https://tryhackme.com/room/furthernmap) + [Nmap Reference Guide](https://nmap.org/book/man.html) |
| **Timeboxing** | **3–4 h** room + notes switches |
| **Focus examen — lire vraiment** | Room : scans TCP SYN/version/scripts, output `-oA`, timing, host discovery. Doc Nmap : chapitres / sections **Host Discovery**, **Port Scanning Basics**, **Service and Version Detection**, **NSE** (scripts `default`/`safe` utiles), **Output**. Switches à graver : `-sC -sV -p- -Pn -oA`, `--min-rate` avec prudence. |
| **Vu ton niveau — accélérer / skip** | Skip TCP/IP théorie profonde (Master 2 / téléinfo). Skip UDP exhaustif au début. Skip options obscures (`--datadir`, idle scan, etc.) sauf si un lab l'exige. |

### Services courants (SMB, LDAP, RDP, WinRM, MSSQL, SSH, HTTP)

| | |
| --- | --- |
| **Ressource** | **THM Premium** path [Jr Penetration Tester](https://tryhackme.com/path/outline/jrpenetrationtester) (Network Services) + [Impacket examples](https://github.com/fortra/impacket/tree/master/examples) |
| **Timeboxing** | **6–8 h** (1 service / session) |
| **Focus examen — lire vraiment** | Sur chaque service : enum anonyme, versions, shares/users, auth, pivots possibles. Impacket : README des binaires `smbclient.py`, `wmiexec.py`, `psexec.py`, `secretsdump.py`, `GetNPUsers.py`, `GetUserSPNs.py` — **exemples CLI**, pas le code source. |
| **Vu ton niveau — accélérer / skip** | Skip théorie LDAP/Kerberos profonde ici (Phase 3). Skip HTTP « c'est quoi REST » (Lead Java). Concentre-toi sur **misconfig & foothold**, pas sur l'archi applicative. |

---

## 3. Outils de base

### Gobuster / Feroxbuster

| | |
| --- | --- |
| **Ressource** | **THM Premium** [Gobuster: The Basics](https://tryhackme.com/room/gobustergobasics) + man / `--help` |
| **Timeboxing** | **2 h** |
| **Focus examen — lire vraiment** | Modes **dir**, **dns**, **vhost** ; extensions ; wordlists Kali ; quand s'arrêter (récursion vs bruit). |
| **Vu ton niveau — accélérer / skip** | Skip histoire de l'outil. 3 commandes templates dans tes notes suffisent. |

### SMB enum (`smbclient`, `rpcclient`)

| | |
| --- | --- |
| **Ressource** | **THM Premium** [Network Services](https://tryhackme.com/room/networkservices) + [smbclient man](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html) |
| **Timeboxing** | **3 h** |
| **Focus examen — lire vraiment** | Null session, list shares, download, `rpcclient` enumusers ; signes de creds dans shares. Man : options `-N`, `-L`, usage interactif `get`/`cd`. |
| **Vu ton niveau — accélérer / skip** | Skip protocole SMB interne (tu as le niveau réseaux). Focus commandes actionnables. |

### Impacket / NetExec

| | |
| --- | --- |
| **Ressource** | [Impacket](https://github.com/fortra/impacket) · [NetExec wiki](https://www.netexec.wiki/) |
| **Timeboxing** | **3–4 h** |
| **Focus examen — lire vraiment** | Impacket : pages/examples des outils ci-dessus + auth `-hashes`. NetExec wiki : modules **smb** (enum, spray, shares, spider), pas tout le catalogue. |
| **Vu ton niveau — accélérer / skip** | Skip installation from source / dev contributing. Skip modules exotiques (MSSQL avancé, etc.) jusqu'à ce qu'un lab le demande. |

### Burp Suite

| | |
| --- | --- |
| **Ressource** | PortSwigger [Getting started](https://portswigger.net/burp/documentation/desktop/getting-started) + **THM Premium** [Burp Suite: The Basics](https://tryhackme.com/room/burpsuitebasics) |
| **Timeboxing** | **4–5 h** |
| **Focus examen — lire vraiment** | Proxy intercept, **Repeater**, scope, désactiver intercept, Intruder en mode simple (sniper). Doc : sections Proxy + Repeater seulement au départ. |
| **Vu ton niveau — accélérer / skip** | Skip Collaborator / Extender / AppSec enterprise. Tu connais auth/JWT/Spring : focus **modifier requêtes** et rejouer, pas « comprendre HTTP ». |

### Hydra / Nikto

| | |
| --- | --- |
| **Ressource** | man `hydra` · [Nikto](https://github.com/sullo/nikto) · rooms password attacks du path Jr Pentest |
| **Timeboxing** | **2 h** hydra + **45 min** nikto |
| **Focus examen — lire vraiment** | Hydra : syntaxe service HTTP-FORM / ssh / ftp + risque lockout. Nikto : lire la sortie pour **pistes manuelles**, pas comme preuve d'exploit. Exam Guide : ce qui est restreint côté scanners. |
| **Vu ton niveau — accélérer / skip** | Skip tuning avancé. Nikto = outil secondaire, ne pas en faire un chapitre. |

---

## 4. Shells & transferts

### Reverse / bind shells + TTY

| | |
| --- | --- |
| **Ressource** | [PayloadsAllTheThings — Reverse Shell](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md) + **THM Premium** [What the Shell?](https://tryhackme.com/room/introtoshells) |
| **Timeboxing** | **3–4 h** |
| **Focus examen — lire vraiment** | Bash/python/powershell reverse ; listener `nc -lvnp` ; stabilisation TTY (`pty.spawn`, `stty raw -echo`). 4–5 payloads max dans tes notes. |
| **Vu ton niveau — accélérer / skip** | Skip la liste encyclopédique PayloadsAllTheThings (dizaines de langages). Ignore meterpreter comme dépendance (restrictions examen). |

### Transfert de fichiers

| | |
| --- | --- |
| **Ressource** | [PayloadsAllTheThings — File Transfer](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/File%20Transfer.md) |
| **Timeboxing** | **2 h** |
| **Focus examen — lire vraiment** | Linux : `wget`/`curl`, `scp`, base64. Windows : `certutil`, `iwr`/`Invoke-WebRequest`, smb. Cas « pas d'egress HTTP ». |
| **Vu ton niveau — accélérer / skip** | Skip méthodes exotiques (ICMP, etc.) jusqu'au besoin. Tu connais déjà scp/curl en ops. |

---

## 5. Scripting & Windows basics

### Python helpers

| | |
| --- | --- |
| **Ressource** | **THM Premium** [Python for Pentesters](https://tryhackme.com/room/pythonforpentesting) |
| **Timeboxing** | **3–4 h** |
| **Focus examen — lire vraiment** | Sockets simples, parsing, petits scripts d'exploit/fuzzer — assez pour adapter un POC. |
| **Vu ton niveau — accélérer / skip** | Skip « variables / loops » si fluide en Python. Pas de frameworks (Flask/Django) ici — tu les connais déjà hors scope OSCP. |

### Windows fundamentals (gap prioritaire)

| | |
| --- | --- |
| **Ressource** | Microsoft [PowerShell](https://learn.microsoft.com/powershell/) + **THM Premium** [Windows Fundamentals 1–3](https://tryhackme.com/room/windowsfundamentals1) |
| **Timeboxing** | **6–8 h** |
| **Focus examen — lire vraiment** | Rooms : users/groups, services, registry, permissions fichiers, Task Scheduler. PowerShell doc : cmdlets `Get-Service`, `Get-Process`, `Get-ChildItem`, `Get-Acl`, `whoami` équivalents — navigation & enum, pas admin Exchange. |
| **Vu ton niveau — accélérer / skip** | Skip GUI « découverte Windows » trop lente si déjà à l'aise ; insiste sur **CLI enum** utile priv-esc. Ne dérive pas vers AD ici (Phase 3). |

---

## 6. Setup lab

| Objectif | Ressource | Timeboxing | Focus |
| --- | --- | --- | --- |
| Kali + snapshots | [Kali Get Started](https://www.kali.org/docs/introduction/download-official-kali-linux-images/) | **2–3 h** | Install VM + 1 snapshot clean ; skip customisation ricing |
| Vérifier THM Premium | [TryHackMe](https://tryhackme.com/) | **15 min** | Bookmark path Jr Pentest ; pas de création de compte |
| 1ʳᵉ machine Easy documentée | THM Premium Easy / HTB Easy | **3–5 h** | Appliquer template notes ; accepter l'échec partiel |

---

## Budget temps

| Bloc | Heures |
| --- | --- |
| Mindset + notes + setup | 6–8 h |
| Nmap + services | 10–12 h |
| Outils | 12–15 h |
| Shells + transferts | 5–6 h |
| Python léger | 3–4 h |
| Windows fundamentals | 6–8 h |
| Première machine Easy | 3–5 h |
| **Total** | **~45–58 h** |

---

## Critères de sortie

- [ ] Checklist Exam Guide (restrictions + preuves) dans tes notes
- [ ] Machine Easy enumérée sans writeup
- [ ] Reverse shell Linux stable documenté
- [ ] Template notes opérationnel
- [ ] Bases Windows CLI amorcées

---

[← Plan OSCP](plan-oscp.md) · **Suivant :** [Phase 1 — Enumeration & exploitation manuelle](phase-1-enumeration.md)
