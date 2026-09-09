# Jellyfin Tray Control

A lightweight system tray indicator for managing Jellyfin Server on Debian and Linux desktops.

## Features
- **Auto-Detection:** Automatically detects native systemd service (`jellyfin.service`) or Flatpak container (`org.jellyfin.JellyfinServer`).
- **Event-Driven:** Uses GIO D-Bus signal subscriptions instead of active polling (0.0% idle CPU).
- **Lightweight:** Minimal memory footprint (<15 MB RSS).
- **Non-Blocking:** Responsive GTK3 / AyatanaAppIndicator interface.

## Security & Privileges
- **Polkit Integration:** Uses a dedicated PolicyKit action (`org.jellyfin.service.policy`) to manage service states via D-Bus.
- **No Sudoers Modification:** Avoids `/etc/sudoers.d/` overrides, preserving standard Linux privilege separation and safe user-space execution.

## Installation & Dependencies (Debian/Ubuntu)
```bash
sudo apt install python3-gi python3-gi-cairo gir1.2-gtk-3.0 gir1.2-ayatanaappindicator3-0.1
sudo install -m 0644 org.jellyfin.service.policy /usr/share/polkit-1/actions/
sudo install -m 755 jellyfin-tray /usr/local/bin/jellyfin-tray
```

## Uninstallation
```bash
sudo rm -f /usr/local/bin/jellyfin-tray /usr/share/polkit-1/actions/org.jellyfin.service.policy
```

## License
Distributed under the GNU General Public License v3.0. See `LICENSE` for details.

## Disclaimer
This is an independent community utility and is not affiliated with, endorsed by, or connected to the official Jellyfin project.
