# Aegis-AI-Autonomous-SOC
Project Aegis-AI is a high-tech SOC lab showcasing the future of autonomous defense. It integrates Microsoft Sentinel and NGFWs with Claude and Gemini to automate triage, log analysis, and firewall policy updates. By bridging SOAR workflows with AI, it transforms manual monitoring into a self-healing security ecosystem.Project Aegis-AI is designed to bridge the gap between traditional manual monitoring and autonomous
security operations. By integrating industry-standard SIEM/NGFW tools with Large
Language Models (Claude 3.5 & Gemini Pro), this lab automates triage, analyzes
complex logs, and implements real-time firewall policy adjustments. Developed by Shaunhacker. ```mermaid
[
graph TD
    %% Define Node Styles
    classDef victim fill:#f96,stroke:#333,stroke-width:2px,color:white;
    classDef defensive fill:#3498db,stroke:#333,stroke-width:2px,color:white;
    classDef ai fill:#9b59b6,stroke:#333,stroke-width:2px,color:white,stroke-dasharray: 5 5;
    classDef response fill:#2ecc71,stroke:#333,stroke-width:2px,color:white;

    subgraph "Lab Infrastructure (Telemetry Generation)"
        A[Attacker (Kali)] -->|Simulates Attack| B(Victim VM: Win/Linux):::victim
        B -->|Layer 7 Traffic| C{NG Firewall: FortiGate/Palo Alto}:::defensive
        B -->|Host Logs: Sysmon| D[Wazuh Agent/EDR]:::defensive
    end

    subgraph "Nerve Center (SIEM/XDR)"
        C -->|Syslog/NetFlow| E[Microsoft Sentinel / Wazuh Indexer]:::defensive
        D -->|Security Events| E
    end

    subgraph "AI Orchestration Layer (SOAR & LLMs)"
        E -->|Webhook Trigger| F(n8n/Shuffle SOAR):::response
        F -->|API Request: Log Metadata| G{Claude 3.5 Sonnet}:::ai
        F -->|API Request: Uncategorized Logs| H{Gemini Pro}:::ai
        
        G -->|Returns: Triage/Intent| F
        H -->|Returns: Policy CLI Commands| F
    end

    subgraph "Autonomous Response"
        F -->|Approve/Deny via Slack| I[Human Orchestrator (L1 SOC)]:::response
        I -->|Approve| F
        F -->|API Call: Block IP/Isolate Host| C
    end

    %% Apply Styles
    linkStyle default stroke:#c9d1d9,stroke-width:1px;
    linkStyle 7,8,9,10 stroke:#9b59b6,stroke-width:2px,stroke-dasharray: 5 5;
    linkStyle 12,13 stroke:#2ecc71,stroke-width:2px;]
```
