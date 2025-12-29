# Deployment — Secure VNet + NSG Lab (Portal Only)

## Resources
- RG: `rg-vnet-nsg-lab`
- VNet: `vnet-nsg-lab` (10.10.0.0/16)
- Subnets: `snet-mgmt` (10.10.1.0/24), `snet-app` (10.10.2.0/24)
- NSGs: `nsg-mgmt`, `nsg-app` (subnet-associated)
- VMs (no public IP): `vm-mgmt-01`, `vm-app-01`

## Steps (Portal)
1. Create Resource Group: `rg-vnet-nsg-lab`
2. Create VNet `vnet-nsg-lab` with two subnets:
   - `snet-mgmt` 10.10.1.0/24
   - `snet-app`  10.10.2.0/24
3. Create NSGs:
   - `nsg-mgmt`
   - `nsg-app`
4. Associate NSGs to subnets:
   - `nsg-mgmt` → `snet-mgmt`
   - `nsg-app`  → `snet-app`
5. Configure inbound rule on `nsg-app`:
   - Allow TCP 22 from `10.10.1.0/24` to `10.10.2.0/24` (priority 100)
6. Create two VMs (no public IPs, no inbound ports opened):
   - `vm-mgmt-01` in `snet-mgmt`
   - `vm-app-01` in `snet-app`

## Evidence to capture
See `screenshots/README.md`

