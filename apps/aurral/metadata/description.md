# Aurral

Self-hosted music discovery and request management for Lidarr with library-aware recommendations, granular monitoring controls, and optional Weekly Flow playlists powered by Soulseek + Navidrome.

## Features

- **Search & Discovery** – Real-time artist search via MusicBrainz, daily Discover recommendations based on your library, tags, and trends
- **Lidarr Management** – Add artists with granular monitor options (None / All / Future / Missing / Latest / First), add specific albums, optional search-on-add
- **Library view** – Browse your existing Lidarr library in a clean UI with quick navigation into artist details
- **Request tracking** – Track download and import progress with queue/history awareness
- **Weekly Flow** *(optional)* – Generate playlists from your library, then download tracks via Soulseek into a dedicated folder; optional Navidrome smart playlist integration
- **Multi-user** – Local accounts with roles and granular permissions, optional reverse-proxy auth (OAuth2/OIDC)
- **Notifications** – Gotify support for key events
- **PWA** – Installable as a web app with auto-update support

## Requirements

- **Lidarr** reachable from Aurral (configured in Settings after first run)
- **A MusicBrainz contact email** (required by MusicBrainz User-Agent policy)
- Last.fm API key *(optional but strongly recommended for recommendations)*
- Navidrome *(optional, for Weekly Flow playlist integration)*

## First-Run Setup

On first launch, Aurral guides you through:

1. Creating your admin account
2. Connecting Lidarr
3. Setting your MusicBrainz contact email
4. *(Optional)* Connecting Last.fm, Navidrome, and Gotify

Everything can be adjusted later in Settings.

## Data & Safety

Aurral **does not write to your main music folder directly**. All library changes go through Lidarr's API. Only Weekly Flow writes into its own dedicated directory.
