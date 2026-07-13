# 2. Architecture and design decisions

<img width="891" height="1024" alt="image" src="https://github.com/user-attachments/assets/08940a6e-90ff-4913-8d5d-5cedbc833e29" />

## Design principles
The architecture was intentionally simple enough for a first deployment while preserving a clear path toward future expansion.

## Dedicated VPC
A dedicated VPC was used to make the network boundary explicit and reproducible. It provides direct control over addressing, routing, and security.

## Public subnet
The Nginx server is Internet-facing, so the initial EC2 instance resides in a public subnet with a route to an Internet Gateway. Future database and internal application services should be placed in private subnets.

## Stateful instance firewall
An EC2 Security Group controls permitted inbound traffic. SSH is limited to an administrator address, while HTTP and HTTPS serve public visitors.

## Persistent public endpoint
A stable public IPv4 address was associated with the instance so the domain record would not need to change after every stop-and-start cycle. Public IPv4 addresses may incur hourly charges and should be monitored.
