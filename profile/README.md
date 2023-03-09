# Polaris Bare Metal Edge Provisioning Service

```mermaid
    sequenceDiagram
    autonumber
    participant device
    participant Local router
    participant Rendezvous service
    participant Polaris service
    participant Owner service
    device->>+Local router: DHCP opt. 60
    Local router->>-device: HTTP Boot URL
    device->>+Polaris service: HTTP Boot request
    Polaris service->>-device: Secure boot signed UOS boot image
    device->>+Rendezvous service: Request owner service URL (FDO T01)
    Rendezvous service->>-device: Owner service URL
    device->>+Owner service: Provisioning secrets (FDO T02)
    Owner service->>-device: Polaris waiting room credentials
    device->>+Polaris service: Request profile/join waiting room
    Polaris service->>-device: Profile URL
    device->>device: Device executes<br/>profile
```


Parameter | Location | Required | Default | Description
--------- | ------- |------- |------- | -----------
Authorization | header | yes | n/a | Access Token in Bearer format signed using symmetric key obtained through device onboarding
org_id | URL | yes | n/a | Organization ID obtained through device onboarding
device_id | Authorization header | yes | n/a | Device ID obtained through device onboarding
