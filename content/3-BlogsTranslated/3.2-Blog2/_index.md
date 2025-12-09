---
title: "Blog 2"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Dynamic Routing with Amazon VPC Route Server

AWS provides the managed **Amazon VPC Route Server** service to help customers establish and operate dynamic routing using the Border Gateway Protocol (BGP) within Amazon Virtual Private Cloud (Amazon VPC).

Previously, to enable dynamic routing inside a VPC, you had to deploy a software-based router on Amazon EC2. Now, with Amazon VPC Route Server, you can:

- Establish BGP peerings between Route Server and virtual network appliances  
- Exchange routing information dynamically based on network state  
- Automatically update VPC route tables without manual configuration  
- Detect failures faster using **Bidirectional Forwarding Detection (BFD)**  
- Perform deep traffic inspection across firewalls in Multi-AZ environments  

This blog walks through how Amazon VPC Route Server works, key use cases, and how to begin using dynamic routing in Amazon VPC.

---

## Overview of Amazon VPC Route Server

A customer deploys a software appliance to process voice traffic. This appliance requires dynamic routing as well as updated routing-state information derived from BGP.

The appliance requires:

- Dynamic routing from Route Server  
- Bidirectional BGP sessions for liveness detection  
- Appropriate route switching  

![Figure 1: Dynamic routing architecture with Amazon VPC Route Server](images/hinh1.png)

**Figure 1: Dynamic routing architecture with Amazon VPC Route Server**

Dynamic routing flow:

1. The Route Server establishes a BGP session with the network appliance.  
2. The appliance advertises its service routes to the Route Server.  
3. The Route Server updates the VPC route tables.  
4. The Route Server establishes a BFD session the appliance.  
5. The appliance establishes its BFD session toward the Route Server.  
6. Both sides perform network-detection procedures to maintain BGP session state.

---

## How Dynamic Routing Works in Amazon VPC

![Figure 2: Route exchange from Route Server into VPC route tables](images/hinh2.png)

**Figure 2: Route exchange from Route Server into VPC route tables**

Sequence:

1. The network appliance establishes a BGP session with the Route Server.  
2. Routing updates are exchanged.  
3. The Route Server updates the VPC route table.  
4. Traffic flows using the new route.

---

## When Should You Use Dynamic Routing?

### ✔ Automated Failover Handling

Failover in cloud architectures often requires routes to change immediately when an instance, device, or Availability Zone becomes unhealthy.

![Figure 3: Failover handled through dynamic routing](images/hinh3.png)

**Figure 3: Failover handled through dynamic routing**

---

### ✔ Floating IP Architecture for High Availability

Floating IPs maintain a stable IP address even when the backend instance changes — especially important for:

- financial applications  
- trading systems  
- real-time services  

![Figure 4: Floating IP architecture for high uptime](images/hinh4.png)

**Figure 4: Floating IP architecture for high uptime**

---

### ✔ Traffic Inspection Through Firewalls

Commonly used for:

- DMZ environments  
- outbound traffic filtering  
- blocking unauthorized access  

Dynamic routing enables:

- routing traffic through firewalls on demand  
- automatic adjustment when firewalls go up/down  

![Figure 5: Multi-AZ firewall inspection architecture](images/hinh5.png)

**Figure 5: Multi-AZ firewall inspection architecture**

---

### ✔ Faster Failure Detection with BFD

Before BFD, failover detection could take 10–30 seconds.  
With BFD → **under 1 second**.

![Figure 6: Faster failure detection using BFD](images/hinh6.png)

**Figure 6: Faster failure detection using BFD**

---

### ✔ Automatic VPC Route Table Updates

When routes on the appliance change → VPC route tables update automatically.

![Figure 7: Automatic route updates inside VPC](images/hinh7.png)

**Figure 7: Automatic route updates inside VPC**

---

## Route Consistency and Route Advertisement

![Figure 8: Route advertisement inside Route Server](images/hinh8.png)

**Figure 8: Route advertisement inside Route Server**

The Route Server:

- Accepts routes from the appliance  
- Validates allowed routes  
- Publishes routes into the VPC route table  
- Manages lifecycle based on BGP session state  

---

## BFD and Its Role in Faster Recovery

BFD allows:

- millisecond-level failure detection  
- faster BGP failover  
- improved consistency for latency-sensitive workloads  

![Figure 9: How BFD accelerates failover](images/hinh9.png)

**Figure 9: How BFD accelerates failover**

---

# Conclusion

Amazon VPC Route Server offers a powerful and flexible way to run dynamic routing inside AWS. With support for:

- BGP  
- BFD  
- Firewall inspection  
- Floating IP architectures  
- Automatic route advertisement  

→ Route Server enables the design of highly available, resilient, and easy-to-operate cloud network architectures.

---

# Authors

**Rashid Mulji – Principal Solutions Architect, AWS**  
**Ryan Umstead – Senior Solutions Architect, AWS**
