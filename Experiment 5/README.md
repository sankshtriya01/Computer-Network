# Experiment 5: Flow Control and Error Control Protocols (Stop-and-Wait, Go-Back-N ARQ, Selective Repeat ARQ)

## 1. Network Topology Design
- **Simple LAN topology** (as per assignment guidelines)
- Devices used:
  - PC0 (Sender)
  - PC1 (Receiver)
  - 1 × Switch (2960 or any generic switch)
- All PCs connected to the switch using straight-through cables.
- IP Configuration:
  - PC0: 192.168.1.1 / 255.255.255.0
  - PC1: 192.168.1.2 / 255.255.255.0
- No routers or serial links were used to keep the simulation simple and focused only on protocol behavior.

**Files created:**
- `stop_and_wait.pkt`
- `go_back_n.pkt`
- `selective_repeat_arq.pkt`

## 2. Protocol Implementation & Simulation Method
All simulations were done in **Cisco Packet Tracer Simulation Mode** using **ICMP (Simple PDU)** as frame proxies.

**Common Steps for all protocols:**
1. Switched to Simulation Mode.
2. Edited filters → Only **ICMP** enabled.
3. Used **Add Simple PDU** tool to generate traffic from PC0 to PC1.
4. Used **Capture/Forward** button to step through packet flow.
5. Simulated errors by **deleting PDUs** in the Event List (trash icon).

### Stop-and-Wait ARQ (`stop_and_wait.pkt`)
- Sent **one PDU at a time**.
- Waited for Echo Reply (ACK) before sending the next packet.
- Error simulation: Deleted one packet → observed timeout and retransmission of **only that packet**.

### Go-Back-N ARQ (`go_back_n_arq.pkt`)
- Sent **multiple PDUs quickly** (6–10 packets) without waiting for individual ACKs.
- **Explanation**: Go-Back-N allows the sender to send multiple frames before needing an acknowledgment, but if an error is detected, the sender retransmits **all frames starting from the erroneous frame**.
- Error simulation: Deleted one packet in the middle → observed that the receiver discarded subsequent good frames and the sender retransmitted multiple frames from the bad one onward.

### Selective Repeat ARQ (`selective_repeat_arq.pkt`)
- Sent **multiple PDUs quickly** (same as Go-Back-N).
- **Explanation**: Selective Repeat allows the sender to send multiple frames. The receiver buffers out-of-order good frames and the sender retransmits **only the erroneous frame**.
- Error simulation: Deleted one packet in the middle → observed retransmission of mainly the lost frame.

**Note on Packet Tracer Limitation:**  
Cisco Packet Tracer Simulation Mode does not fully implement receiver-side buffering or selective ACKs. Therefore, the visual difference between Go-Back-N and Selective Repeat is limited, but the number of retransmitted packets was observed and documented conceptually.

## 3. Performance Comparison

| Protocol            | Frames sent at once | On single error                     | Retransmitted frames | Efficiency (with errors) | Observation |
|---------------------|---------------------|-------------------------------------|----------------------|--------------------------|-----------|
| Stop-and-Wait       | 1                   | Only the bad frame                  | 1                    | Lowest                   | Very slow, safe |
| Go-Back-N ARQ       | Multiple            | Bad frame + all after it            | Many                 | Medium                   | Wastes bandwidth |
| Selective Repeat ARQ| Multiple            | **Only the bad frame**              | 1 (ideally)          | **Highest**              | Most efficient |

**Key Findings:**
- Stop-and-Wait is simplest but has the lowest throughput because of constant waiting.
- Go-Back-N improves utilization when there are no errors but performs poorly under errors.
- Selective Repeat gives the best performance under error-prone conditions because only corrupted frames are retransmitted.
- As network conditions (error rate) increase, Selective Repeat clearly outperforms the other two.

## 4. How to Run the Simulations
1. Open the respective `.pkt` file in Cisco Packet Tracer.
2. Switch to **Simulation** mode.
3. Click **Edit Filters** → enable only **ICMP**.
4. Use **Add Simple PDU** to send traffic.
5. Use **Capture/Forward** or **Auto Capture/Play** to observe.
6. Delete PDUs in Event List to simulate errors.

## 5. Files Included
- `stop_and_wait.pkt`
- `go_back_n.pkt`
- `selective_repeat_arq.pkt`
- `output.txt` (detailed results)
- `test_cases.txt`
- This `README.md`

**Assumptions & Design Decisions:**
- Used simple switch topology to focus purely on protocol behavior.
- Manual PDU deletion was used to simulate packet loss/errors.
- All simulations are repeatable using the same steps.

**Screenshots** of all three simulations (multiple packets, error deletion, retransmission) are available inside the Packet Tracer files (Event List captures).
