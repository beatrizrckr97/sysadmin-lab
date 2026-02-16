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
