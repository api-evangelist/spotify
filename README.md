# Spotify

Spotify is the world's leading music streaming platform with 600M+ users and 100M+ tracks. The Spotify Web API enables developers to discover music and podcasts, manage Spotify libraries, control audio playback, access audio analysis, and build personalized music experiences. Authentication uses OAuth 2.0 with scopes for user-authorized access. The API underwent significant changes in February 2026 with new generic library endpoints and streamlined playlist management.

- **Developer Portal:** https://developer.spotify.com/
- **Web API Documentation:** https://developer.spotify.com/documentation/web-api
- **Dashboard:** https://developer.spotify.com/dashboard
- **Community:** https://community.spotify.com/t5/Spotify-for-Developers/bd-p/Spotify_Developer

## APIs

### Spotify Web API

The Spotify Web API provides RESTful access to Spotify's music and podcast catalog, user library management, playback control, and personalization features. Covers 80+ endpoints across Albums, Artists, Tracks, Playlists, Player, Search, Shows, Episodes, Audiobooks, Recommendations, and User personalization.

- **Base URL:** https://api.spotify.com/v1
- **Authentication:** OAuth 2.0 (Authorization Code, PKCE, Client Credentials)
- **Documentation:** https://developer.spotify.com/documentation/web-api

**Key Capabilities:**
- Full music and podcast catalog search and metadata retrieval
- Playback control (play, pause, skip, seek, queue, volume, shuffle, repeat)
- User library management via generic Spotify URI endpoints (post Feb 2026)
- Playlist creation, editing, and track management
- Personalized recommendations with audio feature targeting
- Audio analysis (tempo, key, energy, danceability, valence)
- User top artists and tracks across short/medium/long time ranges

## Artifacts

### OpenAPI Specifications

| Spec | Description |
|---|---|
| [spotify-openapi-original.yml](openapi/spotify-openapi-original.yml) | Spotify Web API OpenAPI 3.0 spec (80+ endpoints) |

### JSON Schema

| Schema | Description |
|---|---|
| [spotify-track-schema.json](json-schema/spotify-track-schema.json) | Track object schema with artists, album, audio features, and market availability |
| [spotify-playlist-schema.json](json-schema/spotify-playlist-schema.json) | Playlist schema with tracks, owner, followers, and collaboration settings |

### JSON Structure

| Structure | Description |
|---|---|
| [spotify-track-structure.json](json-structure/spotify-track-structure.json) | Hierarchical field map for the Spotify Track object |

### JSON-LD Context

| Context | Description |
|---|---|
| [spotify-context.jsonld](json-ld/spotify-context.jsonld) | Linked data context mapping Spotify vocabulary to schema.org MusicRecording, MusicPlaylist, etc. |

### Examples

| Example | Description |
|---|---|
| [spotify-search-tracks-example.json](examples/spotify-search-tracks-example.json) | Search catalog for tracks with full request/response |
| [spotify-get-playback-state-example.json](examples/spotify-get-playback-state-example.json) | Get current playback state with device and track details |

### Spectral Rules

| Ruleset | Description |
|---|---|
| [spotify-rules.yml](rules/spotify-rules.yml) | Spectral ruleset for Spotify API conventions including OAuth and pagination |

### Capabilities

| Capability | Description |
|---|---|
| [music-discovery.yaml](capabilities/music-discovery.yaml) | Music discovery, playlist management, and playback control (17 MCP tools) |
| [shared/spotify-web-api.yaml](capabilities/shared/spotify-web-api.yaml) | Shared Spotify Web API definition |

### Vocabulary

| Vocabulary | Description |
|---|---|
| [spotify-vocabulary.yml](vocabulary/spotify-vocabulary.yml) | Music domain vocabulary covering tracks, playlists, audio analysis, and OAuth concepts |

## Authentication

Spotify uses OAuth 2.0. Choose the appropriate flow:

| Flow | Use Case |
|---|---|
| Authorization Code | Server-side apps with user login |
| Authorization Code + PKCE | Single-page apps and mobile apps |
| Client Credentials | Server-to-server, no user context |
| Implicit Grant | Deprecated as of 2026 |

## February 2026 API Changes

Key changes in the February 2026 update:
- New generic `PUT /me/library` endpoint accepting Spotify URIs (replaces type-specific save endpoints)
- Playlist track endpoints renamed from `/tracks` to `/items`
- Removed: Create Playlist for User, Get Artist's Top Tracks, Get Available Markets, Get New Releases, Get Several Albums, Get Several Artists

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
