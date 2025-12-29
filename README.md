# Secure VNet + NSG Lab — Azure Portal Only (AZ-104)

## Goal
Deploy a segmented VNet with subnet-level NSGs and validate allowed/denied traffic using Azure portal tooling.

## Architecture
- Resource Group: `rg-vnet-nsg-lab`
- VNet: `vnet-nsg-lab` (10.10.0.0/16)
- Subnets:
  - `snet-mgmt` (10.10.1.0/24)
  - `snet-app`  (10.10.2.0/24)
- NSGs:
  - `nsg-mgmt` → associated to `snet-mgmt`
  - `nsg-app`  → associated to `snet-app`
- VMs (no public IPs):
  - `vm-mgmt-01` in `snet-mgmt`
  - `vm-app-01` in `snet-app`

## Validation approach
- Network Watcher: Effective security rules + IP flow verify

## Evidence
See `screenshots/README.md`

## Documentation
- Deployment: `docs/deployment.md`
- Validation: `docs/validation.md`
- Troubleshooting: `runbooks/troubleshooting.md`
- Teardown: `teardown/teardown.md`
