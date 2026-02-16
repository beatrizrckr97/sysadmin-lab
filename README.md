# SysAdmin Lab (KVM + Ubuntu)

This repository contains hands-on labs, scripts, and troubleshooting playbooks I use to practice Linux system administration in a KVM-based Ubuntu environment.

## Lab Environment
- Hypervisor: KVM
- Guest OS: Ubuntu (server)
- Focus: incident troubleshooting, automation, monitoring, and service management

## What’s inside

### Monitoring
- Prometheus + Grafana + Blackbox Exporter setup
- systemd service configuration and verification

### Automation
- Shell scripts to automate user/group creation to simulate real environment provisioning

### Troubleshooting Playbooks
Step-by-step incident guides for:
- SSH down after reboot
- Website down / connection refused
- Disk full (100% usage)
- High CPU investigation

## How I use this repo
- Reproduce common incidents in a safe lab
- Troubleshoot systematically (verify → isolate → fix → validate)
- Document root cause and prevention steps

## Quick Commands I practice
- Service management: `systemctl status|restart <service>`
- Logs: `journalctl -xe`, `tail -f /var/log/syslog`
- Networking: `ss -tulnp`, `curl -v`, `traceroute`
- Resources: `top`, `free -m`, `df -h`, `du -sh`
