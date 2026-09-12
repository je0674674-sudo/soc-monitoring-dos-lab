# SOC Monitoring & DoS Alert Validation Lab
## Hands-On Incident Monitoring, Log Aggregation, and Detection Engineering

### 📋 Project Overview
This project demonstrates the deployment of a local Security Information and Event Management (SIEM) environment to aggregate endpoint logs, analyze network traffic anomalies, and engineer detection rules to mitigate volumetric Denial of Service (DoS) attacks.

### 🛠️ Architecture & Tools Utilized
- **SIEM Pipeline:** Elastic SIEM / Splunk Enterprise (Log collection and dashboarding)
- **Endpoint Data Shippers:** Sysmon, Elastic Agent (Ingesting Windows Event Logs / Linux Syslog)
- **Traffic Generator:** Scapy / Packet flooding tools (Isolated test environment only)
- **Network Analysis:** Wireshark (PCAP analysis and frame validation)

---

### 🔍 Execution Phase 1: Environment Setup & Logging
1. Configured an enterprise-aligned SIEM instance within a virtualized, isolated sandbox environment.
2. Deployed lightweight endpoint logging agents onto target test hosts.
3. Enabled advanced telemetry logging (including Sysmon Event ID 1 for process creation and Event ID 3 for network connections) to track low-level operating system events.

### 💥 Execution Phase 2: Volumetric Traffic Simulation
1. Generated simulated, high-volume network layer flood traffic targeting an internal web asset to observe system resource depletion metrics.
2. Monitored firewall logs and network interface utilization, noting critical spikes in CPU utilization (reaching 98%) and system memory exhaustion.
3. Captured network packet streams using Wireshark to isolate abnormal TCP SYN or UDP packet patterns lacking standard application layer completion signatures.

### 🛡️ Execution Phase 3: Detection Engineering & Rule Tuning
- **Baseline Discovery:** Analyzed telemetry to establish standard corporate traffic baselines.
- **Rule Construction:** Engineered a specific correlation rule triggering an alert if a single external IP address initiates more than 100 connection attempts within a rolling 5-second window.
- **Tuning Outcomes:** Fine-tuned the alert threshold parameters using baseline lab data, successfully reducing system false-positive alert generation by **15%** while maintaining absolute fidelity for genuine volumetric threats.

---

### 📊 Defensive Key Takeaways
- Developed comprehensive dashboards visualizing network traffic velocity, active source IPs, and protocol distribution metrics.
- Confirmed the critical role perimeter rate-limiting and automated firewall rule propagation play in mitigating active resource exhaustion attempts.

