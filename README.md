# OSPF Routing Protocol Lab Project

## Overview
This lab project involves the implementation and configuration of the OSPF (Open Shortest Path First) routing protocol across a network of routers. The goal is to configure each router to communicate effectively with the Internet and to ensure proper routing functionality using OSPF.

## Requirements
- Routers: R1, R2, R3, R4
- FRRouting (FRR) installed on each router
- Internet access via R1 (configured as the gateway)
- Wireshark for packet capture (optional)

## Configuration Steps

### Part 1: Enable OSPF Daemon
1. Edit the `/etc/frr/daemons` file to enable OSPF on R1.
2. Restart the FRR routing service by executing:
   ```bash
   systemctl restart frr
   ```
3. Repeat the above steps for R2, R3, and R4.

### Part 2: Configure OSPF in Area 0
1. Use `vtysh` to configure OSPF on R1 to advertise its routable networks.
2. Enter the following commands in `vtysh`:
   ```bash
   configure terminal
   router ospf
   network <network> <wildcard-mask> area 0
   ```
3. Identify the appropriate network addresses using `ifconfig` and CIDR notation.

### Part 3: Configure OSPF in Area 1
1. Follow the same steps as in Part 2 for R2 and R3, configuring OSPF in Area 1.
2. Note: OSPF is not configured on R4's eth2 interface, as it points to a terminal node.

### Part 4: Set Default IP Route to R1
1. Configure R2, R3, and R4 to use R1 as the default gateway for accessing the Internet.
2. Verify the configuration by pinging the SFTP server (128.238.77.36) from each router.

## Verification
- Use `ping` and `traceroute` to ensure connectivity between routers and to external destinations.
- Optionally, capture OSPF packets using Wireshark to verify OSPF communication.

## Additional Resources
- [FRRouting Documentation](http://docs.frrouting.org/en/latest/ospfd.html#configuring-ospf)

## Notes
- Ensure to configure passive interfaces where necessary, especially on terminal node interfaces.
- The default IP route on R2, R3, and R4 should point to R1 to access external networks.
