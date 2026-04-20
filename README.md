# Aegis-AI-Autonomous-SOC
Project Aegis-AI is a high-tech SOC lab showcasing the future of autonomous defense. It integrates Microsoft Sentinel and NGFWs with Claude and Gemini to automate triage, log analysis, and firewall policy updates. By bridging SOAR workflows with AI, it transforms manual monitoring into a self-healing security ecosystem.Project Aegis-AI is designed to bridge the gap between traditional manual monitoring and autonomous
security operations. By integrating industry-standard SIEM/NGFW tools with Large
Language Models (Claude 3.5 & Gemini Pro), this lab automates triage, analyzes
complex logs, and implements real-time firewall policy adjustments. Developed by Shaunhacker. 
'''mermaid[graph TD
    %% Node Definitions
    A["Attacker (Kali Linux)"]
    B["Victim Environment (Windows/Ubuntu)"]
    C{"NGFW (FortiGate/Palo Alto)"}
    D["Endpoint Security (Wazuh/Sysmon)"]
    E["SIEM (Microsoft Sentinel)"]
    F["SOAR Orchestrator (n8n/Shuffle)"]
    G[["Claude 3.5 (Triage & Intent)"]]
    H[["Gemini Pro (Log-to-Policy CLI)"]]
    I["Analyst Approval (Slack/Discord)"]

    %% Flow/Connections
    A -->|Simulated Attacks| B
    B -->|Network Telemetry| C
    B -->|Host Logs| D
    C -->|Syslog| E
    D -->|Security Events| E
    
    E -->|Incident Trigger| F
    F --- G
    F --- H
    
    F -->|Human-in-the-Loop| I
    I -->|Authorized Action| F
    F -->|Auto-Remediation API| C

    %% Styling
    classDef victim fill:#e67e22,stroke:#333,stroke-width:2px,color:#fff;
    classDef security fill:#2980b9,stroke:#333,stroke-width:2px,color:#fff;
    classDef ai fill:#8e44ad,stroke:#333,stroke-width:2px,color:#fff,stroke-dasharray: 5 5;
    classDef action fill:#27ae60,stroke:#333,stroke-width:2px,color:#fff;

    class B victim;
    class C,D,E security;
    class G,H ai;
    class F,I action;]'''
