# [VBML](../README.md) Track

This VBML file is a meta track that declares a set of properties to define a media source on the
Internet.

## Template

```
# VBML 1.0.0

type: track # or live
```

## Properties

### type: string

The type can be set to `track` or `live` depending if it's a media or a live stream.

### origin: uri

The original URI where updates should be pulled from.

### source: uri

The source of the media.
```
source: https://www.youtube.com/watch?v=n5vjV4hwRxo
```

### title: string

The title of the media.

### cover: url

The cover of the media.

### author: string

The author of the media.

### feed: string

The feed playlist of the media.
```
feed: https://www.youtube.com/c/Asthenic
```

### duration: integer

The duration of the media.

### date: yyyy-mm-ddThh:mm:ss

The publication date of the media.
```
date:  2020-01-10T09:30:00
```

## Samples

- [track.vbml](../samples/track.vbml)
- [live.vbml](../samples/live.vbml)

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
