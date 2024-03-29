# [VBML](../README.md) Playlist

This VBML file is a meta playlist that declares a set of properties to define a list of medias on
the Internet.

## Template

```
# VBML 1.0.6

type: playlist
```

## Properties

### type: string

The type can be set to `playlist` or `feed` depending if it's a playlist or a feed. A playlist is a
sequential list of tracks. A feed contains a stack of tracks where the first track is viewed as the
most recent entry.

## Optional

### origin: uri

The original URI where updates should be pulled from.

### title: string

The title of the playlist.

### cover: url

The cover of the playlist.

### tracks: list

The list of tracks with the format `source (uri)`.
```
tracks: |
    https://www.youtube.com/watch?v=n5vjV4hwRxo
    https://www.youtube.com/watch?v=UedTcufyrHc
```

It's also possible to specify self contained tracks:
```
tracks:
    track:
        source: https://www.youtube.com/watch?v=n5vjV4hwRxo
    track:
        source: https://www.youtube.com/watch?v=UedTcufyrHc
```

## Samples

- [playlist.vbml](../samples/playlist.vbml)
- [feed.vbml](../samples/feed.vbml)

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](https://bunjee.me) | <bunjee@omega.gg>
