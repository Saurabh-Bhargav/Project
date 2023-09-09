# High Availability pfSense Cluster Implementation Documentation

## Introduction

This documentation outlines the implementation of a high availability pfSense cluster to ensure network continuity and resilience. The project consists of two pfSense virtual machines (VMs) in an active-passive configuration, with a CARP IP address for seamless failover.

## Network 
[Network Diagram](https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20100422.png)




## Requirements

Ensure that your system meets the following requirements before proceeding with the setup:

- **Hardware Requirements**: Describe any hardware prerequisites (e.g., CPU, RAM, storage).
- Below are the configuration of system i used.
- CPU - 10 CORE
- RAM - 8GB
- STORAGE - 500 GB SSD
- **Software Requirements**:
VMware Workstation 17 Player - You can use other virtualization softwares also as you see fit.

## Installation and Configuration Guide

### Step 1: Configure Virtual Machines

1. **Primary pfSense VM (192.168.1.10)**:
   
 https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20092720.png


https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20085846.png


2. **Backup pfSense VM (192.168.1.20)**:
   
 https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20092720.png


https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20085931.png


### Step 2: HA & CARP Configuration

1. Configure the High Availability settings firewall and sync it with backup firewall.
   
   Go to System > High Availability
   
   Make sure you test that changes you making in master are being reflected on backup immediately.
   

2. Configure CARP settings on both pfSense VMs:

https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20090651.png
  
     

### Step 3: Client VM Setup

1. Configure the client VM (192.168.1.50) to use the CARP IP (192.168.1.100) as the gateway:

   https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20092742.png

   
https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20090854.png


### Step 4: Testing and Failover

1. 
https://github.com/Saurabh-Bhargav/Projects/blob/main/pfSense/High%20Availability%20pfSense%20Cluster%20Implementation/Images/Screenshot%202023-09-07%20091217.png
     

   - I turned off the MASTER Firewall(192.168.1.10) but my internet on my client VM was working fine. Also the i was able to login in 192.168.1.100.



## Troubleshooting

In case of issues, refer to the following general troubleshooting tips:

1. **Issue**: **Loss of Connectivity to Primary pfSense VM**
   - **Symptoms**: Inability to access the primary pfSense VM.
   - **Resolution**: Check the primary pfSense VM's status, CARP settings, and network connectivity.

2. **Issue**: **Failover Not Triggered**
   - **Symptoms**: Failover doesn't occur as expected.
   - **Resolution**: Verify CARP settings, ensure proper synchronization between pfSense VMs, and check for network issues.

3. **Issue**: **Client VM Cannot Reach the Internet**
   - **Symptoms**: The client VM loses internet connectivity.
   - **Resolution**: Verify client VM's gateway settings, firewall rules, and CARP IP address.

## Conclusion

For someone new to cluster setups, it's essential to note that in order for high availability to work, the client machine should be configured to use the CARP IP (192.168.1.100) as its gateway, just like you would in a Windows Server cluster. By following the steps outlined here, you have ensured network continuity and resilience in case of a pfSense firewall failure.

For further assistance or inquiries, please feel free to contact the project owner at [SaurabhBhargav@gmail.com](saurabhbhargavofficial.gmail.com) or via [LinkedIn](https://www.linkedin.com/in/Saurabh-Bhargav/).
