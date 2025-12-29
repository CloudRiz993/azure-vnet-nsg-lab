# Teardown — Secure VNet + NSG Lab (Portal Only)

## Recommended (fastest): delete the Resource Group
1. Azure Portal → Resource groups → `rg-vnet-nsg-lab`
2. Delete resource group → confirm by typing `rg-vnet-nsg-lab`

This removes:
- VMs, NICs, disks
- VNet, subnets
- NSGs, public IPs (if any)

## Post-check
- RG no longer exists
- No remaining resources in that region for this lab

