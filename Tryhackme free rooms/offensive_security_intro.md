TryHackMe - Offensive Security Intro Write-Up

Today I completed the Offensive Security Intro room on TryHackMe and learned an important concept used during web application enumeration: discovering hidden directories and pages.

Scenario

The lab contained a fake banking website. As an attacker, the objective was to identify pages that were not directly linked from the main website but still existed on the server.

In real organizations such as banks, administrators and employees often have separate portals for managing accounts, transactions, and internal operations. If these pages are improperly secured or accidentally exposed, they can become valuable targets during a security assessment.

Tool Used: Gobuster

I used Gobuster to enumerate hidden directories and files.

Example command:

gobuster dir -u http://fakebank.thm -w wordlist.txt

Understanding the Parameters

- "-u" specifies the target URL that Gobuster should scan.
- "-w" specifies the wordlist used to guess potential directories and pages.

Gobuster takes each entry from the wordlist and checks whether a corresponding page exists on the target website.

What I Learned

- Websites often contain pages that are not visible through normal navigation.
- Directory enumeration is a critical reconnaissance technique.
- Wordlists can help discover hidden resources such as admin panels, login pages, backups, and internal portals.
- Security assessments often begin with information gathering before attempting further exploitation.

Key Takeaway

This room reinforced the importance of reconnaissance. Before exploiting a target, understanding its structure and identifying hidden resources can reveal valuable attack paths. Learning how tools like Gobuster work provides a strong foundation for future penetration testing and web application security studies.

#TryHackMe #CyberSecurity #EthicalHacking #OffensiveSecurity #LearningInPublic #SOCAnalystJourney