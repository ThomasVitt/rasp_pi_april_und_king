# Raspberry Pi: Home Assistant (Docker) + WireGuard

Voraussetzung: Raspberry Pi OS Lite (Debian-basiert, 64 oder 32 Bit), SSH aktiv, Ansible auf deinem Rechner.

```bash
ansible-galaxy collection install -r requirements.yml
# inventory.ini und group_vars/raspi.yml anpassen (Host, WireGuard-Peers, Interface)
ansible-playbook playbook.yml --ask-pass --ask-become-pass   # oder mit SSH-Key
```

Danach: Home Assistant unter `http://<pi-ip>:8123`; auf dem Router UDP 51820 zum Pi weiterleiten.
Der Server-Public-Key wird am Ende ausgegeben und gehört in die Client-Konfiguration (`Endpoint = <deine-ip-oder-ddns>:51820`).
