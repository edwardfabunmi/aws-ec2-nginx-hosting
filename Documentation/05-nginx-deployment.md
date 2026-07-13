# 5. Nginx deployment
## Install Nginx (Web services engine)
```
sudo apt update -y 
sudo apt upgrade -y 
sudo apt list --upgradable 
apt install nginx -y 
```
## To verify that nginx have been insalled
```
systemctl status nginx
```

## Deploy the static files
A safer deployment pattern is to stage files in the user's home directory, verify them, and then copy them into the web root.
```
mkdir -p ~/webcontent
sudo rsync -av --delete ~/webcontent/ /var/www/html/
sudo nginx -t
sudo systemctl reload nginx
```

## Validate
```
curl -I http://localhost
curl -I http://SERVER_PUBLIC_IP
```
A successful response should return an HTTP status such as 200 OK or a deliberate redirect.

## Common issue: default Nginx page
Seeing the default page means Nginx is working, but the project's files have not yet replaced the default document root or the active server block points elsewhere.
