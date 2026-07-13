# secure-static-portfolio-website-on-aws
<img width="2530" height="1291" alt="image" src="https://github.com/user-attachments/assets/c3ae8be9-85fc-4f3b-b745-d56240a8efb5" />



A hands-on AWS project demonstrating how to deploy and secure a production-ready static website using Amazon EC2, Ubuntu, Nginx, a custom domain, Let's Encrypt SSL, VPC networking, and AWS security best practices.

## Live project
### Portfolio website: http://edwardfabunmi.online

## Portfolio contents
* [Project overview](Documentation/01-project-overview.md)
* [Architecture](Documentation/02-architecture.md)
* [AWS networking](Documentation/03-aws-networking.md)
* [EC2 and Linux administration](Documentation/04-ec2-and-linux.md)
* [Nginx deployment](Documentation/05-nginx-deployment.md)
* [DNS and HTTPS](Documentation/06-dns-and-https.md)
* [Security validation](Documentation/07-security-validation.md)
* [Troubleshooting](Documentation/08-troubleshooting.md)
* [Cost optimization](Documentation/09-cost-optimization.md)
* [Lessons learned and roadmap](Documentation/10-lessons-and-roadmap.md)
* [Command cheat sheet](Documentation/commands-cheatsheet.md)

## Skills demonstrated
* AWS VPC, subnet, Internet Gateway, route tables, Security Groups, VPC Flow Logs, S3, EC2, EBS, and Elastic IP
* Ubuntu Linux administration, SSH, SCP, file permissions, and systemd
* Nginx web deployment and service management
* DNS configuration, TLS/SSL, Certbot, and Let’s Encrypt
* Network troubleshooting, security validation, and cloud cost optimization

## 🌐 Architecture & Traffic Flow

The following interactive diagram illustrates the complete infrastructure stack and end-to-end traffic flow, starting from the client request down to the Nginx web server within AWS.

```mermaid
flowchart TD
    U[🌐 Internet User] --> H[HTTPS 443]
    H --> D[Custom Domain<br/>smartcloud9.online]
    D --> DNS[DNS A Record]
    DNS --> IP[EC2 Public IP]
    IP --> IGW[Internet Gateway]
    IGW --> VPC[Custom AWS VPC]
    VPC --> RT[Route Table]
    RT --> SUB[Public Subnet]
    SUB --> SG[Security Group<br/>SSH • HTTP • HTTPS]
    SG --> EC2[Amazon EC2<br/>Ubuntu Server]
    EC2 --> NGINX[Nginx Web Server]
    NGINX --> SSL[Let's Encrypt SSL]
    SSL --> SITE[Static Website<br/>/var/www/html]

    VPC -.-> FLOW[VPC Flow Logs]
    FLOW -.-> S3[Amazon S3 Bucket]

    %% Color Styling for GitHub Light/Dark Modes
    style U fill:#f9f9f9,stroke:#333,stroke-width:2px
    style D fill:#e1f5fe,stroke:#03a9f4,stroke-width:1px
    style IGW fill:#fff3e0,stroke:#ff9800,stroke-width:1px
    style VPC fill:#ede7f6,stroke:#673ab7,stroke-width:2px
    style EC2 fill:#e8f5e9,stroke:#4caf50,stroke-width:2px
    style S3 fill:#ffebee,stroke:#ef5350,stroke-width:1px
