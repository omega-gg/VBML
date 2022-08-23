# [VBML](../README.md) Backend index

This VBML file is the index that declares a set of backends and their core functionalities. That's
often the Semantic Player entry point that provides a set of backends dedicated to access video
resources on the Internet.

## Template

```
# VBML 1.0.0

type: index
```

## Properties

### type: string

The type must be set to `index`.

### version: x.x.x(...)

The version of the VBML file.

### backends: list

The list of backends with the format `id (string) name (string) version (version) validation 
(regExp)`.
```
backends: |
    youtube Youtube 1.0.0 ^youtube.com|^youtu.be
```

## Optional

### origin: uri

The original VBML URI where updates should be pulled from.

### covers: list

The list of backends covers with the format `id (string) source (url)`.
```
covers: |
    youtube cover/youtube.png
```

### backends_search: list

The list of backends dedicated to search with the format `id (string)`.
```
backends_search: |
    duckduckgo
```

### backends_track: list

The list of backends dedicated to tracks with the format `id (string)`.
```
backends_track: |
    youtube
```

### backends_cover: list

The list of backends dedicated to track covers with the format `id (string)`.
```
backends_cover: |
    tmdb
```

### backends_subtitle: list

The list of backends dedicated to subtitles with the format `id (string)`.
```
backends_subtitle: |
    opensubtitles
```

## Samples

- [index.vbml](https://github.com/omega-gg/backend/blob/master/index.vbml): omega Movement backend index

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
