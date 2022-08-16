# Automating the server setup

## Terraform

Infrastructure as code uses the idea of having a full declarative description of the components 
that should be running at any given time, from the name of the machine to the last package 
installed on it. A tool then parses this description file and corrects any discrepancies observed, 
such as updating a firewall rule, changing an IP address, attaching more disk, or whatever is needed.

Terraform is open source and [supports a number of cloud providers](https://registry.terraform.io). We can SSH into
our bouncing servers and download the tool:

```text
root@Bouncer:~/# wget\
https://releases.hashicorp.com/terraform/1.2.7/terraform_1.2.7_linux_amd64.zip
root@Bouncer:~/# unzip terraform_1.2.7_linux_amd64.zip
root@Bouncer:~/# chmod +x terraform
```

Terraform will interact with the AWS Cloud using valid credentials that we provide.

## AWS

in progress ...

## The containers

Whichever cloud provider we chose and whatever Linux distribution they host, as long as there is Docker support, we 
can spawn the fully configured C2 backends using a couple of command lines. 

The following will run our Metasploit container:

```text
root@tardis:~/# docker run -dit \
-p 9990-9999:9990-9999 \
-v $HOME/.msf4:/root/.msf4 \
-v /tmp/msf:/tmp/data phocean/msf
```

And this will run the SILENTTRINITY container:

```text
root@tardis:~/# docker run -d \
-v /opt/st:/root/st/data \
-p5000-5050:5000-5050 \
barzh/silent
```

Launching a fully functioning Nginx server that redirects traffic to the 
C2 endpoints is a one-line job:

```text
root@tardis:~/# docker run -d \
-p80:80 -p443:443 \
-e DOMAIN="www.customdomain.com" \
-e C2IP="192.168.1.29" \
-v /opt/letsencrypt:/etc/letsencrypt \
barzh/nginx
```

The DNS record of www.<customdomain>.com should already point to the server’s public IP for this to work. 
The Metasploit and SilentTrinity containers can run on the same host, but the Nginx container must run on a separate 
host. If the IP or domain gets flagged, respawn a new host and run a docker run command. Twenty seconds later, we have 
a new domain with a new IP routing to the same backends.