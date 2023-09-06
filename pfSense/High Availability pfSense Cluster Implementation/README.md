# High Availability pfSense Cluster Implementation

## Project Description

This project aims to ensure network continuity and seamless operation in the event of a pfSense firewall failure. By implementing a high availability (HA) pfSense cluster, consisting of two virtual machines in an active-passive configuration, we guarantee uninterrupted network services. This project serves as a foundational exploration of pfSense HA, offering a solid starting point for more advanced network security and resilience projects in the future.

## Architecture Overview

- **Primary pfSense VM** (192.168.1.10): This serves as the master firewall, responsible for network traffic when everything is functioning correctly.

- **Backup pfSense VM** (192.168.1.20): This acts as the backup firewall, taking over in case the primary firewall fails.

- **CARP IP** (192.168.1.100): The Common Address Redundancy Protocol (CARP) IP address shared between the pfSense firewalls.

- **Client VM** (192.168.1.50): An Ubuntu 20.04.3 LTS virtual machine used to interact with the pfSense cluster.

## Usage Instructions

1. Clone this repository to your local machine.
2. Refer to the documentation in the `Documentation/` folder for detailed setup instructions.

## Additional Resources

- [pfSense Official Website](https://www.pfsense.org/): For more information on pfSense and its capabilities.

## Contact Information

- Email: [Saurabh_Bhargav](saurabhbhargavofficial@gmail.com)
- LinkedIn: [Saurabh-bhargav](https://www.linkedin.com/in/saurabh-bhargav/)


