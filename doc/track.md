# [VBML](../README.md) Track

This VBML file is a meta track that declares a set of properties to define a media source on the
Internet.

## Template

```
# VBML 1.0.6

type: track
```

## Properties

### type: string

The type can be set to:
- `track` for a media
- `live` for a live stream
- `hub` for a [Video Hub](../VideoHub.md)
- `channel` for a [Video Channel](../channel.md)
- `interactive` for an interactive video

## Optional

### origin: uri

The original URI where updates should be pulled from.

### source: uri or tracks

The source of the track.
```
source: https://www.youtube.com/watch?v=n5vjV4hwRxo
```

It's also possible to specify multiple track sources:
```
source:
    track:
        duration: 1:00
        source: https://www.youtube.com/watch?v=n5vjV4hwRxo
    track:
        duration: 1:00
        source: https://www.youtube.com/watch?v=UedTcufyrHc
```

### media: uri

The media source of the track. The track properties will not be updated.
```
media: https://www.youtube.com/watch?v=n5vjV4hwRxo
```

This property is superseded by source.

### related: uri

The related playlist for the track.
```
related: https://omega.gg/vox/hubs
```

### title: string

The title of the track.

### cover: url

The cover of the track.

### author: string

The author of the track.

### feed: string

The feed playlist of the track.
```
feed: https://www.youtube.com/c/Asthenic
```

### duration: milliseconds or 00:00:00.000 format

The duration of the track.

### at: milliseconds or 00:00:00.000 format

The starting point of the track.

### end: milliseconds or 00:00:00.000 format

The ending point of the track.

This property is superseded by duration.

### timezone: string from this [list](timezone.md)

The time zone of the channel.

This property is specific to the channel type.

### date: yyyy-mm-ddThh:mm:ss

The publication date of the track.
```
date: 2020-01-10T09:30:00
```

### ambient: string

The external audio track to be looped in the background.

### subtitles: list

The specific subtitles for the track.
```
subtitles: |
    https://omega.gg/sub-eng.srt
    https://omega.gg/sub-fr.srt
```

### id: string

The id of the track. It's useful to identify a track inside a track list.

This property is limited to 10 characters.

This property is specific to a track inside a multi-track source or a template item.

```
source:
    track:
        id: track
```

```
templates:
    template:
        id: template
```

### templates: list

A list of track templates to avoid redundancy in the multi-track declaration.

A template supports the following properties: source (single uri) and ambient.

This property is specific to a multi-track source.

```
templates:
    template:
        id: templateA
        source: https://www.youtube.com/watch?v=n5vjV4hwRxo
    template:
        id: templateB
        source: https://www.youtube.com/watch?v=UedTcufyrHc
```

### template: string

The template id containing base properties for the current track.

This property is specific to a track inside a multi-track source.

### context: list

The default context of the track.

This property is specific to the interactive type.

### tags: list

The available tags for the track.

Each entry is limited to 10 characters.

This property is specific to the interactive type.
```
tags: |
    tagA
    tagB
```

## Samples

- [track.vbml](../samples/track/track.vbml)
- [slice.vbml](../samples/track/slice.vbml)
- [live.vbml](../samples/track/live.vbml)
- [hub.vbml](../samples/track/hub.vbml)
- [multi.vbml](../samples/track/multi.vbml)
- [channel.vbml](../samples/track/channel.vbml)
- [radio.vbml](../samples/track/radio.vbml)

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](https://bunjee.me) | <bunjee@omega.gg>
