# Bouncing servers

Bouncing servers are virtual hosts set up anonymously, to SSH into after connecting to via Tor or a VPN, and trust to 
interact with the rest of our attack infrastructures. Bouncing servers never interact with the target. They are used to 
host management tools like Terraform, Docker, and Ansible that can later help build multiple attack infrastructures.

Although they never interact with the target, they can be associated with those parts of our attack infrastructures 
that do, so deleting and re-creating bouncing servers regularly (every few weeks) is a good idea.

They can be hosted on one or many cloud providers spread across many geographical locations. 
Limitation is the payment solution supported by the providers.

All major cloud providers (AWS, Google Cloud, Microsoft Azure, Alibaba, etc.) require a credit card before approving 
your account. This may not be a problem, as there are many services that provide prepaid credit cards in exchange for 
cash.

## Resources

* [NiceVPS](https://nicevps.net/) costs €15.99 a month for a server with 1GB of memory and one vCPU core. [Cryptocurrency accepted Hosting, VPS, Anonymous Domain](https://nicevps.net/index/payments)
* [Cinfu](https://www.cinfu.com/) costs between €4 and around €5 a month (depending on country, Bulgaria, Netherlands, France, Germany, and availability) for a server with 2GB of memory and one vCPU core. [Payment Options](https://panel.cinfu.com/index.php/knowledgebase/11/Payment-Options.html)
* [PiVPS](https://pivps.com/) costs about $4.99 a month for a server with 1GB of memory and one vCPU core. Supports most major payment gateways, including Bitcoin, PerfectMoney, Skrill (Moneybookers), 2checkout (Credit/Debit Card), PAYEER and OKpay.
