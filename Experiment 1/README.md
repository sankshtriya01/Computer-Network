# Experiment 1: Design and Simulation of Network Topologies
## Bus, Star, Ring, and Mesh Topologies using Cisco Packet Tracer

## 1. Introduction
This assignment demonstrates the design and simulation of four fundamental network topologies — **Bus, Star, Ring, and Mesh** — using Cisco Packet Tracer. The simulation focuses on understanding data flow, connectivity, advantages, disadvantages, and performance of each topology under normal and varying network conditions.

## 2. Network Topologies Designed

### 1. Bus Topology (`Bus Topology.pkt`)
- All PCs connected to a single shared backbone cable (simulated using a Hub or coaxial-like shared medium).
- Devices: 4–6 PCs + 1 Hub
- Connection: All PCs connected to a central Hub using Copper Straight-Through cables.

### 2. Star Topology (`Star Topology.pkt`)
- Most commonly used topology in modern LANs.
- All PCs connected to a central Switch.
- Devices: 4–6 PCs + 1 Switch (2960)
- Connection: Point-to-point links from each PC to the central Switch.

### 3. Ring Topology (`Ring Topology.pkt`)
- Devices connected in a closed loop.
- Data travels in one direction (unidirectional ring).
- Devices: 4–6 PCs connected in a circular manner using Copper Straight-Through cables.
- Note: Simulated using direct PC-to-PC connections forming a logical ring.

### 4. Mesh Topology (`Mesh Topology.pkt`)
- Every device connected to every other device (full mesh).
- Devices: 4 PCs with multiple direct connections between each pair.
- Provides multiple paths for data flow and high redundancy.

## 3. Simulation Details
- **Tool Used**: Cisco Packet Tracer
- **Devices**: PCs, Hub, Switch
- **Cabling**: Copper Straight-Through cables
- **IP Configuration**: All PCs configured in the same subnet (192.168.1.0/24)
- **Testing Method**: 
  - Ping command from Desktop → Command Prompt
  - Simulation Mode to observe packet flow
  - Added multiple PDUs to simulate data traffic

## 4. Advantages and Disadvantages

| Topology     | Advantages                                      | Disadvantages                                   | Data Flow Efficiency | Fault Tolerance |
|--------------|--------------------------------------------------|--------------------------------------------------|----------------------|-----------------|
| **Bus**      | Simple, low cost, easy to install               | Single point of failure, high collision rate    | Low                  | Very Low        |
| **Star**     | Easy to manage, centralized control, scalable   | Central device failure affects whole network    | High                 | Medium          |
| **Ring**     | Ordered data flow, no collisions in ideal case  | One node failure breaks the entire ring         | Medium               | Low             |
| **Mesh**     | High redundancy, multiple paths, reliable       | Expensive, complex wiring, difficult to manage  | Very High            | Very High       |

## 5. Performance Analysis
- **Bus Topology**: High collision probability under heavy traffic. Performance degrades significantly with more devices.
- **Star Topology**: Best performance in normal conditions. Easy to troubleshoot and expand.
- **Ring Topology**: Data flows sequentially. A single break in the ring can disconnect the network.
- **Mesh Topology**: Excellent reliability and load balancing due to multiple alternate paths. Highest network efficiency.

**Impact on Real-time Applications:**
- Star and Mesh topologies perform better for video streaming and VoIP due to lower latency and higher reliability.
- Bus and Ring topologies may suffer from delays and packet loss under high traffic.

## 6. How to Run the Simulations
1. Open Cisco Packet Tracer.
2. Open any of the following files:
   - `Bus Topology.pkt`
   - `Star Topology.pkt`
   - `Ring Topology.pkt`
   - `Mesh Topology.pkt`
3. Go to **Realtime** mode and test connectivity using `ping` from each PC.
4. Switch to **Simulation** mode to observe packet flow and data transmission.
5. Use **Add Simple PDU** to generate traffic and analyze performance.

## 7. Files Included
- `Bus Topology.pkt`          → Bus Topology
- `Star Topology.pkt`         → Star Topology
- `Ring Topology.pkt`         → Ring Topology
- `Mesh Topology.pkt`         → Mesh Topology
- `README.md`        → This documentation


## 8. Assumptions and Design Decisions
- Used simple topologies with 4–6 PCs for clear visualization.
- Copper Straight-Through cables used for all connections (standard Ethernet).
- All devices placed in the same subnet for easy connectivity testing.
- Simulations are repeatable and focus on basic data flow and failure scenarios.

**Screenshots** of each topology, ping results, and Simulation Mode packet flow are available within the respective `.pkt` files.

---

