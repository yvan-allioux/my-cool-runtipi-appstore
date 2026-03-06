# WireGuard WARP Proxy

This app runs a Cloudflare WARP client (via WireGuard) inside a container and exposes an HTTP proxy (Tinyproxy) on port 3128. Other devices on your LAN can route their traffic through the WARP VPN simply by configuring this proxy — no VPN client needed on each device.

## How it works

1. The container starts a WireGuard tunnel to Cloudflare WARP
2. A watchdog script detects when the tunnel is active
3. Network routing is fixed so LAN traffic stays direct
4. Tinyproxy starts and listens on port 3128
5. Any device can use `http://<server-ip>:3128` as its HTTP proxy

## Initial Setup (Required)

Before starting the app, you need to generate the Cloudflare WARP configuration files. Run these commands on your server:

```bash
# Navigate to the app data directory
cd /path/to/runtipi/app-data/wireguard-warp-proxy

# Create the WireGuard config directory
mkdir -p config/wg_confs

# Generate WARP credentials using a temporary container
docker run --rm -it \
  -v $(pwd)/config:/config \
  linuxserver/wireguard:latest \
  sh -c "apk add --no-cache curl && \
    curl -fsSL https://github.com/ViRb3/wgcf/releases/latest/download/wgcf_2.2.22_linux_amd64 -o /usr/bin/wgcf && \
    chmod +x /usr/bin/wgcf && \
    wgcf register --accept-tos --config /config/wgcf-account.toml && \
    wgcf generate --config /config/wgcf-account.toml -p /config/wg_confs/peer_cloudflare.conf"
```

The init script (`custom-cont-init.d/99-proxy-fix.sh`) is automatically created when you first install the app.

## Verification

Check that WARP is active:
```bash
docker exec wireguard-warp-proxy curl -s https://www.cloudflare.com/cdn-cgi/trace | grep warp
```
Expected output: `warp=on` or `warp=plus`

Test the proxy from another machine:
```bash
curl -x http://<server-ip>:3128 -I https://www.google.com
```

## Configuration

| Variable | Description | Default |
|---|---|---|
| LAN_SUBNET | Your local network subnet | 192.168.1.0/24 |
| TZ | Container timezone | Europe/Paris |
