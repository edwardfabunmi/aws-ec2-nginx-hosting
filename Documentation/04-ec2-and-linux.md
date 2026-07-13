# 4. EC2 provisioning and Ubuntu administration

## Instance provisioning
The initial instance was launched with Ubuntu, a GP3 EBS root volume, the custom VPC and subnet, and the project Security Group. The instance was later resized to a smaller type to reduce ongoing cost.

## SSH key authentication
On window, the downloaded private key must have restrictive permissions:

```bash
chmod 400 portfolioweb-key.pem
ssh -i portfolioweb-key.pem ubuntu@SERVER_PUBLIC_IP
```
```chmod 400 ``` permits only the file owner to read the key. OpenSSH rejects keys that are accessible too broadly.

## Basic administration
```bash
sudo apt update
sudo apt upgrade -y
sudo systemctl status nginx
sudo systemctl restart nginx
```

## Troubleshooting SSH timeout
An SSH timeout is commonly caused by networking rather than the key itself. Validate:

the instance is running;
the public IPv4 address is current;
port 22 is allowed from the administrator's present public IP;
the subnet route reaches the Internet Gateway;
the instance has a public IP;
local or corporate firewalls are not blocking outbound SSH.
