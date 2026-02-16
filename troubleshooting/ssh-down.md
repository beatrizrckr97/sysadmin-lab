# Incident: SSH not accessible after reboot

## Symptoms
- SSH connection times out / refused after reboot
- Ping works (server responds)

## Impact / Scope
- Remote administration blocked
- Possibly affects all admins/users depending on access method

## Immediate Checks (Confirm)
- Confirm reachability:
  - `ping <server_ip>`
- Confirm SSH port:
  - `nc -vz <server_ip> 22` or `nmap -p 22 <server_ip>`
- Confirm DNS (if using hostname):
  - `nslookup <hostname>`

## Investigation (Isolate root cause)

### 1) Check out-of-band / console access
If SSH is not available, use:
- KVM/hypervisor console (preferred in lab)
- Cloud console (in real world)
Goal: confirm system booted and you can log in locally.

### 2) Verify SSH service and socket
- `systemctl status ssh`
- `systemctl restart ssh`
- `systemctl enable ssh`

### 3) Check if SSH is listening
- `ss -tulnp | grep :22`

### 4) Check firewall rules
- `ufw status`
- `iptables -S` (or `nft list ruleset`)

### 5) Check logs for SSH / boot errors
- `journalctl -u ssh --no-pager -n 100`
- `journalctl -xe --no-pager | tail -n 80`

### 6) Check network config (common after reboot)
- `ip a`
- `ip route`
- Confirm interface is up and correct IP is assigned

## Fix / Mitigation
Examples:
- SSH service was stopped → restart + enable
- Firewall blocked port 22 → allow rule
- Network interface down → bring up interface / fix config

## Validation
- From your machine:
  - `ssh -v user@<server_ip>`
- On server:
  - `systemctl is-active ssh`
  - `ss -tulnp | grep :22`

## Prevention
- Monitoring alert for SSH port (Blackbox exporter)
- Confirm SSH enabled at boot
- Document reboot checklist

## Notes / Timeline
- <timestamp> reboot
- <timestamp> ping ok, ssh fails
- <timestamp> console check → <finding>
- <timestamp> fix applied → ssh restored
