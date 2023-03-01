# Polaris Bare Metal Edge Provisioning Service

```mermaid
    sequenceDiagram
    autonumber
    participant device
    participant Local router
    participant Rendezvous service
    participant Polaris service
    device->>Local router: DHCP opt. 60
    Local router->>device: HTTP Boot URL
    device->>Polaris service: HTTP Boot request
    Polaris service->>device: POS UKI boot image
    device->>Rendezvous service: device key
    Rendezvous service->>device: Polaris waiting room authorization
    device->>Polaris service: Request profile
    Polaris service->>device: Profile URL
    device->>device: Device executes<br/>profile
```
