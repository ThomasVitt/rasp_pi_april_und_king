# Raspberry Pi: Home Assistant (Docker) + WireGuard-Client zum vServer

Voraussetzung: Raspberry Pi OS Lite, SSH aktiv, Ansible auf deinem Rechner.

```bash
ansible-galaxy collection install -r requirements.yml
# inventory.ini und group_vars/raspi.yml anpassen
ansible-playbook playbook.yml --ask-pass --ask-become-pass
```

1. Das Playbook gibt am Ende den **Public Key des Pi** aus.
2. Trage ihn auf dem vServer als Peer ein (`AllowedIPs = 10.8.0.2/32`) und lade WireGuard dort neu.
3. Der Pi verbindet sich mit `PersistentKeepalive = 25`, startet den Tunnel beim Boot und ein Watchdog-Timer prueft jede Minute die Verbindung und baut sie bei Ausfall neu auf.

Home Assistant: `http://<pi-ip>:8123`
