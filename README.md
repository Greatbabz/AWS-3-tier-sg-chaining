# AWS 3-Tier Security Group Chaining

## Architecture
Internet → SG-LoadBalancer (80/443) → SG-WebServers (80) → SG-Database (3306)

## Security Groups

| Tier | Security Group | Inbound Rules |
|------|---------------|---------------|
| Load Balancer | SG-LoadBalancer | HTTP (80), HTTPS (443) from the internet |
| Web Servers | SG-WebServers | HTTP (80) from LB, SSH (22) from my IP |
| Database | SG-Database | MySQL (3306) from Web Servers only |

## Key Security Feature
 **Database has ZERO internet exposure** - even if someone finds the IP, the security group blocks them.

## Screenshots
- [Load Balancer SG](./SG-loadbalancer-HTTP&HTTPS.png)
- [Web Servers SG](./SG-webservers-SSH&HTTP.png)
- [Database SG](./SG-database-MYSQL&Aurora.png)
- [Architecture Diagram](./SG-Chaining-Diagram.drawio.png)

## Technologies
- AWS VPC
- Security Groups (Stateful)
- Security Group Chaining
