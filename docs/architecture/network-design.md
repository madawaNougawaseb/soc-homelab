# SOC Homelab — Network Design

## 1. Network Overview

The SOC homelab will use an isolated virtual network to simulate an enterprise security environment.

The laboratory network will be separated from the physical home network to ensure that attack simulations and security testing remain contained within the lab.

### SOC Network

| Parameter       | Value                                  |
| --------------- | -------------------------------------- |
| Network         | `10.10.10.0/24`                        |
| Network Type    | VMware Host-Only                       |
| Purpose         | Isolated SOC laboratory                |
| Default Gateway | None initially                         |
| DHCP            | Disabled initially                     |
| Internet Access | Via separate NAT adapter when required |

---

## 2. Virtual Machines

The initial SOC environment will contain three virtual machines.

| Hostname        | IP Address    | Role               |
| --------------- | ------------- | ------------------ |
| `KALI-ATTACKER` | `10.10.10.10` | Attack simulation  |
| `WIN-ENDPOINT`  | `10.10.10.20` | Monitored endpoint |
| `SOC-SIEM`      | `10.10.10.30` | Wazuh SIEM         |

---

## 3. Network Segmentation

The laboratory will use two virtual network interfaces where required.

### NAT Network

The NAT interface provides controlled Internet access for activities such as:

* Operating system updates
* Installing software
* Downloading security tools
* Updating package repositories

NAT traffic is not used as the primary communication path for attacks between laboratory machines.

### Host-Only Network

The Host-Only interface provides the isolated SOC network:

`10.10.10.0/24`

This network is used for communication between:

* Kali Linux
* Windows Endpoint
* Wazuh SIEM

The Host-Only network prevents laboratory attack traffic from directly reaching the physical home network.

---

## 4. Initial IP Addressing


10.10.10.1       Reserved
10.10.10.2-9     Reserved for infrastructure

10.10.10.10      KALI-ATTACKER
10.10.10.20      WIN-ENDPOINT
10.10.10.30      SOC-SIEM

10.10.10.31-99   Future servers
10.10.10.100-199 Future endpoints
10.10.10.200-254 Reserved


Static addressing will be used for the initial SOC infrastructure to make monitoring and documentation easier.

---

## 5. Traffic Flow

### Attack Traffic


KALI-ATTACKER
10.10.10.10
      │
      │ Attack simulation
      ▼
WIN-ENDPOINT
10.10.10.20


### Telemetry Flow


WIN-ENDPOINT
10.10.10.20
      │
      │ Logs / telemetry
      ▼
SOC-SIEM
10.10.10.30
```

### SOC Investigation


SOC-SIEM
    │
    │ Alerts / Events
    ▼
SOC ANALYST
```

---

## 6. Security Boundary

The SOC network is intentionally isolated from the physical home network.

```text
             INTERNET
                 │
                 ▼
           HOME ROUTER
                 │
                 ▼
            HOST PC
                 │
          VMware Workstation
                 │
        ┌────────┴────────┐
        │                 │
       NAT            HOST-ONLY
        │                 │
        ▼                 ▼
    Internet       10.10.10.0/24
                          │
              ┌───────────┼───────────┐
              │           │           │
              ▼           ▼           ▼
            KALI       WINDOWS      WAZUH
           .10.10       .10.20      .10.30
```

The physical home network will not be used as the attack network.

---

## 7. Future Expansion

The network has been designed to support additional systems.

Potential future systems include:

* Windows Server / Active Directory
* Additional Windows endpoints
* Linux servers
* Network IDS/IPS
* Vulnerability scanner
* Security automation server
* Honeypot
* Threat intelligence platform
* Cloud-connected security infrastructure

Additional systems will receive addresses from the reserved ranges.

---

## 8. Design Principles

The SOC network follows these principles:

1. **Isolation** — Security testing must remain inside the laboratory.
2. **Repeatability** — Systems should be configurable and reproducible.
3. **Observability** — Security activity should generate useful telemetry.
4. **Documentation** — Major configuration changes and experiments will be documented.
5. **Scalability** — The network should support future expansion.
6. **Safety** — Credentials and sensitive information will never be committed to the public repository.
