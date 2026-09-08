# VMware SOC Network Configuration

## Objective

Create an isolated virtual network for the SOC homelab.

## Virtual Network

| Setting | Value |
|---|---|
| Network Name | SOC-HOMELAB |
| VMware Network | VMnet19 |
| Network Type | Host-only |
| Subnet | 10.10.10.0/24 |
| Subnet Mask | 255.255.255.0 |
| DHCP | Disabled |
| Host Virtual Adapter | Enabled |

## Purpose

The Host-only network provides an isolated communication network for the cybersecurity laboratory.

The network allows the virtual machines to communicate with each other and with the Windows host while preventing the laboratory network from directly accessing the physical home network.

## Planned IP Addressing

| System | IP |
|---|---|
| Kali Linux | 10.10.10.10 |
| Windows Endpoint | 10.10.10.20 |
| Wazuh SIEM | 10.10.10.30 |

## Network Interfaces

Virtual machines that require Internet access will use a separate NAT interface.

The Host-only interface will be used for SOC communication and attack traffic.

## Security Considerations

The SOC network is intentionally isolated from the physical home network.

Attack simulations will only be performed against systems inside the isolated laboratory.

No production systems or personal devices will be used as attack targets.

## Evidence

Virtual Network Editor configuration:

`screenshots/phase-3-vmware-network.png`