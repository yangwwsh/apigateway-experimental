---

copyright:
years: 2017
lastupdated: "2017-07-10"
author: "Om Goeckermann"

---
# MacOS install of the Toolkit preview
Information References
https://www.npmjs.com/package/apiconnect
https://github.ibm.com/apimesh/apiconnect-mgmt-lite-datapower
https://www.ibm.com/support/knowledgecenter/en/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim_apic_test_with_dpdockergateway.html

## Follow these instructions to prepare an environment for the API Connect Toolkit preview.

Install Node.js VERSIONS 4.4+, or 6 + from https://nodejs.org/en/download/.

Install node using nvm. For more information, see: https://github.com/creationix/nvm.

Install git. For more information, see: https://help.github.com/articles/set-up-git/.

Install Docker Community Edition (CE) version 1.13 or higher, which includes Docker Compose.
For more information, see "Download from Docker Store" at https://www.docker.com/community-edition#/download. Choose the “Stable” version of Docker CE rather than the “Edge” version.
    Note: You may need to add $USER to `docker group`. For more information, see:  https://docs.docker.com/engine/installation/linux/linux-postinstall/#manage-docker-as-a-non-root-user

Verify Docker is running by clicking on the Docker Icon in the taskbar. Start Docker if it is not running.

### Configuration:
Ensure that you configure Docker to allocate at least 4.0 GB of memory and 2 CPU to the images in the **Menu > Preferences > Advanced** tab.

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
