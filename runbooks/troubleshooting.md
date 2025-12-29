# Troubleshooting Runbook — VNet + NSG Lab

## Symptom: IP flow verify returns Allowed when you expected Denied
- Default NSG rule `AllowVnetInBound` allows VNet-to-VNet traffic unless overridden.
- Add an explicit Deny rule for Mgmt → App (all ports) with priority higher than default (e.g., 110), while keeping the Allow rule for TCP 22 at priority 100.

## Symptom: Effective rules do not show your custom rule
- Confirm `nsg-app` is associated to `snet-app`
- Confirm rule is created in `nsg-app` (Inbound)
- Confirm priority is lower than 65000
- Refresh effective rules / wait a few minutes

## Symptom: Network Watcher tools not available
- Ensure Network Watcher is enabled in the same region as the VMs

