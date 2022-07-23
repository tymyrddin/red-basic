.. Trees documentation master file, created by
   sphinx-quickstart on Mon Jun 13 17:53:19 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Attack Trees
=================================

These attack trees are meant as a training zone, a story with several entry points to grok systematic hacking concepts
from. For educational purposes, most trees are example cases to understand the basics, and do not completely spell out
a hack. The use of tools is mininised, there is plenty of room for creativity and experimentation, and links for further
discovery are also given.


.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Testlab

   docs/lab/README.md
   docs/lab/Kali.md
   docs/lab/Windows.md
   docs/lab/macOS.md
   docs/lab/Linux.md
   docs/lab/*

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Reconnaissance

   docs/reconnaissance/README.md
   docs/reconnaissance/Info-company-website.md
   docs/reconnaissance/Info-person.md
   docs/reconnaissance/Deep-dive-DNS.md
   docs/reconnaissance/Gather-app-information.md
   docs/reconnaissance/Discover-app-vulnerabilities.md
   docs/reconnaissance/War-dialing-driving-flying-shipping.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Scanning

   docs/scanning/README.md
   docs/scanning/Hosts-icmp.md
   docs/scanning/Hosts-tcp.md
   docs/scanning/Hosts-udp.md
   docs/scanning/Traceroute-analysis.md
   docs/scanning/Service-and-OS-detection.md
   docs/scanning/Vulnerabilities.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Enumeration

   docs/enumeration/README.md
   docs/enumeration/*

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Database

   docs/databases/README.md
   docs/databases/Access-password-database.md
   docs/databases/Crack-root.md
   docs/databases/DB-exploits.md
   docs/databases/SQLi.md
   docs/databases/Confirm-injection-vuln.md
   docs/databases/SQLi-login.md
   docs/databases/SQLi-extract.md
   docs/databases/SQLi-outside.md
   docs/databases/SQLi-get-shell.md
   docs/databases/Automated-exploitation.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Application

   docs/application/README.md
   docs/application/Mapping.md
   docs/application/File-upload.md
   docs/application/Remote-code-execution.md
   docs/application/Local-file-inclusion.md
   docs/application/Remote-file-inclusion.md
   docs/application/XSS.md
   docs/application/XSS-context.md
   docs/application/Hook-to-beef.md
   docs/application/Cookies.md
   docs/application/Clickjacking.md
   docs/application/CSRF.md
   docs/application/Last-resort.md
   docs/application/MitB.md
   docs/application/Browser-based-attacks.md
   docs/application/ZAP.md
   docs/application/Post-exploitation.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Server

   docs/server/README.md
   docs/server/Spoof-webserver.md
   docs/server/Hijack-application-session.md
   docs/server/Escalate-reverse-shell.md
   docs/server/Privilege-escalation-on-web-server.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: CI/CD pipeline

   docs/cicd/README.md
   docs/cicd/Supply-chain.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Malware

   docs/malware/README.md
   docs/malware/Create-malware.md
   docs/malware/Malware-Windows.md
   docs/malware/Keylogger.md
   docs/malware/Password-recovery.md
   docs/malware/Modify-source.md
   docs/malware/Trojan-Windows.md
   docs/malware/Malware-macOS.md
   docs/malware/Trojan-macOS.md
   docs/malware/Malware-Linux.md
   docs/malware/Trojan-Linux.md
   docs/malware/Target-device.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Social engineering

   docs/social-engineering/README.md
   docs/social-engineering/Mail-delivery.md
   docs/social-engineering/Fake-login.md
   docs/social-engineering/Beef-hook.md
   docs/social-engineering/Phishing.md
   docs/social-engineering/Pharming.md
   docs/social-engineering/Analytics.md
   docs/social-engineering/Fake-prompts.md
   docs/social-engineering/Out-of-the-box.md
   docs/social-engineering/C2.md
   docs/social-engineering/Credential-stuffing.md
   docs/social-engineering/Create-botnet.md
   docs/social-engineering/SEO-poisoning.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: System

   docs/system/README.md
   docs/system/Gain-unauthorised-access.md
   docs/system/Escalate-basic-shell.md
   docs/system/Maintain-windows.md
   docs/system/Maintain-macos.md
   docs/system/Upload-exec.md
   docs/system/Backdoor-system.md
   docs/system/PE-macOS.md
   docs/system/PE-windows.md
   docs/system/PE-linux.md
   docs/system/Pivoting.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Network

   docs/network/README.md
   docs/network/Sniffing.md
   docs/network/ARP-spoofing.md
   docs/network/Compromise-router.md
   docs/network/Attack-domestic-WiFi.md
   docs/network/IP-spoofing.md
   docs/network/DoS.md
   docs/network/DDoS.md
   docs/network/DrDoS.md
   docs/network/Hijack-network-session.md
   docs/network/Replay-attack.md
   docs/network/TCP-sequence-prediction-attack.md
   docs/network/Hijack-BGP.md
   docs/network/DNS-spoofing.md
   docs/network/DNS-attacks.md
   docs/network/SSL-BEAST.md
   docs/network/SSL-hijacking.md
   docs/network/SSL-stripping.md
   docs/network/HTTPS-spoofing.md
   docs/network/MitM.md
   docs/network/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Crypto

   docs/crypto/README.md
   docs/crypto/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Troubleshooting

   docs/trouble/README.md
   docs/trouble/*