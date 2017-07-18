apic-init-dp
new repo to run the command

WELCOME
INITIAL SETUP
APICONNECT TOOLKIT WITH DATAPOWER
The API Connect Developer toolkit allows the testing and development of APIs with DataPower on a developer’s desktop by using docker-compose to start DataPower and a minimal API Connect Management Server on the same machine the developer is using. The developer does not need remote access to DataPower and API Connect Management Server to start development or testing.
THE PURPOSE OF THIS DOCUMENT
The main purpose of this document is to allow users to setup API Connect Toolkit and test with V6.
FIRST STEP
Go to the Appendix, and find the OS specific setup instructions and complete them before continuing to the “Toolkit Installation and Setup” section of this guide.
TOOLKIT INSTALLATION AND STARTUP
Make sure you execute the following steps from the OS main Display, the instructions cannot be run from a ssh or telnet session. The installation steps will need to start up a Browser from the command line, so if you cannot start a GUI from the session, you will not be able to successfully complete the installation.
1. apic-init-dp tool apic-init-dp is an internal tool that validates your initial setup and preloads the required docker images.
1.1. Download the apic-init-dp tool, open the URL below
1.2. Read the instructions in the README.md file and install the
Experimental gateway.
1.3. Verify the images have been downloaded 1.3.1. “docker images”
2. Create a new “Project” directory to organize your work, change into that directory. (i.e. ~/myproject)
3. Clean the npm cache folder
4. Uninstall old version of apiconnect (you may need administrative privileges to do the install)
5. Delete the directory C:\.apiconnect on Windows or ~/.apiconnect on other platforms.
6. Install apiconnect globally
7. Create an empty directory in the Project directory, call it “reboot- oauth”. Change to the newly created directory and create a
loopback app.
 https://github.ibm.com/apimesh/apiconnect-init-datapower-gateway
  2
npm cache clean
 npm uninstall –g apiconnect
 npm install apiconnect -g --no-shrinkwrap --registry http://apim-ci1.rtp.raleigh.ibm.com:4873
 apic loopback
8. Hit enter at each prompt to choose the defaults.
(Note: Toolkit only works if it detects a loopback project in the directory where you are invoking apic)
9. Ensure that you are in the newly created directory
10. Enter the the following commands at the command line
11. Wait a few minutes, a Browser should open and you should be
presented with the apic editor.
12. Select the API (in this case reboot-oauth)
13. Verify DataPower gateway is selected for the gateway
13.1. Click “Assemble” at the top menu
13.2. Click DataPower Gateway policies radio button.
13.3. Click the Save icon
14. Start the servers (bottom of the browser) if they are stopped by pressing the “Play” Button. You should see both the Gateway and Applications running. (Note be patient, it may take a few minutes).
Congratulations you have installed API Connect Toolkit!
 3
apic config:set datapower-api-gateway-experimental=true
 apic config:set oauth-redirect-uri=https://localhost
  SKIP_LOGIN=true apic edit

TESTING THE SETUP
These instructions are for testers who have not used the toolkit, or for those that need a refresher.
1. Edit the API
2. Select the API you just created
3. Delete all security requirements
*** This only applies to DP Reboot/V6, there should be a defect for this ***
1 Click Design Tab
2 Click Security Menu
3 Delete all the Security requirements.
4. Save by clicking the floppy on the upper right corner
 SKIP_LOGIN=true apic edit
  4
5. Click the Assemble Tab, check to verify the servers are running
 6. If the servers are not running, click the “Start the servers” button.
7. Test the API by pressing the “Test” button. You’ll see it on the Assemble screen, under the Source tab).
8. From the “Choose an operation to invoke:” select “get/Messages/greet” and select the operation.
9. Scroll down till you see the Invoke button
10. Press the Invoke button.
11. Check the response by scrolling down
12. If the Status code is -1 and you get a message about an
untrusted certificate you will need to accept the certificiate
 5
 13. click the link in the second window and accept the certificate from the browser
14. Once you’ve accepted the certificate, you should see
6
 APPENDIX
1. PRE-REQUISITES
• Node.js
VERSIONS 4.4+, or 6 +
• Git
Not specified
• Docker CD (Community Edition) (Windows 10, OSX, Linux) v1.13 or higher
• Docker Toolbox (Windows 7) Not specified, choose the latest
• Docker-Compose v1.11 or higher
2. First Steps resources
https://www.npmjs.com/package/apiconnect
https://github.ibm.com/apimesh/apiconnect-mgmt-lite-datapower
https://www.ibm.com/support/knowledgecenter/en/SSMNED_5.0.0 /com.ibm.apic.toolkit.doc/tapim_apic_test_with_dpdockergateway. html
3. Suggestions
• To access find the URL for DataPower
• Type docker ps
• Find the image with “datapower-api-gateway-v6” or
command with “/bin/drouter”
• Find the Ports entry with 9090/tcp
• Example : 0.0.0.0:32769->9090/tcp
• enter https://0.0.0.0:32769 on your browser
      7
• Enter the default username/password for drouter (admin/admin)
• To Edit assemblies
• SKIP_LOGIN=true apic edit
4. Software Setup
• Git setup and GiitHub
Refer to the OS specific setups below for installing git
Follow the instructions at the following URL to connect to github
Note:
Windows 7 users should run git from the “Docker
QuickStart terminal”
Windows 10 users should run git from the ”Git Bash” link.
 8
https://help.github.com/enterprise/2.10/user/articles/connecting-to-github-with-ssh/
5. OS Specific setup
1. OSX
Use Homebrew https://brew.sh/ as a package manager.
1.1. Install node
Install node using nvm (PREFERRED)
https://github.com/creationix/nvm
Or use brew to install nvm
  1.2.
o
1.3. 1.
2.
Install git
Use brew https://www.atlassian.com/git/tutorials/install-git
 Install Docker CE (Community Edition)
Go to URL https://www.docker.com/community- edition#/download and click the link “Download from Docker Store” for your OS. Follow the instructions to install Docker. Choose the “Stable” version of Docker CD. Do Not choose the “Edge” version.
You may need toto add $USER to docker group
  3.
READ: https://docs.docker.com/engine/installation/linux/linux- postinstall/#manage-docker-as-a-non-root-user
  4. Docker-compose will be included when you install Docker 5. Ensure that Docker has resources it needs
6. Click on the Docker Icon on the upper right task bar
7. Click the Preferences Menu option
  9
8. Under the Advanced Tab, allocate at least 4GB RAM and 2 CPUs
9. Verify Docker is running, by clicking on the Docker Icon in the upper right taskbar. Start Docker if it is not running.
 10
2. Linux
2.1. We will use either yum or apt-get as a package manager
(depends on your flavor of Linux)
2.2. Install node
2.3. Install node using nvm (PREFERRED)
https://github.com/creationix/nvm
Or use a package manager
https://nodejs.org/en/download/package-manager/
2.4. Install git
o Use the appropriate package manager
2.5. Install Docker CE (Community Edition) for Centos and Fedora, EE for Redhat
• Go to URL https://www.docker.com/community- edition#/download and click the link “Download from Docker Store” for your OS. Follow the instructions to install Docker.
• You may need to add $USER to docker group
o https://docs.docker.com/engine/installation/linux/linux-
postinstall/#manage-docker-as-a-non-root-user
2.6. Install Docker-Compose
1. https://docs.docker.com/compose/install/
2. Record the docker-compose install location by typing “which
docker-compose”
3. Check version by typing docker-compose –v
4. If it returns the version but no build information use this link
to replace docker-compose:
https://github.com/docker/compose/releases
5. Use the information from step 2 to replace docker-compose
6. I’ve tested with both Version 1.12.0 and 1.13.0
2.7. You will need to disable the firewall while you are testing
apic mgmt.-lite, till you know which ports you need to secure or expose.
        11
12
o Your system may be using firewalld, ufw or iptables. You should disable them for now.
o Example :
• On Linux systems, the following commands may work.
• sudo ufw disable
• systemctl disable firewalld
3. Windows 10
3.1. Install Node
https://medium.com/appseed-io/how-to-run-multiple-versions-of- node-js-with-nvm-for-windows-ffbe5c7a2b47
Or use the IBM tools at http://w3.java.ibm.com/java/jim/ (PREFERRED)
   1.
2. 3.2.
1.
2. 3.
4. 5.
3.3. 3.4.
3.5. Ensure that Docker has the resources it needs
1. Click the ^ to show the hidden icons
Install Java 8 first
Then IBM SDKs for Node.js (choose Version 4 or 6)
Install Docker CE (Community Edition)
Ensure that your Windows machine has the latest updated via Windows Update
Enable Hardware-Assisted Virtualization via the BIOS
Go to URL https://www.docker.com/community- edition#/download and click the link “Download from Docker Store” for your OS. Follow the instructions to install Docker. Choose the “Stable” version of Docker CD. Do Not choose the “Edge” version.
Git will be included with the Docker install
i. If git-bash is not installed, install from ii. https://git-for-windows.github.io
Docker-compose will be included when you install Docker
  Use the “Git Bash” link instead of the command prompt or Power Shell, you must run the “Git Bash” shell as Administrator (“Run as Administrator”)
 13
14
2. Right click the docker whale to get to the menus
3. Clock the settings menu
4. Click the Shared Drives Tab and enable the drive where
API Connect is installed (most likely C:)
5. Click Advanced
6. Ensure that there are 2 or more CPUs allocated
7. Ensure the VM has at least 4GB of RAM allocated
8. Click apply to save changes
4. Windows 7
4.1.
Install Node
https://medium.com/appseed-io/how-to-run-multiple- versions-of-node-js-with-nvm-for-windows-ffbe5c7a2b47 Or use the IBM tools at http://w3.java.ibm.com/java/jim/ (PREFERRED)
o Install Java 8 first
o IBM SDKs for Node.js (choose Version 4 or 6) Install Docker Toolbox
o o
   4.2.
o Ensure that you’ve updated Windows 7 to the latest patch
level.
o Enable Hardware-Assisted Virtualization via the BIOS o Verify HAV support by running tool
https://www.microsoft.com/en-
us/download/details.aspx?id=592
o Install Docker Toolbox from https://www.docker.com/products/docker-toolbox
o Git will be included with the Docker Toolbox install
o Docker-compose will be included when you install Docker 4.3. Use the “Docker Quickstart terminal” link instead of the command prompt or Power Shell. You must run the “Docker
Quickstart terminal” as Administrator.
4.4. You should only have one instance of the “Docker
Quickstart terminal”
   4.5.
o o
Ensure that Docker has the resources it needs Click the Oracle VM Virtual Box shortcut
Verify the correct VM is selected, the click settings
 15
16
4.6. Click the Systems Menu, and find the Motherboard and Processor tabs
 4.7.
o o
Under the Motherboard tab, ensure that the Base Memory has at least 4096 MB RAM
Under the Processor tab, ensure that there are 2 or more Processors/CPUs allocated
Make sure the VM is Powered Off!
