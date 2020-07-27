---
layout: default
title: Let's Encrypt everything using yourdomain.com
description: Automatically renewing Let's Encrypt certificates for pfSense, Home Assistant, Unifi, Portainer and Plex
category: Home Automation
published: 2020-07-28
image: ./assets/images/Letsencrypt.jpg
---

# Let's Encrypt everything using yourdomain.com

<img align="right" width="320px" alt="Let's Encrypt Logo" src="../assets/images/Letsencrypt.jpg"/>

In this blog I will show how to setup automatically renewing Let's Encrypt certificates for pfSense, Home Assistant, Unifi, Portainer and Plex.  Clearly if you only have one or two of those servers, then use the Table of Contents (below) to jump to the relevant part.  If you have another server on your network, then this will be a good general guide to setting those up with certificates too.

Like many IT guys, I have owned my own domain for years.  Having recently upgraded my router to something more capable, I started looking at ways to encrypt traffic to make my pfSense router and Home Assistant server accessible remotely.
 
Behind my motivation was the fact that the laptop I spend most time on belongs to my client and they draconian security software which blocks access to unencrypted websites, including those on my own network.  So for peace of mind and for very practical reasons I started looking into getting SSL certificates for every server on my home network, regardless of whether they were publicly accessible.  Perhaps I got carried away, but now I have proper SSL certificates for:

| Server | Desired Sub-Domain |
| --- | --- |
| pfSense Firewall Router | pfsense.yourdomain.com |
| Home Assistant | hassio.yourdomain.com |
| Ubiquiti Unifi Network Controller  | unifi.yourdomain.com |
| Portainer | portainer.yourdomain.com |
| Plex (for internal access) | plex.yourdomain.com |


## pfSense Firewall Router 

