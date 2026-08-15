# Phase 3 — Active Directory (cœur du gap)

[← Phase 2](phase-2-privilege-escalation.md) · [Plan](plan-oscp.md) · [Phase 4 →](phase-4-buffer-overflows.md)

**Compte :** **TryHackMe Premium déjà actif** — rooms/paths AD Premium en première intention.

**Durée totale phase :** 80–100 h  
**Format :** ressource → timeboxing → **focus lecture (examen × ton niveau)**

---

## Objectif de phase

Attaquer un domaine Windows jusqu'à Domain Admin — principal écart CV → OSCP+.

---

## 1. Concepts (socle)

### AD DS / objets / trusts

| | |
| --- | --- |
| **Ressource** | Microsoft Learn [AD DS overview](https://learn.microsoft.com/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview) + **THM Premium** [Active Directory Basics](https://tryhackme.com/room/activedirectorybasics) |
| **Timeboxing** | **4–5 h** |
| **Focus examen — lire vraiment** | Microsoft : domaine vs forêt, DC, users/computers/groups, GPO (idée). Room THM : **tout** le parcours pratique. Vocabulaire : SID, SPN, OU. |
| **Vu ton niveau — accélérer / skip** | Skip design d'architecture AD enterprise, sites/replication, schéma étendu. Tu n'as pas besoin d'être admin AD prod — juste attaquant. |

### Kerberos vs NTLM

| | |
| --- | --- |
| **Ressource** | Microsoft [Kerberos Authentication Overview](https://learn.microsoft.com/windows-server/security/kerberos/kerberos-authentication-overview) + HackTricks Kerberos |
| **Timeboxing** | **3–4 h** notes |
| **Focus examen — lire vraiment** | Flux **AS-REQ / AS-REP / TGS-REQ / TGS-REP** ; rôle du SPN ; différence NTLM (hash) vs Kerberos (tickets). Lien direct avec AS-REP Roast / Kerberoast / PtH / PtT. |
| **Vu ton niveau — accélérer / skip** | Skip RFC Kerberos complète, crypto des keys, troubleshooting Microsoft long format. Schéma 1 page + 5 techniques liées = suffisant. |

---

## 2. Enumeration AD

### BloodHound

| | |
| --- | --- |
| **Ressource** | [BloodHound docs](https://bloodhound.readthedocs.io/) · [BloodHound.py](https://github.com/dirkjanm/BloodHound.py) |
| **Timeboxing** | **4–5 h** |
| **Focus examen — lire vraiment** | Collecte (SharpHound / bloodhound-python) ; import ; requêtes : *Shortest Paths to Domain Admins*, *Kerberoastable*, *AS-REP roastable*, ACL dangereuses (`GenericAll`, `WriteDacl`, `ForceChangePassword`). Comprendre **une arête** avant de l'attaquer. |
| **Vu ton niveau — accélérer / skip** | Skip installation Neo4j deep-dive après le 1er setup OK. Skip Cypher avancé. Skip BloodHound Enterprise marketing. |

### PowerView / Impacket enum

| | |
| --- | --- |
| **Ressource** | [PowerView](https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon) + [Impacket examples](https://github.com/fortra/impacket/tree/master/examples) + HackTricks AD enum |
| **Timeboxing** | **6–7 h** |
| **Focus examen — lire vraiment** | PowerView : `Get-NetUser/Computer/Group`, `Get-ObjectAcl`, spn/asrep helpers selon version. Impacket : `GetADUsers`, `GetNPUsers`, `GetUserSPNs`, `lookupsid`, `smbclient`. Une commande → une note « quand ». |
| **Vu ton niveau — accélérer / skip** | Skip lecture du code source PowerSploit. Skip enum forest trusts complexes tant que DA single-domain n'est pas fluide. |

---

## 3. Attaques OSCP-like

### AS-REP Roast / Kerberoast / spraying

| | |
| --- | --- |
| **Ressource** | **THM Premium** [Attacktive Directory](https://tryhackme.com/room/attacktivedirectory) + Impacket + Hashcat modes + [NetExec wiki](https://www.netexec.wiki/) |
| **Timeboxing** | **5–6 h** room + **2 h** spray |
| **Focus examen — lire vraiment** | Prérequis comptes (no preauth / SPN) ; commandes Impacket ; cracking ; spray prudent. Exam Guide : spoofing/poisoning souvent restreint — **vérifier** avant LLMNR/NBT-NS. |
| **Vu ton niveau — accélérer / skip** | Skip théorie cracking GPU avancée. Skip poisonings si hors règles examen. |

### PtH / Overpass / PtT / ACL / delegation

| | |
| --- | --- |
| **Ressource** | HackTricks (pass-the-hash, tickets, ACL, delegation) + rooms THM Generic Attacks / AD Premium + FAQ OffSec modules AD |
| **Timeboxing** | **12–16 h** cumulés |
| **Focus examen — lire vraiment** | Chaînes courantes OSCP+ : creds → lateral → ACL abuse → DA. Délégation : comprendre *à quoi ça sert* + 1–2 labs ; Golden/Silver : **compréhension + 1 démo**, pas spécialité. |
| **Vu ton niveau — accélérer / skip** | Skip ADCS full ESC1–ESC8 encyclopédie sauf si ton syllabus PEN-200 l'exige. Skip cross-forest warfare. Priorité : **chemins BloodHound exécutables**. |

### Parcours guidé THM

| | |
| --- | --- |
| **Ressource** | **THM Premium** rooms AD Red Team / [Wreath](https://tryhackme.com/room/wreath) |
| **Timeboxing** | **8–12 h** |
| **Focus examen — lire vraiment** | Enchaînement pivot + creds + AD ; notes comme sections de rapport. |
| **Vu ton niveau — accélérer / skip** | Skip rooms purement défensives Blue Team. |

---

## 4. Lateral movement & pivoting

| Objectif | Ressource | Timeboxing | Focus examen | Vu ton niveau |
| --- | --- | --- | --- | --- |
| evil-winrm / Impacket exec | [evil-winrm](https://github.com/Hackplayers/evil-winrm) · `psexec/wmiexec/smbexec` | **4–5 h** | Auth password vs hash ; upload outils | Skip options rares |
| SSH `-D` / proxychains | man ssh · [proxychains-ng](https://github.com/haad/proxychains) | **2–3 h** | Dynamic forward vers réseau interne | Skip VPN enterprise theory |
| chisel / ligolo-ng | READMEs [chisel](https://github.com/jpillora/chisel) · [ligolo-ng](https://github.com/nicocha30/ligolo-ng) | **4–6 h** | Reverse tunnel lab ; 1 scénario documenté | Skip toutes les features ; 1 flow qui marche |

---

## 5. Pratique machines AD

| | |
| --- | --- |
| **Ressource** | HTB Academy AD (si abonnement) · HTB AD · [PG Practice](https://www.offsec.com/labs/practice/) |
| **Timeboxing** | **4–8 h / set** ; bloqué **> 2 h** sur une arête → autre chemin BloodHound |
| **Focus examen — lire vraiment** | FAQ OffSec : modules AD recommandés (*Active Directory Introduction and Enumeration*, *Attacking AD Authentication*, *Lateral Movement in AD*, *Assembling the Pieces*). |
| **Vu ton niveau — accélérer / skip** | Ne compense pas le manque d'AD par plus de Linux — **rester sur AD** jusqu'aux critères de sortie. |

### Session type 3–4 h

| Minute | Action |
| --- | --- |
| 0–40 | Enum users/SMB/LDAP |
| 40–90 | BloodHound + lecture chemins |
| 90–180 | Exécuter **un** chemin |
| 180–240 | Notes rapport + creds |

---

## Budget temps

| Bloc | Heures |
| --- | --- |
| Concepts | 9–12 h |
| Enum tools | 12–15 h |
| Attaques + THM | 25–35 h |
| Lateral + pivot | 12–15 h |
| Machines / PG | 25–35 h |
| **Total** | **~85–110 h** |

---

## Critères de sortie

- [ ] Expliquer un chemin DA BloodHound sans writeup
- [ ] DA via ≥ 3 techniques
- [ ] Notes commandes AD
- [ ] ≥ 1 pivot documenté

---

[← Phase 2](phase-2-privilege-escalation.md) · **Suivant :** [Phase 4 — Buffer overflows](phase-4-buffer-overflows.md)
