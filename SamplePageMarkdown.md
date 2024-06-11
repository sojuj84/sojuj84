# [NetScaler](https://www.netscaler.com/)
----
## Table of Contents
<!-- no toc -->
1. [NetScaler ADC](#netscaler-adc)
2. [What is ADC?](#what-is-adc)
3. [Where is it placed?](#where-is-it-placed)
4. [What does it do?](#what-does-it-do)

## NetScaler ADC
NetScaler appliance is an application switch that efficiently analyses application-specific traffic to distribute, optimize, and secure Layer4-Layer7 (L4-L7) network traffic for web applications. It acts as a load balancer for each request slowing server failure and minimizing client disruptions.

## What is ADC?
The Application Delivery Controller (ADC) has features that can be broadly classified as:

1. **Data switching:** NetScaler deployed in front of application systems redirects client requests to optimize traffic distribution. Administrators can segment application traffic according to application type. 

2. **Firewall security:** An ADC appliance blocks Application Layer attacks by preventing malicious requests from reaching the Application Layer. An ADC appliance has built-in defenses against DoS attacks, SQL injections, cross-site scripting attacks, buffer overflow exploits, and more. This helps the servers from becoming overwhelmed. The ADC provides security against identity theft securing confidential data.


3. **Optimization:** ADC improves server performance by offloading resource-intensive operations such as SSL processing, data compression, client keep-alive, TCP buffering, and caching from servers, increasing the application speed. Servers or Clients using ADC require no configuration changes to deliver applications.


4. **Policy infrastructure:** A policy defining the specific details of traffic management and filtering on a NetScaler can be set up. A policy consists of 2 parts: the expression (type of request that matches the policy) and the action (what to do with a matching request). A policy list consists of policies with one or more expressions that together define the criteria a connection must meet. The ADC appliance implements only the first matching policy for all policy types except the Rewrite policy. For Rewrite policies, the ADC appliance evaluates the policies in order and performs the associated actions in the same order. Policy priority is important for getting the results you want.


5. **Packet flow:** An ADC appliance can be configured to include multiple features based on the requirement. For example, by configuring both compression and SSL offload, an outgoing packet might be compressed and then encrypted before being sent to the client.
  

## Where is it placed?
A NetScaler appliance is placed between the Client and the Server in a network to work as an intermediary and process the traffic flow. NetScaler acts as a server for incoming traffic to receive requests and sends a new request to the server on behalf of the client.


The following are the common network deployment modes:

1. **Gateway:** NetScaler can be used as a gateway at the perimeter of the intranet providing a secure single point of access to the servers, applications, and other network resources in the internal network.

2. **Application firewall:** NetScaler filters malicious requests and responses preventing security breaches, data loss, and possible unauthorized modifications to websites that access sensitive business or customer information.

3. **Load balancer:** NetScaler operates as a load balancer by distributing client requests across multiple servers using load-balancing criteria to optimize resource utilization. Forwarding each arriving client request to the server best suited to handle the request, NetScaler prevents bottlenecks.

4. **Global server load balancer:** NetScaler can be configured as a GSLB to provide disaster recovery and ensure continuous availability of applications against points of failure in a WAN. In case of an outage, NetScaler balances load across data centers by directing client requests to the closest operational data center.

5. **Packet forwarder:** NetScaler can be configured as a packet forwarder to forward packets to an IP not owned by it. 


The following are the common physical deployment modes:

1. **Inline or Two-arm mode:** The appliance is connected to different Ethernet segments using multiple network interfaces in two-arm mode. It can connect to the server network with one or more redundant interfaces, and the appliance and servers can be on separate subnets. Usually, virtual servers are configured to provide an abstraction of the real servers.

2. **One-arm mode:** One network interface of the appliance is connected to an Ethernet Segment in one-arm mode. In this case, the client and server sides of the network are not isolated but are provided access to applications using virtual servers. One-arm mode can simplify network changes needed for NetScaler installation in some environments.

## What does it do?
The NetScaler appliance is deployed before a server farm to function as a transparent TCP proxy between clients and servers. This does not require any client-side configuration and is called Request Switching technology. Request Switching enables an appliance to multiplex and offload the TCP connections, maintain persistent connections, and manage traffic at the request (application layer) level. This is possible because the appliance can separate the HTTP request from the TCP connection on which the request is delivered.

To function as a proxy, a NetScaler appliance uses a variety of IP addresses. The key NetScaler-owned IP addresses are:

- **NetScaler IP (NSIP) address:** The NSIP address is for management and general system access to the appliance itself, and communication between appliances in a high availability configuration.

- **Virtual server IP (VIP) address:** A VIP address is associated with a virtual server. It is the public IP address to which clients connect.

- **Subnet IP (SNIP) address:** An SNIP address is used in connection management and server monitoring.

- **IP Set:** An IP set is a set of IP addresses, configured on the appliance as SNIP.

- **Net Profile:** A net profile (or network profile) contains an IP address or an IP set. A net profile can be bound to load balancing or content switching virtual servers, services, service groups, or monitors.

Because a NetScaler appliance functions as a TCP proxy, it translates IP addresses before sending packets to a server. When configuring a virtual server, clients connect to a VIP address on the NetScaler appliance instead of directly connecting to a server. In the absence of a virtual server, when an appliance receives a request, it transparently forwards the request to the server. This is called the transparent mode of operation.

The configuration of a NetScaler appliance is typically built up with a series of virtual entities that serve as building blocks for traffic management. The building block approach helps separate traffic flows. A virtual server is a named NetScaler entity that external clients can use to access applications hosted on the servers. It is represented by an alphanumeric name, virtual IP (VIP) address, port, and protocol. Services represent applications on a server. While services are normally combined with virtual servers, a service can still manage application-specific traffic without a virtual server.
