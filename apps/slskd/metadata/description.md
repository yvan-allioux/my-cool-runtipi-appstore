# slskd

slskd is a modern client-server application for the Soulseek file-sharing network. It provides a clean web-based UI for searching, downloading, and sharing files.

## Features

- Web-based UI for managing Soulseek activity
- Configurable shared directories
- Upload/download slot management and speed limits
- User groups and quotas
- Chat rooms
- API key support for integration with tools like Soularr
- VPN integration (Gluetun) support

## Default Credentials

- **Username**: `slskd`
- **Password**: `slskd`

Change these immediately after first login.

## Configuration

Configuration can be done via:
1. Environment variables (prefix `SLSKD_`)
2. YAML configuration file (`slskd.yml` in the app data directory)
3. The web UI (if remote configuration is enabled)

## Volumes

- **/app** - Application data (config, databases, logs, downloads)
- **/music** - Shared music directory (optional, configure host path in form)

## Integration with Soularr

To use with Soularr, create an API key in the slskd configuration and provide it in your Soularr `config.ini`.
