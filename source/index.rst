.. Trees documentation master file, created by
   sphinx-quickstart on Mon Jun 13 17:53:19 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Attack Trees
=================================

Attack Trees represent often used movements and can help organise our thoughts around which tools and scripts may be reuseful for which type of pentesting and/or various audits (and which mitigations we may need for our own development efforts).

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Testlab

   docs/lab/README.md
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

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Scanning

   docs/scanning/README.md
   docs/scanning/Initial-scanning.md
   docs/scanning/Ping-sweep.md
   docs/scanning/Port-scanning.md
   docs/scanning/Traceroute-analysis.md
   docs/scanning/Service-and-OS-detection.md

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
   docs/application/Hijack-application-session.md
   docs/application/Clickjacking.md
   docs/application/CSRF.md
   docs/application/Last-resort.md
   docs/application/ZAP.md
   docs/application/Post-exploitation.md

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
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Social engineering

   docs/social-engineering/README.md
   docs/social-engineering/*

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Malware

   docs/malware/README.md
   docs/malware/create-malware.md
   docs/malware/Target-device.md
   docs/malware/Backdoor-veil.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: System

   docs/system/README.md
   docs/system/Gain-unauthorised-access.md
   docs/system/Privilege-escalation-on-windows.md
   docs/system/Privilege-escalation-on-linux.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Server

   docs/server/README.md
   docs/server/Spoof-webserver.md
   docs/server/Escalate-reverse-shell.md
   docs/server/Privilege-escalation-on-web-server.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Network

   docs/network/README.md
   docs/network/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Crypto

   docs/crypto/README.md
   docs/crypto/*

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: CI/CD pipeline

   docs/cicd/README.md
   docs/cicd/Supply-chain.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Troubleshooting

   docs/trouble/README.md
   docs/trouble/*