# VBML - Backend index

## Template

```
# VBML 1.0.0

type: index
```

## Settings

### type: string

The type must be set to `index`.

### source: url (optional)

The official source URL of the VBML file, where updates should be pulled from.

### version: x.x.x(...)

The version of the VBML file.

### backends: list

The list of backends with the format `id (string) name (string) version (version) validation 
(regExp)`.
```
backends: |
    youtube Youtube 1.0.0 ^youtube.com|^youtu.be
```

### covers: list (optional)

The list of backends covers with the format `id (string) source (url)`.
```
covers: |
    youtube cover/youtube.png
```

### backend_search: list (optional)

The list of backends dedicated to search with the format `id (string)`.
```
backend_search: |
    duckduckgo
```

### backend_track: list (optional)

The list of backends dedicated to tracks with the format `id (string)`.
```
backend_track: |
    youtube
```

### backend_cover: list (optional)

The list of backends dedicated to track covers with the format `id (string)`.
```
backend_cover: |
    tmdb
```

### backend_subtitle: list (optional)

The list of backends dedicated to subtitles with the format `id (string)`.
```
backend_subtitle: |
    opensubtitles
```

## Samples

- [index.vbml](https://github.com/omega-gg/backend/blob/master/index.vbml): omega Movement backend index

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
