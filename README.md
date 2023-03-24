# MEAN-STACK-DEPLOYMENT-TO-UBUNTU-IN-AWS
NOTE: USE UBUNTU VERSION 20.04 IN ORDER NOT TO RUN INTO ERRORS, IF YOU ARE USING VERSION 22.04 UPWARDS YOU ARE LIKELY TO HAVE ERRORS OR UNSUPPORTED VERSION

MEAN Stack is a combination of the following components:
1. MongoDB (Document database) – Stores and allows retrieval of data.
2. Express (Back-end application framework) – Makes requests to Database for Reads and Writes.
3. Angular (Front-end application framework) – Handles Client and Server Requests
4. Node.js (JavaScript runtime environment) – Accepts requests and displays results to end user

**Preparing prerequisites**

In order to complete this project you will need an AWS account and a virtual server with Ubuntu Server OS, 20.04 LTS (HVM) image.

## Step 1: Install NodeJs
Update ubuntu
```
sudo apt update
```

Upgrade ubuntu
```
sudo apt upgrade
```

In this tutorial, we will explore three different ways of installing Node.js and npm on Ubuntu 20.04:
+ **From the "standard Ubuntu repositories".** This is the easiest way to install Node.js and npm on Ubuntu and should be sufficient for most use cases. The version included in the Ubuntu repositories is 10.19.0.
+ **From the "NodeSource repository."** Use this repository if you want to install a different Node.js version than the one provided in the Ubuntu repositories. Currently, NodeSource supports Node.js v14.x, v13.x, v12.x, and v10.x.
+ **Using "nvm (Node Version Manager)".** This tool allows you to have multiple Node.js versions installed on the same machine. If you are Node.js developer, then this is the preferred way of installing Node.js.

We are going to use NodeSource repository and Node Version Manager which is most preferable for the installation of MongoDB because The new minimum supported Node.js version is now 14.20.1

### Installing Node.Js Way 1
Installing Node.js and npm from NodeSource

NodeSource is a company focused on providing enterprise-grade Node support. It maintains an APT repository containing multiple Node.js versions. Use this repository if your application requires a specific version of Node.js.

At the time of writing, NodeSource repository provides the following versions:
+ v14.x - The latest stable version.
+ v13.x
+ v12.x - The latest LTS version.
+ v10.x - The previous LTS version.

We’ll install Node.js version 14.x:

Run the following command as a user with sudo privileges to download and execute the NodeSource installation script:
```
sudo curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
```

The script will add the NodeSource signing key to your system, create an apt repository file, install all necessary packages, and refresh the apt cache.

If you need another Node.js version, for example 12.x, change the setup_14.x with setup_12.x.

Once the NodeSource repository is enabled, install Node.js and npm:

```
sudo apt-get install -y nodejs
```

The nodejs package contains both the node and npm binaries.

Verify that the Node.js and npm were successfully installed by printing their versions:
```
node --version
```

`
Output
v14.21.3
`

```
npm --version
```

`
Output
6.14.18
`

To be able to compile native addons from npm you’ll need to install the development tools:
```
sudo apt install build-essential
```

### Installing Node.Js Way 2
Installing Node.js and npm using NVM

NVM (Node Version Manager) is a bash script that allows you to manage multiple Node.js versions on a per-user basis. With NVM you can install and uninstall any Node.js version that you want to use or test.
Visit the [](https://github.com/nvm-sh/nvm#installing-and-updating) copy either the curl or wget command to download and install the nvm script:
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```


**NOTE: Do not use sudo while installing mongodb and other items as it will enable nvm for the root user 
e.g `sudo npm install body-parser` it might give an `error sudo command not found`, instead use  `npm install body-parser`**

The script will clone the project’s repository from Github to the ~/.nvm directory:

Close and reopen your terminal to start using nvm

Once the script is in your PATH, verify that nvm was properly installed by typing:
```
nvm --version
```

`
Output
0.35.3
`

To get a list of all Node.js versions that can be installed with nvm, run:
```
nvm list-remote
```

The command will print a huge list of all available Node.js versions.

To install the latest available version of Node.js, run:
```
nvm install node
```

The output should look something like this:



