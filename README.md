# who-to-install-and-upgrade-nginx-1.20-on-Ubuntu-20.04
I am using Ubuntu 20.04 and i have installed nginx using sudo apt update sudo apt install nginx

## Installation instructions
Before you install nginx for the first time on a new machine, you need to set up the nginx packages repository. Afterward, you can install and update nginx from the repository.

## Supported distributions and versions
nginx packages are available for the following Linux distributions and versions:

**RHEL/CentOS**

Version	Supported Platforms
```
7.4+	x86_64, ppc64le, aarch64/arm64
8.x	x86_64, aarch64/arm64, s390x
```
**Debian**

Version	Supported Platforms

```
10.x “buster”	x86_64, i386, aarch64/arm64
11.x “bullseye”	x86_64, aarch64/arm64
```
**Ubuntu**

Version	Supported Platforms
```
18.04 “bionic”	x86_64, aarch64/arm64
20.04 “focal”	x86_64, aarch64/arm64, s390x
21.10 “impish”	x86_64, aarch64/arm64
```
**SLES**

Version	Supported Platforms
```
12 SP5+	x86_64
15 SP2+	x86_64
```
**Alpine**

Version	Supported platforms
```
3.12	x86_64, aarch64/arm64
3.13	x86_64, aarch64/arm64
3.14	x86_64, aarch64/arm64
3.15	x86_64, aarch64/arm64
```
**Amazon Linux**

Version	Supported platforms
```
2 (LTS)	x86_64, aarch64/arm64
```

_________________________________________

![This is an image](https://myoctocat.com/assets/images/base-octocat.svg)

## Install Howto

>If you want to install version 1.20.2 specifically, you will need to add the official nginx repository to your Sources list.

Here is how you do it:

>Open Terminal (or connect via SSH)

*Ensure you have all of the prerequisites installed:*
```
sudo apt install curl gnupg2 ca-certificates lsb-release ubuntu-keyring
```
*Import the nginx signing key for apt:*
```
curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor \
     | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null

```
*Create a sources .list file for apt:*
```
echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
     http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
     | sudo tee /etc/apt/sources.list.d/nginx.list
```
*Pin the repository to ensure the nginx packages are installed instead of the Ubuntu-provided packages:*
```
echo -e "Package: *\nPin: origin nginx.org\nPin: release o=nginx\nPin-Priority: 900\n" \
     | sudo tee /etc/apt/preferences.d/99-nginx
```
*Update apt:*
```
sudo apt update
```
*Install nginx:*
```
sudo apt install nginx
```
NOW YOU HAVE SUCCESSFULLY INSTALL NGINX NEW STABLE VERSION 1.20.2 ,but some time you have some ,little bit problem. 
=================================================================================================================

i have attached the default nginx.conf file replace with the new one,on the save path.
```
cd /etc/nginx/;ls
```
also define the directory of sites-avalible and sites-enabled in the same above path.


SEE YOU NEXT TIME, BEST OF LUCK

