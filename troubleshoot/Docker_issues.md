# Docker Issues

Verify Docker is running by clicking on the Docker Icon in the taskbar. Start Docker if it is not running.

### Configuration:
Ensure that you configure Docker to allocate at least 4.0 GB of memory and 2 CPU to the images in the **Menu > Preferences > Advanced** tab.

### Using the DataPower Docker Container
To find the URL for DataPower enter `docker ps`.

Find the image with `datapower-api-gateway-v6` or in `/bin/drouter`.

Find the Ports entry with 9090/tcp
    • Example : `0.0.0.0:32769->9090/tcp`

To access the DataPower container, open the web page https://0.0.0.0:32769 on your browser, and enter the default username/password for drouter (`admin`/`admin`).


## Troubleshooting:

**All Platforms**
I am getting the message `setup-container is already running` when I attempt to run node `test/util/setup-containers.js`

    solution: delete the files `test/.env` and `test/tmp-*`

Be sure to cd to your project directory before running `apic loopback`.

There are often random failures during `npm install -g apiconnect` that don’t actually cause serious problems.

if you’re having trouble with `git clone` stage, be sure that you’ve added an SSH key to your GH account https://help.github.com/enterprise/2.10/user/articles/connecting-to-github-with-ssh/
or with Personal Access Token: https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/

The error
```
$ git clone https://github.ibm.com/apimesh/apiconnect-init-datapower-gateway
Cloning into 'apiconnect-init-datapower-gateway'...
Username for 'https://github.ibm.com': belyi@us.ibm.com
Password for 'https://belyi@us.ibm.com@github.ibm.com':
remote: Password authentication is not available for Git operations.
remote: You must use a personal access token or SSH key.
```
