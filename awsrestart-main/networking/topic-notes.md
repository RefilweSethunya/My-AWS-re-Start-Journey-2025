# Networking Notes

## Virtual Private Cloud (VPC)
- Amazon VPC provides the virtual network infrastructure for AWS resources, logically isolated.  
- VPCs can connect to other networks using:
  - The Internet Gateway for internet access  
  - AWS Direct Connect or VPN for secure private network connections  
  - VPC Peering for communication between different VPCs  

## Domain Name Services (Route 53)
- Amazon Route 53 provides two main DNS-related services:
  - Acts as a domain registrar for many top-level domains (TLDs).  
  - Offers DNS hosting for both public and private domains.
    - To use Route 53:
      - Create a Public Hosted Zone for public domain name resolution.
      - Create a Private Hosted Zone for internal name resolution within a VPC.  

## Content Delivery (CloudFront)
- Amazon CloudFront is a Content Delivery Network (CDN) that speeds up data delivery to end users.  
- It uses edge locations around the world to cache and serve content closer to users.  
- When a user requests content, CloudFront automatically routes the request to the nearest edge location for optimal performance.  

## Reflection
Networking in AWS revolves around securely connecting and optimizing access to cloud resources. The VPC provides the foundation for isolation and connectivity, allowing integration with both public and private networks. Route 53 enhances accessibility and reliability through efficient DNS management for internal and external domains. CloudFront extends this network performance globally, ensuring faster content delivery and an improved user experience. Together, these services form the backbone of AWS networking.

## Exam Essentials
Know the components of a VPC.<br>The key components of a VPC include at least one subnet, security groups, network access control lists (NACLs), and internet gateways.
<br><br>
Be able to select the best Route 53 routing policy for a given scenario.<br>All routing policies except the Simple routing policy can use health checks to route around failures. If you want to direct traffic to any available resource, Failover, Weighted, and Multivalue Answer routing policies will suffice. If performance is a concern, choose a Latency routing policy. If you need to direct users based on their specific location, use a Geolocation routing policy.
