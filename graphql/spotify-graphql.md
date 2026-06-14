# Spotify GraphQL Schema

## Overview

This document describes a conceptual GraphQL schema for the Spotify Web API. The Spotify Web API is a RESTful service, but this schema models its resources and relationships as GraphQL types to enable structured querying of music catalog, user library, playback state, audio analysis, and recommendation data.

**Source API:** Spotify Web API (REST)
**Base URL:** https://api.spotify.com/v1
**Documentation:** https://developer.spotify.com/documentation/web-api/reference/
**Authentication:** OAuth 2.0 (Authorization Code, PKCE, Client Credentials)

## Schema Source

The types in this schema are derived from the Spotify Web API reference documentation and reflect the data structures returned by endpoints covering tracks, albums, artists, playlists, users, playback, audio analysis, podcasts, audiobooks, search, and recommendations.

## Type Summary

| Category | Types |
|---|---|
| Tracks | Track, AlbumTrack, AudioFeatures, AudioAnalysis, Section, Segment, Beat, Bar, Tatum, TuneableTrack |
| Albums | Album, NewRelease |
| Artists | Artist, ArtistAlbum, ArtistRelated |
| Playlists | Playlist, PlaylistTrack, FeaturedPlaylist |
| Users | User, PublicUser, Follower |
| Podcasts | Show, Episode |
| Audiobooks | Audiobook, AudiobookChapter |
| Browse | Category |
| Library | SavedItem, TopItems, RecentlyPlayed |
| Search | SearchResult, SearchResultSet |
| Playback | PlaybackState, CurrentlyPlaying, Device, DeviceType, Actions, Context, RepeatState, RestrictionReason |
| Recommendations | Recommendation, RecommendationSeed |
| Shared | Image, ExternalUrl, ExternalIds, Copyrights, Restriction, Markets, ResumePoint, Cursor, CursorPaging, Paging, AnalyticsMetric |

## Key Relationships

- A **Track** belongs to an **Album** and has one or more **Artist** references.
- An **Album** contains a list of **AlbumTrack** items and is associated with one or more **Artist** entities.
- An **Artist** exposes a list of **ArtistAlbum** entries and related artists via **ArtistRelated**.
- A **Playlist** holds ordered **PlaylistTrack** items, each wrapping a **Track** or **Episode**.
- A **User** owns playlists and has a **Follower** count.
- **PlaybackState** references the current **Device**, a **Context** (album, playlist, artist, or show), and the **CurrentlyPlaying** item.
- **AudioAnalysis** for a track decomposes into **Section**, **Segment**, **Beat**, **Bar**, and **Tatum** arrays.
- **Recommendation** results include **RecommendationSeed** objects describing the seeds used.
- **Show** aggregates **Episode** items; **Audiobook** aggregates **AudiobookChapter** items.
- **SearchResultSet** bundles paginated results for tracks, albums, artists, playlists, shows, episodes, and audiobooks.
- **Paging** and **CursorPaging** are generic pagination wrappers used throughout the API.

## Query Entry Points

- `track(id: ID!)` — fetch a single track by Spotify ID
- `tracks(ids: [ID!]!)` — fetch multiple tracks
- `album(id: ID!)` — fetch a single album
- `albums(ids: [ID!]!)` — fetch multiple albums
- `artist(id: ID!)` — fetch a single artist
- `artists(ids: [ID!]!)` — fetch multiple artists
- `playlist(id: ID!)` — fetch a single playlist
- `user(id: ID!)` — fetch a public user profile
- `me` — fetch the current authenticated user
- `show(id: ID!)` — fetch a podcast show
- `episode(id: ID!)` — fetch a podcast episode
- `audiobook(id: ID!)` — fetch an audiobook
- `search(query: String!, types: [SearchType!]!, market: String, limit: Int, offset: Int)` — search the catalog
- `recommendations(seedArtists: [ID!], seedTracks: [ID!], seedGenres: [String!], tuneableTrack: TuneableTrackInput)` — get track recommendations
- `playbackState` — fetch current playback state for the authenticated user
- `currentlyPlaying(market: String)` — fetch the currently playing item
- `devices` — list available playback devices
- `categories(locale: String, limit: Int, offset: Int)` — browse categories
- `featuredPlaylists(locale: String, limit: Int, offset: Int)` — get featured playlists
- `newReleases(limit: Int, offset: Int)` — get new album releases
- `myTopItems(type: TopItemType!, timeRange: TimeRange, limit: Int, offset: Int)` — get user's top tracks or artists
- `recentlyPlayed(limit: Int, before: String, after: String)` — get recently played tracks
- `mySavedItems(type: SavedItemType!, limit: Int, offset: Int)` — get user's saved library items
- `audioFeatures(id: ID!)` — get audio features for a track
- `audioFeaturesMultiple(ids: [ID!]!)` — get audio features for multiple tracks
- `audioAnalysis(id: ID!)` — get detailed audio analysis for a track

## Mutation Entry Points

- `saveItems(uris: [String!]!)` — save items to the user's library
- `removeItems(uris: [String!]!)` — remove items from the user's library
- `createPlaylist(userId: ID!, name: String!, public: Boolean, collaborative: Boolean, description: String)` — create a new playlist
- `addToPlaylist(playlistId: ID!, uris: [String!]!, position: Int)` — add items to a playlist
- `removeFromPlaylist(playlistId: ID!, tracks: [PlaylistTrackInput!]!)` — remove items from a playlist
- `reorderPlaylistItems(playlistId: ID!, rangeStart: Int!, insertBefore: Int!, rangeLength: Int)` — reorder playlist items
- `followPlaylist(playlistId: ID!)` — follow a playlist
- `unfollowPlaylist(playlistId: ID!)` — unfollow a playlist
- `followArtistOrUser(ids: [ID!]!, type: FollowType!)` — follow artists or users
- `unfollowArtistOrUser(ids: [ID!]!, type: FollowType!)` — unfollow artists or users
- `startPlayback(deviceId: ID, contextUri: String, uris: [String!], offset: PlaybackOffsetInput, positionMs: Int)` — start or resume playback
- `pausePlayback(deviceId: ID)` — pause playback
- `skipToNext(deviceId: ID)` — skip to next track
- `skipToPrevious(deviceId: ID)` — skip to previous track
- `seekToPosition(positionMs: Int!, deviceId: ID)` — seek to a position
- `setRepeatMode(state: RepeatState!, deviceId: ID)` — set repeat mode
- `setVolume(volumePercent: Int!, deviceId: ID)` — set volume
- `toggleShuffle(state: Boolean!, deviceId: ID)` — toggle shuffle
- `transferPlayback(deviceIds: [ID!]!, play: Boolean)` — transfer playback to a device
- `addToQueue(uri: String!, deviceId: ID)` — add an item to the playback queue