I have the excellent [Netgate SG-1100](https://store.netgate.com/pfSense/SG-1100.aspx) router running pfSence.  To say pfSence is a capable firewall is an understatement!  There are so many add-ins that the list is mind boggling.  I had planned to install a Pi-Hole ad-blocking server once I got a new router.  No need.  pfSence has ngBlocker built in which works at the firewall network packet level unlike Pi-Hole which works at the DNS level.  So far more effective than Pi-Hole and built-in.

I will not illucidate how to install automatically renewing Let's Encrypt certificates on the pfSense router because it is expertly covered by ceoS3C in his YouTube video [Enable SSL for pfSense 2.4 - Quick & Easy!](https://www.youtube.com/watch?v=6XMZ0gUZeTc&t=33s)    To cut a long story short, the pfSense router has automatical certificate renewal built-in, so is not hard to configure.

If you are looking to purchase a new router, you should take a serious look at the [Netgate SG-1100](https://store.netgate.com/pfSense/SG-1100.aspx) but be warned - get it from a European distributor - otherwise you will need to pay import duty. Ouch!

### The HAProxy HTTPS offloading alternative 

It's OK if you don't understand the title, neither do I!  But I believe it is one way of implementing certificates for all your devices on the home network. Supposedly this works as reverse proxy for offloading HTTPS traffic to the pfSense router.  However, after watching and re-watching, and re-watching Tom Lawrence's video I could never get this working correctly, so gave up.  [How To Setup ACME, Let's Encrypt, and HAProxy HTTPS offloading on pfsense](https://www.youtube.com/watch?v=gVOEdt-BHDY&t=1841s).  

## Table of Content
* [Certificate Generation](#certificate-generation)
* [Automating Certificate Renewal - Part 1](#automating-certificate-renewal---part-1)
* [Installing Certificate for Home Assistant](#installing-certificate-for-home-assistant)
* [Installing Certificate for Unifi Controller](#installing-certificate-for-unifi-controller)
* [Installing Certificate for Plex](#installing-certificate-for-plex)
* [Installing Certificate for Portainer](#installing-certificate-for-portainer)
* [Automating Certificate Renewal - Part 2](#automating-certificate-renewal---part-2)

## Certificate Generation

I used my Raspberry Pi 4 as the certificate renewal and distribution server.  However, I am sure this approach would work with an Linux variant.

First we need the Let's Encrypt certificate [Certbot command-line utility](https://certbot.eff.org/docs/using.html#certbot-command-line-options).  Install the Let's Encrypt Certbot using:

```sh
sudo bash
app-get update
app-get upgrade 
apt install certbot

# check certbot installed correctly
certbot --version
```

## Obtain the correct DNS plug-in for your supplier

Certbot supports a wide range of [Certbot DNS Plug-ins](https://certbot.eff.org/docs/using.html#dns-plugins) which automate the certificate renewal process.  These utilities connect to your domain's DNS provider and put temporary validation records in place so that the Let's Encrypt CA can check that you own the domain.  There are currently 12 supported DNS providers.  I personally use [Digital Ocean](https://m.do.co/c/c998ff9e98bf) as their service is fabulous.  

Install the DNS extension for Certbot

```sh
apt-get install python3-certbot-dns-digitalocean
```

Create a file containing Digital Ocean token and change permissions:
```sh
chmod 600 /hassio/ssl/dns-digitalocean-credentials.ini
```

## Obtain Certificates

Request the certificate for hassio and all your desired sub-domains.  One certificate will suffice for all services.

```sh
certbot certonly \
  --dns-digitalocean \
  --dns-digitalocean-credentials /hassio/ssl/dns-digitalocean-credentials.ini \
  --dns-digitalocean-propagation-seconds 60 \
  --email john@yourdomain.com \
  -d hassio.yourdomain.com \
  -d unifi.yourdomain.com \
  -d portainer.yourdomain.com \
  -d plex.yourdomain.com 
```
The output from the above command will look like this:

```
IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/hassio.yourdomain.com/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/hassio.yourdomain.com/privkey.pem
   Your cert will expire on 2020-XX-XX. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot
   again. To non-interactively renew *all* of your certificates, run
   "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
```


## Automating Certificate Renewal - Part 1

There are two sides to automating certificate renewal.  First, getting the new certificate and second, installing the new certificate into the correct location so they get picked up by the relevant application (Home Assistant, Unifi, Plex, Portainer etc.).

To enable the second part, note that any executable files found in /etc/letsencrypt/renewal-hooks/pre /etc/letsencrypt/renewal-hooks/deploy, and /etc/letsencrypt/renewal-hooks/post will be run as pre, deploy, and post hooks respectively when the certificate is renewed.  So we create scripts to automate the installation of the certificate as we go along.

## Installing Certificate for Home Assistant

Since Home Assistant is in a docker container, need to copy the certs to a docker accessible folder i.e. hassio config.  As we later want to automate this process, create a shell script **copy_to_hassio.sh** with the following commands

```sh
#!/bin/sh
cp /etc/letsencrypt/live/hassio.yourdomain.com/fullchain.pem /hassio/ssl/
cp /etc/letsencrypt/live/hassio.yourdomain.com/privkey.pem /hassio/ssl/
```
## Install the certificate to Home Assistant
```sh
# Make the file executable 
chmod +x ./copy_to_hassio.sh

# run the new shell script
./copy_to_hassio.sh
```

Now check the Home Assistant configuration.yaml file has the following entries

```yaml
http:
  ssl_certificate: /ssl/fullchain.pem
  ssl_key: /ssl/privkey.pem
```

Restart Home Assistant and then go to URL:

https://hassio.yourdomain.com:8123

Your Home Assistant should now have a valid certificate.

## Install automatic renewal script for Home Assistant

```sh
cp /hassio/ssl/copy_to_hassio.sh /etc/letsencrypt/renewal-hooks/deploy/

chmod +x /etc/letsencrypt/renewal-hooks/deploy/copy_to_hassio.sh
```

# Installing Certificate for Unifi Controller 

This procedure is adopted from [Installing certificates for Unifi](https://lg.io/2015/12/13/using-lets-encrypt-to-secure-cloud-hosted-services-like-ubiquitis-mfi-unifi-and-unifi-video.html)

First create a file called **copy_to_unifi.sh** with the following content:

```sh
#!/bin/sh

# Convert the existing certificates into the correct format using
openssl pkcs12 -export \
	-inkey /etc/letsencrypt/live/hassio.yourdomain.com/privkey.pem \
	-in /etc/letsencrypt/live/hassio.yourdomain.com/fullchain.pem \
	-out /hassio/ssl/cert.p12 \
	-name unifi \
	-password pass:temppass
# Note that temppass is the password used to encrypt the file

# Copy the reformatted cert file inside the unifi docker container
docker cp /hassio/ssl/cert.p12 unifi:/media

# Get inside the docker and run the unpack command for the certificate 
docker exec -it unifi keytool -importkeystore -deststorepass aircontrolenterprise \
  -destkeypass aircontrolenterprise -destkeystore /var/lib/unifi/keystore \
  -srckeystore /media/cert.p12 \
  -srcstoretype PKCS12 \
  -srcstorepass temppass \
  -alias unifi \
  -noprompt
```
## Install the certificate to Unifi Controller 
Run the script created above:
```sh
# Make the file executable 
chmod +x ./copy_to_unifi.sh

# run the new shell script
./copy_to_unifi.sh
```

## Install automatic renewal script for Unifi

```sh
cp /hassio/ssl/copy_to_unifi.sh /etc/letsencrypt/renewal-hooks/deploy/

chmod +x /etc/letsencrypt/renewal-hooks/deploy/copy_to_unifi.sh
```

# Installing Certificate for Plex

The procedure to install a certificate for internal use is adopted from this [guide](https://forums.plex.tv/t/add-custom-ssl-certs-now-available-for-everyone-how-to/128684)

First create a file called **copy_to_plex.sh** with the following content:

```sh
#!/bin/sh

# First enable SSH and SCP to NAS710 using the existing keys.
mkdir -p /root/.ssh

# Copy Public/Private Keys to /root/.ssh/
cp /hassio/homeassistant/nas710/id* /root/.ssh/

cp /hassio/homeassistant/nas710/known_hosts /root/.ssh/

chmod 400 /root/.ssh/id_rsa

echo "Public/Private Keys Copied to /root/.ssh"

# reformat certificate
openssl pkcs12 -export \
  -inkey /etc/letsencrypt/live/hassio.yourdomain.com/privkey.pem \
  -in /etc/letsencrypt/live/hassio.yourdomain.com/fullchain.pem \
  -out /hassio/ssl/plexCert.pfx \
  -name plex \
  -password pass:plexpass
  
# Copy the new cert file over to the NAS710 using SCP		
scp /hassio/ssl/plexCert.pfx root@192.168.1.11:/apps/plexmediaserver/plexCert.pfx	
```

Complete following steps if doing for first time [Plex Certificate installation](https://forums.plex.tv/t/add-custom-ssl-certs-now-available-for-everyone-how-to/128684)

In the Plex administration interface, enter following information:
- Custom certificate location: /apps/plexmediaserver/plexCert.pfx		
- Custom certificate encryption key: plexpass
- Custom certificate domain: plex.yourdomain.com

Now restart plex

## Install automatic renewal script for Plex
```sh
cp /hassio/ssl/copy_to_plex.sh /etc/letsencrypt/renewal-hooks/deploy/

chmod +x /etc/letsencrypt/renewal-hooks/deploy/copy_to_plex.sh
```

# Installing Certificate for Portainer

Setting up Portainer to used the same certificate is simplicity itself.  You simply have to add the command line options **--ssl** when setting up the portainer docker instance.  The following script will obtain the latest portainer image, stop portainer and install a new portainer container with SSL.  Note: change /hassio/ssl to be your specific folder.

```sh
#!/bin/sh

# pull the latest portainer image
docker pull portainer/portainer:latest

# stop portainer
docker stop portainer

# remove portainer container
docker rm portainer

# start new portainer container using SSL
docker run -d -p 9000:9000 -p 8000:8000 \
	--name=portainer \
	--restart=always \
	-v /var/run/docker.sock:/var/run/docker.sock \
	-v portainer_data:/data \
	-v /hassio/ssl:/certs \
	portainer/portainer \
	--ssl \
	--sslcert /certs/fullchain.pem \
	--sslkey /certs/privkey.pem
```

The procedure was adopted from [Portainer Deployment Options](https://portainer.readthedocs.io/en/stable/deployment.html)

# Automating Certificate Renewal - Part 2

Althought cerbot adds a cron job, crom is disable on Debian.  Instead, Debian uses systemd. These instructions as adopted from [Renewing Certbot Certificates using Systemd](https://stevenwestmoreland.com/2017/11/renewing-certbot-certificates-using-a-systemd-timer.html)

Create a *Service unit file* called **certbot-renewal.service** and *Timer unit file* called  **certbot-renewal.timer** for Systemd following the instructions in the link above.

Create a new file **setup_systemd.sh** with the following content:

```sh
#!/bin/sh

# The configuration below will activate the service weekly, and 300 seconds after boot-up.
cp /hassio/ssl/certbot-renewal.service /etc/systemd/system/
cp /hassio/ssl/certbot-renewal.timer   /etc/systemd/system/

systemctl start certbot-renewal.timer

systemctl enable certbot-renewal.timer

systemctl status certbot-renewal.timer
```

Now run **setup_systemd.sh** so the certbot-renewal service and timer are started.
```sh  
chmod +x /hassio/ssl/setup_systemd.sh

./setup_systemd.sh
```

As mentioned above, any executable files found in /etc/letsencrypt/renewal-hooks/pre /etc/letsencrypt/renewal-hooks/deploy, and /etc/letsencrypt/renewal-hooks/post will be run as pre, deploy, and post hooks respectively when certificate renewed. 

Running the following command will attempt to renew the certificate and run all the post deploy scripts we have installed above.

```sh  
certbot renew --dry-run
```

If everything went OK, then all three services will have new certificates.  Restart the services to have the certs take effect.







The only bad apple on my network is the Netgear ReadyNAS RN212 which unfortunately only supports self-signed certicates.  

