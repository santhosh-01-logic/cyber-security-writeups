TryHackMe - Defensive Security Introduction

Today I completed the Defensive Security Introduction room on TryHackMe.

Unlike offensive security, where the goal is to find weaknesses, defensive security focuses on detecting attacks, preventing them, and mitigating incidents when they happen.

One thing I learned is that organizations use multiple layers of security because a single security control is never enough.

Firewall

A firewall controls what network traffic is allowed to enter or leave a network.

It acts like a gatekeeper and decides whether traffic should be allowed or blocked based on security rules.

Intrusion Detection System (IDS)

An IDS helps detect suspicious or malicious activity.

It works using rules and patterns that help identify how an attacker or malicious IP address may behave. If something suspicious happens, it generates an alert so the security team can investigate.

Why Layered Security?

I learned that security should have multiple layers because attackers may still get through one defense.

For example, if someone tries to log in from an unusual location or a suspicious IP address, that activity should be detected and investigated. Even if an attacker gains access, there should be additional controls to help identify and stop them.

Threat Intelligence

Before investigating attacks, we need to understand threats.

A threat is something that can cause harm to a system. Attackers may take advantage of vulnerabilities or weaknesses in systems.

Threat intelligence helps security teams understand potential threats, attacker behavior, and indicators of compromise.

Digital Forensics and Incident Response

Digital forensics is the process of finding evidence left behind by an attacker.

No matter what an attacker does, there are usually traces left in logs, files, network traffic, or system activity.

Incident response is what happens after suspicious activity is detected. Security teams investigate, contain, and recover from the incident.

Malware

Malware means malicious software designed to harm, exploit, or gain unauthorized access to systems.

Some examples are:

Trojan Horse

A program that appears legitimate but performs malicious actions in the background, such as modifying or deleting files.

Ransomware

A type of malware that encrypts files and demands payment from the victim to restore access.

Practical Scenario

In the room, I identified a suspicious IP address and treated it as a potential security incident.

The next step was deciding who to escalate the incident to.

I learned that incidents should be escalated through the proper chain of command. In this case, the correct person was the Team Lead because they are responsible for coordinating the response and making decisions.

After receiving approval, I blocked the malicious IP address to help prevent further suspicious activity.

Key Takeaways

- Defensive security focuses on detection, prevention, and response.
- Firewalls control network traffic.
- IDS helps detect suspicious behavior.
- Digital forensics helps find attacker traces.
- Malware comes in many forms, including Trojans and ransomware.
- Security incidents should be escalated to the appropriate team members.
- Logs are extremely important because attackers often leave evidence behind.

Another step forward in understanding how Security Operations Centers (SOCs) protect organizations from cyber threats.

#TryHackMe #CyberSecurity #DefensiveSecurity #SOCAnalyst #ThreatDetection #DigitalForensics #LearningJourney