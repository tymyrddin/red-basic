Grove
=================================

To start off in the red team as someone without hacking experience, we recommend following a story of a small grove
in the forest. The tips of the trees' branches are entrypoints to discovering the trunk and then the roots of the
trees, and from there the network of near-infinite and interwoven fungi threads and roots that connect all the trees,
the mycorrhizal network or 'wood web'.

By following the plots in each section, you can get an impression of the grove, and by extension, of the forest.

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Build a lab

   docs/lab/README.md
   docs/lab/Kali.md
   docs/lab/caldera.md
   docs/lab/Windows.md
   docs/lab/macOS.md
   docs/lab/Linux.md
   docs/lab/Metasploitable
   docs/lab/Webgoat
   docs/lab/msfvenom.md
   docs/lab/empire.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Reconnaissance

   docs/reconnaissance/README.md
   docs/reconnaissance/organisation.md
   docs/reconnaissance/person.md
   docs/reconnaissance/dns.md
   docs/reconnaissance/fingerprint-webserver.md
   docs/reconnaissance/crawl-site.md
   docs/reconnaissance/app.md
   docs/reconnaissance/war-dialing-driving-flying-shipping.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Scanning

   docs/scanning/README.md
   docs/scanning/passive.md
   docs/scanning/icmp.md
   docs/scanning/tcp.md
   docs/scanning/udp.md
   docs/scanning/vulns.md
   docs/scanning/service-and-os.md
   docs/scanning/diving.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Enumeration

   docs/enumeration/README.md
   docs/enumeration/host.md
   docs/enumeration/webserver.md
   docs/enumeration/input-vectors.md
   docs/enumeration/network.md
   docs/enumeration/macos.md
   docs/enumeration/linux.md
   docs/enumeration/windows.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Vulnerability identification

   docs/vulnerabilities/README.md
   docs/vulnerabilities/greenbone.md
   docs/vulnerabilities/nessus.md
   docs/vulnerabilities/nikto.md
   docs/vulnerabilities/sqlmap.md
   docs/vulnerabilities/applications.md
   docs/vulnerabilities/mapping.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Database

   docs/databases/README.md
   docs/databases/db-exploits.md
   docs/databases/sqli.md
   docs/databases/confirm-vuln.md
   docs/databases/login-bypass.md
   docs/databases/extract-info.md
   docs/databases/outside-www.md
   docs/databases/get-shell.md
   docs/databases/access-pwd-db.md
   docs/databases/crack-root.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Application

   docs/application/README.md
   docs/application/mapping.md
   docs/application/file-upload.md
   docs/application/rce.md
   docs/application/lfi.md
   docs/application/rfi.md
   docs/application/xss.md
   docs/application/xss-context.md
   docs/application/hook-to-beef.md
   docs/application/cookies.md
   docs/application/clickjacking.md
   docs/application/csrf.md
   docs/application/last-resort.md
   docs/application/mitb.md
   docs/application/browser-based.md
   docs/application/zap.md
   docs/application/post-exploitation.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Server

   docs/server/README.md
   docs/server/traversal.md
   docs/server/response-splitting.md
   docs/server/poison-cache.md
   docs/server/Spoof-webserver.md
   docs/server/Hijack-application-session.md
   docs/server/mitm.md
   docs/server/bruteforce.md
   docs/server/Escalate-reverse-shell.md
   docs/server/Privilege-escalation-on-web-server.md

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
   docs/social-engineering/mail-delivery.md
   docs/social-engineering/c2.md
   docs/social-engineering/fake-login.md
   docs/social-engineering/beef-hook.md
   docs/social-engineering/phishing.md
   docs/social-engineering/pharming.md
   docs/social-engineering/analytics.md
   docs/social-engineering/fake-prompts.md
   docs/social-engineering/out-of-the-box.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: System

   docs/system/README.md
   docs/system/unauthorised-access.md
   docs/system/escalate-shell.md
   docs/system/maintain-windows.md
   docs/system/upload-exec.md
   docs/system/backdoor-windows.md
   docs/system/pe-windows.md
   docs/system/maintain-macos.md
   docs/system/pe-macos.md
   docs/system/pe-linux.md
   docs/system/pivoting.md

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

.. toctree::
   :caption: Links

   Red Team <https://tymyrddin.github.io/red/>