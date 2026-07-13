# 7. Security and external validation
## Intended public ports
The external scan detected ports 80 and 443. That is expected for a public website:

**80/TCP** accepts HTTP and normally redirects visitors to HTTPS

**443/TCP** serves encrypted HTTPS traffic.

SSH was restricted to an administrator source address, so a scanner elsewhere should not detect port 22 as open.

## Hardening checklist
- Remove any ```All traffic``` inbound Security Group rule.
- Restrict SSH to trusted ```/32``` addresses or replace it with AWS Systems Manager Session Manager.
- Keep Ubuntu and Nginx patched.
- Disable password-based SSH login.
- Require IMDSv2.
- Do not expose application development ports directly to the Internet.
- Back up source code outside the EC2 volume.
- Store secrets in environment configuration or a secrets-management service, never in Git.
## Validation commands
```
sudo nginx -t
sudo ss -tulpn
sudo ufw status verbose
curl -I https://edawrdfabunmi
```

