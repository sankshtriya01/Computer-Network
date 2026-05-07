# Experiment 3: Network Performance Analysis Simulator
## Packet Delay, Loss, Throughput and Routing Algorithms

## 1. Introduction
This simulation analyzes **packet delay**, **packet loss**, and **end-to-end throughput** under different routing algorithms using Cisco Packet Tracer.

## 2. Network Topology
- **Devices**: 4 PCs, 3 Routers (2911), 2 Switches (2960)
- **Topology**: Linear topology with 3 routers
  - PC0/PC1 → Switch0 → Router0 → Router1 → Router2 → Switch1 → PC2/PC3
- Two routing methods implemented:
  - Static Routing
  - Dynamic Routing (RIP)

**Files:**
- `network_topology.pkt` → Main simulation file

## 3. Configuration Summary

**IP Addressing:**
- PC0: 192.168.1.2    Gateway: 192.168.1.1
- PC1: 192.168.1.3    Gateway: 192.168.1.1
- PC2: 192.168.3.2    Gateway: 192.168.3.1
- PC3: 192.168.3.3    Gateway: 192.168.3.1

**Router Interface IPs:**
- Router0: Fa0/0 (192.168.1.1), Fa0/1 (10.0.0.1)
- Router1: Fa0/0 (10.0.0.2), Fa0/1 (10.0.1.1)
- Router2: Fa0/0 (10.0.1.2), Fa0/1 (192.168.3.1)

## 4. Routing Algorithms Implemented

**A. Static Routing**
- Manually configured routes on all routers.
- Simple but not scalable.

**B. Dynamic Routing (RIP)**
- RIP v2 configured on all routers.
- Automatically learns and updates routes.

## 5. Performance Metrics Measured

- **Packet Delay**: Observed in Simulation Mode (time taken by packets)
- **Packet Loss**: Measured by deleting packets or creating congestion
- **Throughput**: Number of successful packets per simulation time

**Comparison Results:**

| Metric              | Static Routing       | RIP (Dynamic)         | Observation                     |
|---------------------|----------------------|-----------------------|---------------------------------|
| Packet Delay        | Lower                | Slightly Higher       | Static is faster initially      |
| Packet Loss         | Higher on failure    | Lower (alternate path)| RIP better in dynamic conditions|
| Throughput          | Good under low load  | Better under load     | RIP adapts better               |
| Convergence         | Manual               | Automatic             | RIP is more resilient           |

## 6. How to Run Simulation
1. Open `network_topology.pkt`
2. Test connectivity using ping
3. Switch to **Simulation Mode**
4. Use **Add Simple PDU** to generate traffic
5. Observe delay and loss in Event List
6. For high load: Use continuous ping or multiple PDUs

## 7. Files Included
- `network_topology.pkt`
- `README.md`
- `output.txt`
- `test_cases.txt`
- `config.txt`

## Conclusion
Dynamic routing (RIP) performs better under changing network conditions and failures, while Static routing offers lower delay in stable small networks.
