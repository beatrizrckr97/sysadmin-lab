# Incident: Website down – connection refused

## Symptoms
- Users unable to access website
- Browser shows "connection refused"

## Impact / Scope
- Web application unavailable
- All users affected

## Investigation

### 1. Checked nginx service status

```bash
systemctl status nginx

Output:

Active: inactive (dead)

Conclusion: nginx service was stopped.

2. Reviewed nginx logs
journalctl -u nginx --no-pager


Logs showed nginx started successfully earlier and was later stopped manually.

Resolution

Restarted nginx service:

sudo systemctl start nginx
