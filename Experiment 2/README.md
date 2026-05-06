# Experiment 2: Packet Switching vs Circuit Switching Simulation
**Using Cisco Packet Tracer**


## 1. Introduction
This project demonstrates the difference between **Packet Switching** and **Circuit Switching** using Cisco Packet Tracer. Packet Switching is used in modern computer networks (Internet), while Circuit Switching is traditionally used in telephone networks.

## 2. Network Topology
- **Devices Used**: 
  - 4 PCs (PC0, PC1, PC2, PC3)
  - 2 Switches (2960)
  - 1 Router (2911)
- **Connections**: 
  - PC0 & PC1 → Switch0
  - PC2 & PC3 → Switch1
  - Switch0 & Switch1 → Router0
- Two files created with same topology but different simulation approach:
  - `packet_switching.pkt`
  - `circuit_switching.pkt`

## 3. IP Configuration
- PC0: 192.168.1.1 / 24   Gateway: 192.168.1.10
- PC1: 192.168.1.2 / 24   Gateway: 192.168.1.10
- PC2: 192.168.2.1 / 24   Gateway: 192.168.2.10
- PC3: 192.168.2.2 / 24   Gateway: 192.168.2.10
- Router0:
  - FastEthernet0/0: 192.168.1.10 / 24
  - FastEthernet0/1: 192.168.2.10 / 24

## 4. Simulation Details

### Packet Switching (`packet_switching.pkt`)
- **Concept**: Data is divided into small independent packets. Each packet can take different routes and is reassembled at destination.
- **Simulation**:
  - Used **Add Simple PDU** to send multiple packets from PC0 to PC2 and PC1 to PC3 simultaneously.
  - Observed packets taking the path through the router independently.
- **Observation**: Efficient bandwidth usage. Packets are mixed and routed dynamically.

### Circuit Switching (`circuit_switching.pkt`)
- **Concept**: A dedicated communication path is established between sender and receiver for the entire duration of the session.
- **Simulation**:
  - Created a continuous ping from PC0 to PC2 (simulating a dedicated circuit).
  - Tried sending normal traffic from PC1 to PC3 while the "circuit" was active.
- **Observation**: Resources are reserved for one connection. Other traffic faces delay or congestion.

## 5. Comparison Table

| Feature                    | Packet Switching                     | Circuit Switching                      |
|---------------------------|--------------------------------------|----------------------------------------|
| Path Establishment        | No dedicated path                    | Dedicated path established first       |
| Bandwidth Utilization     | Shared & Dynamic (Efficient)         | Reserved (Wasted when idle)            |
| Delay                     | Variable (can have jitter)           | Fixed delay after setup                |
| Reliability               | High (can reroute)                   | Low (single path failure breaks link)  |
| Best Suited For           | Internet, Web, Email, File Transfer  | Voice Calls, Video Conferencing        |
| Resource Usage            | Efficient                            | Inefficient                            |
| Example                   | TCP/IP Networks                      | Traditional Telephone Networks         |

## 6. How to Run the Simulations
1. Open Cisco Packet Tracer.
2. Open `packet_switching.pkt` or `circuit_switching.pkt`.
3. Test basic connectivity using ping in Realtime mode.
4. Switch to **Simulation Mode** for better visualization.
5. Use **Add Simple PDU** to generate traffic.
6. For Circuit Switching: Run continuous ping from PC0 to PC2.

## 7. Files Included
- `packet_switching.pkt`
- `circuit_switching.pkt`
- `README.md`
- `output.txt`
- `test_cases.txt`

## 8. Conclusion
Packet Switching is more efficient and suitable for modern data networks, while Circuit Switching provides guaranteed bandwidth but is inefficient for bursty traffic. The Internet is based on Packet Switching.

**Note**: Cisco Packet Tracer is inherently a packet-switched simulator. Circuit Switching is simulated by creating persistent/continuous connections.
