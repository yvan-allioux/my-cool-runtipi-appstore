# Soularr

Soularr is a Python script that connects Lidarr with Soulseek (via Slskd) to automatically download music. It reads your wanted albums and artists from Lidarr, searches for them on the Soulseek network, downloads matching tracks, and notifies Lidarr to import the completed files.

## Requirements

- A running **Lidarr** instance
- A running **Slskd** instance (Soulseek client with API)

## Configuration

After installation, you need to create a `config.ini` file in the app data directory (`data/config.ini`).

Example configuration:

```ini
[Lidarr]
api_key = your_lidarr_api_key
host_url = http://lidarr:8686
download_dir = /data/slskd_downloads

[Slskd]
api_key = your_slskd_api_key
host_url = http://slskd:5030
url_base = /
download_dir = /downloads

[Search Settings]
search_timeout = 5000
maximum_peer_queue = 50
allowed_filetypes = flac,mp3 320,mp3
number_of_albums_to_grab = 10
```

Refer to the [Soularr documentation](https://github.com/mrusse/soularr) for all available configuration options.

## Volumes

- **/data** - Configuration directory (place your `config.ini` here)
- **/downloads** - Must point to your Slskd downloads directory
