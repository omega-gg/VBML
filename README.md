# Video Backend Markup Language (VBML)

## english / [français](fr/README.md)

VBML is a client based markup language designed to provide direct access to video resources on the
Internet. It's based on [BML](https://github.com/omega-gg/BML) and inspired by [YAML](https://en.wikipedia.org/wiki/YAML)
to keep things simple and human readable. The goal is to provide simple properties and routines in
order to access and organize video resources on the Internet. The langauge is client based and
depends entirely on the software it's running from. It can be extended via a scripting language to
extract complex video resources.

- [Software](software.md)
- [Ethics](ethics.md)
- [VideoTag](VideoTag.md)

## Scenarios

You can use VBML in the following scenarios:

### Simple cases

- [Track](doc/track.md)
- [Playlist](doc/playlist.md)

### Advanced cases

- [Backend index](doc/index.md)
- [Backend](doc/backend.md)

## Samples

- [track.vbml](samples/track.vbml)
- [live.vbml](samples/live.vbml)
- [playlist.vbml](samples/playlist.vbml)
- [feed.vbml](samples/feed.vbml)

## Script Language

VBML comes with a scripting language designed to extract complex video resources on the Internet.
It enables the user to specify access routines to extract these resources efficiently. It's based
on a very simple syntax with a focus on efficiency and simplicity.

## History

This language was designed based on practical experience at extracting video resources on the
Internet. It's meant to be coupled with a client based software that needs to retrieve multiple
video resources efficiently. It was intially designed with a [Video Browser](https://omega.gg/about/VideoBrowser)
in mind (like [MotionBox](https://omega.gg/MotionBox)) but it's also used for [MotionMonkey](https://omega.gg/MotionMonkey),
[tevolution](https://omega.gg/tevolution) and it might be useful in other scenarios.

## Implementation

The VBML engine is currently implemented as a part of [Sky kit](https://omega.gg/Sky). You can take
a look at the following sources for implementation details:

- [WControllerPlaylist.h](https://github.com/omega-gg/Sky/blob/master/src/SkGui/src/controllers/WControllerPlaylist.h)
| [WControllerPlaylist.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkGui/src/controllers/WControllerPlaylist.cpp)
- [WBackendIndex.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/io/WBackendIndex.h)
| [WBackendIndex.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/io/WBackendIndex.cpp)
- [WBackendUniversal.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.h)
| [WBackendUniversal.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.cpp)

## Related projects

- [MotionBox](https://omega.gg/MotionBox/sources) - Video Browser
- [MotionMonkey](https://omega.gg/MotionMonkey) - Semantic Player
- [tevolution](https://omega.gg/tevolution) - Remote Video Screen

## Authors

- Benjamin Arnaud aka [bunjee](https://bunjee.me) | <bunjee@omega.gg>
