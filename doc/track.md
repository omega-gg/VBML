# [VBML](../README.md) Track

This VBML file is a meta track that declares a set of properties to define a media source on the
Internet.

## Template

```
# VBML 1.0.4

type: track # or live
```

## Properties

### type: string

The type can be set to:
- `track` for a media
- `live` for a live stream
- `hub` for a [Video Hub](../VideoHub.md)
- `channel` for a [Video Channel](../VideoChannel.md)

## Optional

### origin: uri

The original VBML URI where updates should be pulled from.

### source: uri

The source of the track. The track properties will be updated.
```
source: https://www.youtube.com/watch?v=n5vjV4hwRxo
```

It's also possible to specify multiple track sources:
```
source:
    Track
        duration: 1:00
        source: https://www.youtube.com/watch?v=n5vjV4hwRxo
    Track
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

### hub: string

The hub of the track.
```
hub: https://omega.gg/vox/hub
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

### timezone: string from this [list](timezone.vbml)

The time zone of the channel.

This property is specific to the channel type.

### date: yyyy-mm-ddThh:mm:ss

The publication date of the track.
```
date:  2020-01-10T09:30:00
```

## Samples

- [track.vbml](../samples/track/track.vbml)
- [live.vbml](../samples/track/live.vbml)
- [hub.vbml](../samples/track/hub.vbml)
- [multi.vbml](../samples/track/multi.vbml)
- [channel.vbml](../samples/track/channel.vbml)

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](https://bunjee.me) | <bunjee@omega.gg>
