# [VBML](../README.md) Playlist

This VBML file is a meta playlist that declares a set of properties to define a comprehensive list
of medias on the Internet.

## Template

```
# VBML 1.0.0

type: playlist
```

## Properties

### type: string

The type must be set to `playlist`.

## Properties optional

### subtype: string

The subtype can be set to `playlist` (default) or `feed` depending if it's a playlist or a feed. A
playlist is sequential list of tracks. A feed contains a stack of tracks where the first track is
viewed as the most recent entry.

### source: uri

The source of the playlist.
```
source: https://www.youtube.com/c/Asthenic
```

### title: string

The title of the playlist.

### cover: url

The cover of the playlist.

### tracks: list

The list of tracks with the format `source (uri)`.
```
tracks: |
    https://www.youtube.com/watch?v=n5vjV4hwRxo
```

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>