# VBML (Video Backend Markup Language)

VBML is a markup language designed to provide direct access to video resources on the Internet.<br>
It's based on YAML to keep things simple and human readable.<br>
The goal is to provide standalone informations about video resources.<br>
It's client based and highly depends on client side software.<br>
It can be extended with VBL (Video Backend Language) to extract complex resources.<br>

## VBL (Video Backend Language)

VBL is the VBML scripting language designed to extract video resources on the Internet.<br>
It enables the user to specify access routines to extract video resources.<br>
It's based on a very simple syntax with a focus on efficiency and simplicity.<br>

## History

This language was designed based on practical experience at extracting video sources on the Internet.<br>
I's meant to be coupled with a client based software that needs to retrieve multiple video resources efficently.<br>
As a result it's mostly designed for a Video Browser (like MotionBox), but it might be useful in different scenarios<br>

## Scenarios

- Specify a backend to search and retrieve video tracsk from a search engine (like DuckDuckGo).
- Specify a backend to access videos from a web service (like Youtube).
- Specify a backend to retrieve video subtitles (like OpenSubtitles).
- Specify a backend to retrieve video covers (like TMDb).

## Samples

- [duckduckgo.yml](https://raw.githubusercontent.com/omega-gg/backend/master/duckduckgo.vbml): DuckDuckGo video search engine.
- [youtube.yml](https://raw.githubusercontent.com/omega-gg/backend/master/youtube.vbml): Youtube video retriever.
- [opensubtitles.yml](https://raw.githubusercontent.com/omega-gg/backend/master/opensubtitles.vbml): OpenSubtitles subtitles retriever.
- [tmdb.yml](https://raw.githubusercontent.com/omega-gg/backend/master/tmdb.vbml): TMDb cover retriever.
