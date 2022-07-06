# Introduction

## What?

Web servers became harder to hack, not impossible to hack. Web servers suffer the same vulnerabilities as other servers do, plus then some:

* Vulnerabilities in the server daemon itself
* Vulnerabilities due to unhardened state: exposed scripts, default pages or default applications
* Vulnerabilities within the applications running on the server

## Why?

* To show that it might be possible to deface the site of the client.
* Gaining access to information which is not intended to be exposed by the client.
* Gaining entry into the internal network (if poorly configured and secured).

## How?

* Take advantage of vulnerabilities on hosts or hosted applications to gain or escalate a shell on the remote server or expose the information in an application database through SQL injection or other techniques.
* Use common vulnerabilities, such as DNS poisoning, weak configurations, and poor patching (but those are becoming rare).
* Find new vulnerabilities with code analysis or fuzzing.


