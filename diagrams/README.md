# Diagrams

```mermaid
flowchart LR
  MGMT[snet-mgmt\n10.10.1.0/24] -->|Allowed: TCP 22| APP[snet-app\n10.10.2.0/24]
  MGMT -. other ports .-> APP

