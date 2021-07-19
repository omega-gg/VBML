# Video Backend Markup Language (VBML)

VBML is a client based markup language designed to provide direct access to video resources on the
Internet. It's based on [YAML](https://en.wikipedia.org/wiki/YAML) to keep things simple and human
readable. The goal is to provide simple routines to access video resources directly. It's client
based and entirely depends on the local software it runs from. It can be extended via a scripting
language to extract complex resources.

## Script Language

VBML comes with a scripting language designed to extract complex video resources on the Internet.
It enables the user to specify access routines to extract these resources efficiently. It's based
on a very simple syntax with a focus on efficiency and simplicity.

## History

This language was designed based on practical experience at extracting video resources on the
Internet. It's meant to be coupled with a client based software that needs to retrieve multiple
video resources efficiently. As a result, it was designed with a [Video Browser](http://omega.gg/MotionBox/VideoBrowser)
in mind (like [MotionBox](http://omega.gg/MotionBox)) but it's also used for [MotionMonkey](http://omega.gg/MotionMonkey))
and it might be useful in different scenarios.

## Scenarios

- Specify a backend to retrieve video tracks from a search engine (like DuckDuckGo).
- Specify a backend to access videos from a web service (like Youtube).
- Specify a backend to retrieve video subtitles (like OpenSubtitles).
- Specify a backend to retrieve video covers (like TMDb).

## Implementation

VBML is currently implemented as a part of [Sky kit](http://omega.gg/Sky) for the MotionBox
project. You can take a look at [WBackendUniversal.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.h)
and [WBackendUniversal.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.cpp)
for implemation details.

## Samples

- [duckduckgo.yml](https://github.com/omega-gg/backend/blob/master/duckduckgo.vbml): DuckDuckGo video search engine.
- [bittorrent.yml](https://github.com/omega-gg/backend/blob/master/bittorrent.vbml): BitTorrent video retriever.
- [youtube.yml](https://github.com/omega-gg/backend/blob/master/youtube.vbml): Youtube video retriever.
- [opensubtitles.yml](https://github.com/omega-gg/backend/blob/master/opensubtitles.vbml): OpenSubtitles subtitles retriever.
- [tmdb.yml](https://github.com/omega-gg/backend/blob/master/tmdb.vbml): TMDb cover retriever.

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
