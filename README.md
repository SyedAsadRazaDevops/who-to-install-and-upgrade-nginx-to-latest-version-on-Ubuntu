# who-to-install-and-upgrade-nginx-to-latest-version
I am using Ubuntu 20.04 and I have installed nginx using sudo apt update sudo apt install nginx

## Installation instructions
Before installing Nginx for the first time on a new machine, you must set up the Nginx packages repository. Afterwards, you can install and update nginx from the repository.

![image](https://user-images.githubusercontent.com/71556060/204502437-b4d3b759-0457-4eea-a42d-983180073390.png)

## How To Install nginx

>If you want to install version 1.20.2 specifically, you will need to add the official Nginx repository to your Sources list.

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
nano /etc/nginx/nginx.conf
```
replace the file
```
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
        worker_connections 768;
        # multi_accept on;
}

http {

        ##
        # Basic Settings
        ##

        sendfile on;
        tcp_nopush on;
        tcp_nodelay on;
        keepalive_timeout 65;
        types_hash_max_size 2048;
         server_tokens off;

        # server_names_hash_bucket_size 64;
        # server_name_in_redirect off;

        include /etc/nginx/mime.types;
        default_type application/octet-stream;

        ##
        # SSL Settings
        ##

        ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
        ssl_prefer_server_ciphers on;

        ##
        # Logging Settings
        ##

        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;

        ##
        # Gzip Settings
        ##

        gzip on;

        # gzip_vary on;
        # gzip_proxied any;
        # gzip_comp_level 6;
        # gzip_buffers 16 8k;
        # gzip_http_version 1.1;
        # gzip_types text/plain text/css application/json application/javascript text/xml application/xml a>

        ##
        # Virtual Host Configs
        ##

        include /etc/nginx/conf.d/*.conf;
        include /etc/nginx/sites-enabled/*;
}


#mail {
#       # See sample authentication script at:
#       # http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
# 
#       # auth_http localhost/auth.php;
#       # pop3_capabilities "TOP" "USER";
#       # imap_capabilities "IMAP4rev1" "UIDPLUS";
# 
#       server {
#               server_tokens   off;
#       }
# 
#       server {
#               listen     localhost:143;
#               protocol   imap;
#               proxy      on;
#       }
#}

```

also create the directory of sites-available and sites-enabled in the same above path.
```
sudo mkdir /etc/nginx/sites-enabled/
```

```
sudo mkdir /etc/nginx/sites-available/
```

SEE YOU NEXT TIME, BEST OF LUCK
______________________________________________________________________________________________


Enabling Gzip compression in Nginx
===================================
for a Laravel API server can significantly improve response times by reducing the size of the data sent over the network. Here are the steps to enable Gzip compression in Nginx for a Laravel server:

# Enable Gzip Compression
open the nginx configuration/etc/nginx/nginx.conf
```
         gzip on;
         gzip_vary on;
         gzip_proxied any;
         gzip_comp_level 1;
         gzip_buffers 16 8k;
         gzip_http_version 1.1;
         gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;
```

You can use online tools or browser developer tools to verify that Gzip compression is enabled for your API responses.
With these steps, you should have Gzip compression enabled for your Laravel API server using Nginx, resulting in faster and more efficient responses.




