# Video Backend Markup Language (VBML)

VBML is a markup language designed to provide direct access to video resources on the Internet.<br>
It's based on YAML to keep things simple and human readable.<br>
The goal is to provide standalone informations about video resources.<br>
It's client based and highly depends on client side software.<br>
It can be extended with VBL (Video Backend Language) to extract complex resources.<br>

## Video Backend Language (VBL)

VBL is the VBML scripting language designed to extract video resources on the Internet.<br>
It enables the user to specify access routines to extract video resources.<br>
It's based on a very simple syntax with a focus on efficiency and simplicity.<br>

## History

This language was designed based on practical experience at extracting video sources on the Internet.<br>
It's meant to be coupled with a client based software that needs to retrieve multiple video resources efficently.<br>
As a result, it's mostly designed for a [Video Browser](http://omega.gg/about/VideoBrowser) (like [MotionBox](http://omega.gg/MotionBox)), but it might be useful in different scenarios.<br>

## Scenarios

- Specify a backend to retrieve video tracks from a search engine (like DuckDuckGo).
- Specify a backend to access videos from a web service (like Youtube).
- Specify a backend to retrieve video subtitles (like OpenSubtitles).
- Specify a backend to retrieve video covers (like TMDb).

## Implementation

VBML is currently implemented as a part of [Sky kit](http://omega.gg/Sky) for the MotionBox project.<br>
You can take a look at the [WBackendUniversal.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.cpp) for implemation details.<br>

## Samples

- [duckduckgo.yml](https://github.com/omega-gg/backend/blob/master/duckduckgo.vbml): DuckDuckGo video search engine.
- [youtube.yml](https://github.com/omega-gg/backend/blob/master/youtube.vbml): Youtube video retriever.
- [opensubtitles.yml](https://github.com/omega-gg/backend/blob/master/opensubtitles.vbml): OpenSubtitles subtitles retriever.
- [tmdb.yml](https://github.com/omega-gg/backend/blob/master/tmdb.vbml): TMDb cover retriever.

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
