# Validation — Secure VNet + NSG Lab

## Goal
Prove one allowed flow (Mgmt → App on TCP 22) and one denied flow using Network Watcher.

## A) Confirm subnet NSG association
- VNet `vnet-nsg-lab` → Subnets:
  - `snet-mgmt` associated to `nsg-mgmt`
  - `snet-app` associated to `nsg-app`

## B) Confirm effective security rules (Network Watcher)
- Network Watcher → Effective security rules
- Confirm `allow-mgmt-to-app-ssh` (priority 100) allows TCP 22 from `10.10.1.0/24` to `10.10.2.0/24`

## C) IP flow verify — Allowed
- Network Watcher → IP flow verify
- VM: `vm-app-01`
- Direction: Inbound
- Remote IP: `vm-mgmt-01` private IP (10.10.1.x)
- Local IP: `vm-app-01` private IP (10.10.2.x)
- Protocol: TCP
- Local port: 22
- Expected: Allowed

## D) IP flow verify — Denied
Preferred (segmentation proof):
- Test TCP port 80 (or 443) from `vm-mgmt-01` → `vm-app-01`
- Expected: Denied (requires an explicit deny rule for mgmt→app other ports)

Fallback (internet inbound blocked proof):
- Remote IP outside VNet (e.g., 8.8.8.8) → `vm-app-01` on any port
- Expected: Denied by default deny

## Evidence files
- 01-vnet-subnets.png
- 02-nsg-app-inbound-rules.png
- 03-subnet-nsg-association.png
- 04-effective-security-rules.png
- 05-ip-flow-verify-allowed.png
- 06-ip-flow-verify-denied.png

