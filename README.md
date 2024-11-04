# Senior Research
## Objective
The objective of this project is to determine whether a trade-off between power consumption and network performance is viable in order to reduce power used by a network without significantly impacting the user experience.

This is done by having a main, high-performance node, and a backup/redundant low-performance node at network intersections that require them.

## Methodology
A Small Office/Home Office (SOHO) network will be developed in Cisco Packet Tracer (PT) to simulate network traffic. 

PT's network designer offers a wide range of network device models (routers, switches, endpoints, cables, etc.), and each is labeled. Routers/switches will be designated as **high-power** or **low-power** as they facilitate traffic. The majority of the testing will be affecting these devices.

#### Network Design
The topology is composed of 3 networks, Network A, Network B, and Network C. Each network contains one Layer 3 (L3) switch, PC, and a router.
The routers are set up in a triangle topology so each has a direct path to another. To ensure control over the traffic flow, paths are set with static routing and an administrative distance for path priority. 

The current topology uses the same router for each network. These routers are the highest performance that PT offers. It is planned to swap 1 or more for the lowest performance available in PT.

The following table notes all possible paths:

| Network | Router IP   | Main Path \| Path Priority=1 | Backup Path \| Path Priority=10 |
| ------- | ----------- | ---------------------------- | ------------------------------- |
| A       | 192.168.1.1 | To B: Route 10.0.0.2;        | To B: Route 10.0.0.6, 10.0.0.9  |
|         |             | To C: Route 10.0.0.6         | To C: Route 10.0.0.2, 10.0.0.10 |
| B       | 192.168.2.1 | To A: Route 10.0.0.1         | To A: Route 10.0.0.10, 10.0.0.5 |
|         |             | To C: Route 10.0.0.10        | To C: Route 10.0.0.1, 10.0.0.6  |
| C       | 192.168.3.1 | To A: Route 10.0.0.5         | To A: Route 10.0.0.9, 10.0.0.1  |
|         |             | To B: Route 10.0.0.9         | To B: Route 10.0.0.5, 10.0.0.2  |
Note: Currently the paths are written according to the hops needed to reach the destination. See the Network Addressing Table for a more readable path.

#### Network Addressing Table

| Device  | Interface       | IP Address  | Subnet Mask     | Description       |
| ------- | --------------- | ----------- | --------------- | ----------------- |
| Router0 | FastEthernet0/0 | 192.168.1.1 | 255.255.255.0   | Network A         |
| Router0 | Serial0/0/0     | 10.0.0.1    | 255.255.255.252 | Path to Router1   |
| Router0 | Serial0/0/1     | 10.0.0.5    | 255.255.255.252 | Path to Router2   |
| Router1 | FastEthernet0/0 | 192.168.2.1 | 255.255.255.0   | Network B         |
| Router1 | Serial0/0/0     | 10.0.0.2    | 255.255.255.252 | Path to Router0   |
| Router1 | Serial0/0/1     | 10.0.0.9    | 255.255.255.252 | Path to Router2   |
| Router2 | FastEthernet0/0 | 192.168.3.1 | 255.255.255.0   | Network C         |
| Router2 | Serial0/0/0     | 10.0.0.6    | 255.255.255.252 | Path to Router0   |
| Router2 | Serial0/0/1     | 10.0.0.10   | 255.255.255.252 | Path to Router1   |
| PC0     | NIC             | 192.168.1.2 | 255.255.255.0   | Part of Network A |
| PC1     | NIC             | 192.168.2.2 | 255.255.255.0   | Part of Network B |
| PC2     | NIC             | 192.168.3.2 | 255.255.255.0   | Part of Network C |

### Tentative Tests
All tests will involve sending traffic through the target network equipment while gathering latency and performance data.

**Test 1: All High** 
All traffic takes the path with high-performance routers

**Test 2: All Low** 
All traffic takes the path with low-performance routers

**Test 3: High-Low**
All traffic takes the path with high and low performance routers​

