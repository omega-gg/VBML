# [VBML](../README.md) Track

This VBML file is a meta track that declares a set of properties to define a comprehensive media
source on the Internet.

## Template

```
# VBML 1.0.0

type: track
```

## Properties

### type: string

The type must be set to `track`.

### source: uri

The source of the media.
```
source: https://www.youtube.com/watch?v=n5vjV4hwRxo
```

## Properties optional

### subtype: string

The subtype can be set to `media` or `live` depending if it's a media or a live stream.

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

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
