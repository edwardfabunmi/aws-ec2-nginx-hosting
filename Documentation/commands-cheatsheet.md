# Command cheat sheet

## SSH

```bash
chmod 400 intonasphere-key.pem
ssh -i intonasphere-key.pem ubuntu@SERVER_PUBLIC_IP
```

## Files

```bash
mkdir -p ~/webcontent
unzip website.zip -d ~/webcontent
ls -la ~/webcontent
sudo rsync -av --delete ~/webcontent/ /var/www/html/
```

## Nginx

```bash
sudo nginx -t
sudo systemctl status nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
sudo journalctl -u nginx --since '30 minutes ago'
```

## System

```bash
sudo apt update
sudo apt upgrade -y
df -h
free -h
ss -tulpn
```

## DNS and HTTPS

```bash
dig +short intonasphereai.org
curl -I http://intonasphereai.org
curl -I https://intonasphereai.org
sudo certbot renew --dry-run
```
