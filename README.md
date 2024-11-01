# Senior Research
## Objective
The objective of this project is to determine whether a trade-off between power consumption and network performance is viable in order to reduce power used by a network without significantly impacting the user experience.

This is done by having a main, high-performance node, and a backup/redundant low-performance node at network intersections that require them.

## Methodology
A Small Office/Home Office (SOHO) network will be developed in Cisco Packet Tracer (PT) to simulate network traffic. 

PT's network designer offers a wide range of network device models (routers, switches, endpoints, cables, etc.), and each is labeled. Routers/switches will be designated as **high-power** or **low-power** as they facilitate traffic. The majority of the testing will be affecting these devices.
### Tentative Tests
All tests will involve sending traffic through the target network equipment while gathering latency and performance data.

**Test 1: All High** 
Send all traffic through the high-power device

**Test 2: All Low** 
Send all traffic through the low-power device

**Test 3: Interrupt traffic**
While traffic is being route through the high-power device, shut it off and re-route traffic to the low-power device.

