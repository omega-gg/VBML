# VBML - Backend index

This VBML file is the index that declares a set of backends and their core functionalities. That's
often the entry point for a Semantic Player that provides a set of backends dedicated to access 
video resources on the Internet.

## Template

```
# VBML 1.0.0

type: index
```

## Settings

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

## Settings optional

### source: url

The official source URL of the VBML file, where updates should be pulled from.

### covers: list

The list of backends covers with the format `id (string) source (url)`.
```
covers: |
    youtube cover/youtube.png
```

### backend_search: list

The list of backends dedicated to search with the format `id (string)`.
```
backend_search: |
    duckduckgo
```

### backend_track: list

The list of backends dedicated to tracks with the format `id (string)`.
```
backend_track: |
    youtube
```

### backend_cover: list

The list of backends dedicated to track covers with the format `id (string)`.
```
backend_cover: |
    tmdb
```

### backend_subtitle: list

The list of backends dedicated to subtitles with the format `id (string)`.
```
backend_subtitle: |
    opensubtitles
```

## Samples

- [index.vbml](https://github.com/omega-gg/backend/blob/master/index.vbml): omega Movement backend index

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
