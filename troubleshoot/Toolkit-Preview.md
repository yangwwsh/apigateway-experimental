---

copyright:
years: 2017
lastupdated: "2017-07-10"
author: "Om Goeckermann"

---
## Using API Connect Toolkit technology-preview with the DataPower Gateway
The Developer toolkit allows the testing and development of APIs with the API Connect Toolkit technology-preview with the DataPower Gateway on a developer’s desktop by using docker-compose to start DataPower and a minimal API Connect Management Server on the same machine the developer is using. The developer does not need remote access to DataPower and API Connect Management Server to start development or testing.

 ## Prerequisites:
 IBM DataPower Gateway Virtual Edition V7.5
 Application Optimization Module for IBM DataPower Gateway V7.5
 IBM HTTP Server

**Install Node and NPM**
See: https://github.com/ibm-apiconnect/getting-started/blob/master/toolkit/0-Prereq/README.md)

**Install Docker and Docker Compose:**
Operating System  Reference
MacOS             (macos-install.md)[macos-install.md]
Linux             (linux-install.md)[linux-install.md]
Windows 10        (win10-install.md)[win10-install.md]
Windows 7         (win7-install.md)[win7-install.md]

**Configuration:**

    Ensure that you configure Docker to allocate at least 4.0 GB of memory to the images.


## Troubleshooting:
see ![Troubleshooting](/troubleshooting/Docker_issues.md)

Start APIC:  ``$ apic-init-dp experimental`
