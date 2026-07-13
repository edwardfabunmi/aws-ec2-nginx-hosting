# 8. Troubleshooting record

## Troubleshooting

| **Symptom** | **Likely Cause** | **Resolution** |
|--------------|------------------|----------------|
| SSH connection timed out | Administrator public IP changed | Update the port **22** Security Group source to your current **/32** public IP address. |
| Default Nginx page appeared | Website files were not deployed to the active document root | Copy the website files to `/var/www/html` and reload the Nginx service. |
| Domain did not resolve immediately | DNS propagation delay or incorrect DNS record | Verify the **A** record points to the EC2 public IP and check propagation using DNSChecker. |
| Website displayed as **Not Secure** | SSL/TLS certificate not installed or domain not validated | Install the SSL certificate using **Certbot** after DNS propagation is complete and verify HTTPS. |
| SSH disconnected after reboot | Normal server restart behavior | Wait for the EC2 instance status checks to complete, then reconnect via SSH. |
| Unexpected AWS charges | Larger instance type, EBS storage, or public IPv4 usage | Review **AWS Billing** and **Cost Explorer**, then stop or terminate unused resources and right-size your infrastructure. |

## Layered troubleshooting method
**Local client**: Internet connection, current public IP, key permissions.

**AWS network**: Security Group, NACL, route table, Internet Gateway.

**EC2**: instance state, status checks, public address.

**Operating system**: service state, listening ports, logs.
DNS/TLS: record resolution, certificate hostname and expiry.

**Application**: file paths, permissions, frontend errors.
