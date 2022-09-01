# [VBML](../README.md) Backend

This VBML file is a backend that declares a set of properties and routines to access and extract
video resources on the Internet.

## Template

```
# VBML 1.0.0

type: backend
```

## Properties

### type: string

The type must be set to `backend`.

### version: x.x.x(...)

The version of the VBML file.

### title: string

The title of the backend.

### host: string

The host of the backend.
```
host: youtube.com
```

### validate: regExp

The pattern that validates the supported URI(s).
```
validate: ^youtube.com|^youtu.be
```

## Optional

### origin: uri

The original VBML URI where updates should be pulled from.

### cover: url

The picture cover of the backend.

### search: string

The search capabilities of the backend, can be `tracks`, `coverAudio` and `coverVideo`.
```
search: tracks coverVideo
```

## Scenarios

- Retrieve video tracks from a search engine (like DuckDuckGo)
- Access videos from a web service (like Youtube)
- Retrieve video subtitles (like OpenSubtitles)
- Retrieve video covers (like TMDb)

## Samples

- [duckduckgo.vbml](https://github.com/omega-gg/backend/blob/master/duckduckgo.vbml): DuckDuckGo video search engine
- [bittorrent.vbml](https://github.com/omega-gg/backend/blob/master/bittorrent.vbml): BitTorrent video retriever
- [youtube.vbml](https://github.com/omega-gg/backend/blob/master/youtube.vbml): Youtube video retriever
- [opensubtitles.vbml](https://github.com/omega-gg/backend/blob/master/opensubtitles.vbml): OpenSubtitles subtitles retriever
- [tmdb.vbml](https://github.com/omega-gg/backend/blob/master/tmdb.vbml): TMDb cover retriever

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](https://bunjee.me) | <bunjee@omega.gg>
