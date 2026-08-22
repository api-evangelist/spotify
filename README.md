# Spotify

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
