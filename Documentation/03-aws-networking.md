# 3. AWS networking

## VPC and CIDR
The custom VPC used a private IPv4 address range. The VPC CIDR defines the total address space available to subnets and resources.

## Public subnet
A subnet was created inside the VPC and associated with the public route table. An EC2 instance in this subnet can reach the Internet only when all required layers are present:

## Internet Gateway attached to the VPC
route 0.0.0.0/0 pointing to the Internet Gateway;
subnet associated with that route table;
public IPv4 address on the instance;
Security Group and Network ACL rules permitting the traffic.
Internet Gateway and route table
The Internet Gateway connects the VPC to the Internet. The route table determines where non-local traffic is sent.

| Destination | Target |
|-------------|--------|
| `192.168.0.0/16` | Local |
| `0.0.0.0/0` | Internet Gateway (IGW) |

Destination        Target
192.168.0.0/16     local
0.0.0.0/0          Internet Gateway

## Security Group - Recommended Public Inbound Rules

| Type | Protocol | Port | Source |
|------|----------|------|--------|
| SSH | TCP | 22 | Your Public IP |
| HTTP | TCP | 80 | `0.0.0.0/0` |
| HTTPS | TCP | 443 | `0.0.0.0/0` |

Service	Protocol	Port	Source
SSH	TCP	22	Administrator public IP /32
HTTP	TCP	80	0.0.0.0/0
HTTPS	TCP	443	0.0.0.0/0

Do not use **All traffic** from the entire Internet. Remove temporary broad rules immediately after troubleshooting.

## Network ACL
The default Network ACL was retained during the initial deployment. Unlike Security Groups, Network ACLs are stateless and require corresponding inbound and outbound rules.

## VPC Flow Logs
VPC Flow Logs were configured to capture network-flow metadata for troubleshooting and security analysis. Flow Logs do not capture packet contents.
