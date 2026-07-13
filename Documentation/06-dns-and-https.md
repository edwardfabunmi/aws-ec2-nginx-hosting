# 6. DNS and HTTPS

## DNS record
The apex domain was connected to the server using an A record. DNS propagation was checked across multiple resolvers before diagnosing the web server.

## Install Certbot
```
sudo apt install -y certbot python3-certbot-nginx
sudo certbot --nginx -d www.edwardfabunmi -d www.edwardfabunmi
```
Only request hostnames that already resolve to the server.


## Validate renewal
```
sudo certbot renew --dry-run
systemctl status certbot.timer
```
## Verify HTTPS
```
curl -I https://www.edwardfabunmi
```
The browser certificate viewer should show a valid certificate for the domain, issued by a trusted certificate authority.
