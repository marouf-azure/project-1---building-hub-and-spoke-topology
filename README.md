# project-1---building-hub-and-spoke-topology
In this project, I will build a hub and spoke topology for a small lab based on the article (https://dev.to/peter_samuel_052b9056e236/architecting-secure-hub-spoke-networks-in-azure-a-practical-guide-11b). In enterprises, proposals are put forward for migrating a web application to Azure while enforcing strong network security. On paper it looks easy, but the challenge comes during the security and scalability stage. 

Azure provides the hub and spoke VNET architecture for solving this problem.

The hub-VNET being the secure core of the network (all firewalls, VPN gateways, DNS are placed here)- routes traffic through spokes after inspection and logging.
The spoke-VNET(the workload specific VNET -for applications)- it hosts web servers and databases.

As a problem solver, one must know the reason for every step that is involved in building the network topology for future referencing and troubleshooting.

To start with we prepared the groundwork (as per the article):

1) Provision two virtual networks with non-overlapping IP address spaces.

2) Segment the application network into subnets for layered security.

3) Establish private connectivity between them using VNet Peering.

I followed the initial steps to make the foundation configs by making 2 VNETS - hub-vnet (public and firewall) and App-vnet (spoke) - that has 2 subnets - the backend and the frontend. After making both the VNETs, I got them peered. 
Then from there deploying an Azure Firewall into the Azure Firewall subnet (in the Hub-VNET) was the next configuration, something new that I learned today.
As the firewall subnet is like a reserved space for the firewall, so we need to deploy the Azure firewall in it by creating it in the resource groups. 

