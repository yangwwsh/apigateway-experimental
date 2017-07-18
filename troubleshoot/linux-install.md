---

copyright:
years: 2017
lastupdated: "2017-07-10"
author: "Om Goeckermann"

---
# Linux install of the Toolkit preview
Information References
https://www.npmjs.com/package/apiconnect
https://github.ibm.com/apimesh/apiconnect-mgmt-lite-datapower
https://www.ibm.com/support/knowledgecenter/en/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim_apic_test_with_dpdockergateway.html

## Follow these instructions to prepare an environment for the API Connect Toolkit preview.

Install Node.js VERSIONS 4.4+, or 6 + from https://nodejs.org/en/download/.

Install git. For more information, see: https://help.github.com/articles/set-up-git/.

Ensure that you have installed Docker Community Edition (CE) on Centos and Fedora, or Enterprise Edition (EE)) on Redhat. For more information, see "Download from Docker Store" at https://www.docker.com/community-edition#/download.
    Note: You may need to add $USER to `docker group`. For more information, see:  https://docs.docker.com/engine/installation/linux/linux-postinstall/#manage-docker-as-a-non-root-user

**Note: To install Docker on Ubuntu follow the steps**
** Begin **
1.
```
curl -L https://github.com/docker/compose/releases/download/1.14.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
```
[optional] You can also pipe the result to a temporary file and put it in `/usr/bin/`.
[optional] Another method is to install Docker-Compose using pip (Python Package Installer) with the following commands.
```
 sudo apt-get install python-pip

 sudo pip install docker-compose
```
** End **

Install and verify Docker-Compose version 1.12.0 or higher with the following steps.
  1. Use the Docker-Compose installation instructions at: https://docs.docker.com/compose/install/.
  2. After installation is complete, enter `which docker-compose` and make a note of the Docker-Compose install directory.
  3. Ensure version 1.12.0 or higher is installed by entering `docker-compose –v`.
    Note: If the `-v` output contains version but no build information, replace Docker Compose with the directory information determined in step 2, and instructions found at the following link: https://github.com/docker/compose/releases

You might need to disable your firewall while you are testing API Connect components until you know which ports you need to secure or expose. Your system may be using firewalld, ufw or iptables. Disable them for now.
For example:
    • `sudo ufw disable`
    • `systemctl disable firewalld`
  Note: Note: If you turn off `ufw` (ubuntu firewall), you should renable `ssh` with `sudo ufw allow ssh`. `sudo ufw enable` restores Ubuntu back to defaults.

### Docker Configuration

Ensure that you configure Docker to allocate at least 4.0 GB of memory and 2 CPU to the images.

### Using the DataPower Docker Container

To find the URL for DataPower enter `docker ps`.

Find the image with `datapower-api-gateway-v6` or in `/bin/drouter`.

Find the Ports entry with 9090/tcp
    • Example : `0.0.0.0:32769->9090/tcp`

To access the DataPower container, open the web page https://0.0.0.0:32769 on your browser, and enter the default username/password for drouter (`admin`/`admin`).

## Results

```
Successfully built 23d09337f161
Successfully tagged ibm-apiconnect-toolkit/datapower-api-gateway-v6:1.0.52
```

![Return to Top Level](../../)
