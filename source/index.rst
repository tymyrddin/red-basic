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
   docs/lab/Metasploitable.md
   docs/lab/Webgoat.md

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

   docs/app/README.md
   docs/app/mapping.md
   docs/app/file-upload.md
   docs/app/rce.md
   docs/app/lfi.md
   docs/app/rfi.md
   docs/app/xss.md
   docs/app/xss-context.md
   docs/app/hook-to-beef.md
   docs/app/cookies.md
   docs/app/clickjacking.md
   docs/app/csrf.md
   docs/app/last-resort.md
   docs/app/mitb.md
   docs/app/browser-based.md
   docs/app/zap.md
   docs/app/post-exploitation.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Server

   docs/server/README.md
   docs/server/traversal.md
   docs/server/response-splitting.md
   docs/server/poison-cache.md
   docs/server/spoof.md
   docs/server/hijack-app-session.md
   docs/server/mitm.md
   docs/server/bruteforce.md
   docs/server/escalate-shell.md
   docs/server/privesc.md
   docs/server/picklerick.md

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
   docs/social-engineering/fake-login.md
   docs/social-engineering/beef-hook.md
   docs/social-engineering/analytics.md
   docs/social-engineering/fake-prompts.md
   docs/social-engineering/out-of-the-box.md

.. toctree::
   :maxdepth: 1
   :includehidden:
   :caption: Privilege escalation

   docs/escalation/README.md
   docs/escalation/escalate-shell.md
   docs/escalation/maintain-windows.md
   docs/escalation/upload-exec.md
   docs/escalation/backdoor-windows.md
   docs/escalation/pe-windows.md
   docs/escalation/maintain-macos.md
   docs/escalation/pe-macos.md
   docs/escalation/pe-linux.md
   docs/escalation/pivoting.md

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