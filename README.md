# Video Backend Markup Language (VBML)

## english / [français](fr/README.md)

VBML is the first declarative video language designed for a [Semantic Player](https://omega.gg/about/SemanticPlayer).
It's a client based markup language designed to define, aggregate and access video resources on the
Internet. It's based on [BML](https://github.com/omega-gg/BML) and inspired by [YAML](https://en.wikipedia.org/wiki/YAML)
to keep things simple and human readable. The goal is to provide simple properties and routines in
order to access and organize video resources on the Internet. The language is client based and
depends entirely on the software it's running from. It comes with simple scripting functionalities
to define complex video resources.

- [Software related to VBML](software.md)
- [Ethical principles of the VBML](ethics.md)
- [VBML use cases](cases.md)

## Definitions

- [tevolution](tevolution.md)
- [tevolution channel](channel.md)
- [Video Hub](VideoHub.md)
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

### Track

- [track.vbml](samples/track/track.vbml)
- [slice.vbml](samples/track/slice.vbml)
- [live.vbml](samples/track/live.vbml)
- [hub.vbml](samples/track/hub.vbml)
- [multi.vbml](samples/track/multi.vbml)
- [channel.vbml](samples/track/channel.vbml)
- [radio.vbml](samples/track/radio.vbml)
- [interactive.vbml](samples/track/interactive.vbml)

### Playlist

- [playlist.vbml](samples/playlist/playlist.vbml)
- [feed.vbml](samples/playlist/feed.vbml)

## Script Language

VBML comes with a scripting language designed to extract complex video resources on the Internet.
It enables the user to specify access routines to extract these resources efficiently. It's based
on a very simple syntax with a focus on efficiency and simplicity.

## History

This language was designed based on practical experience at extracting video resources on the
Internet. It's meant to be coupled with a client based software that needs to retrieve multiple
video resources efficiently. It was intially designed with a [Video Browser](https://omega.gg/about/VideoBrowser)
in mind (like [MotionBox](https://omega.gg/MotionBox)) but it's also used for [MotionMonkey](https://omega.gg/MotionMonkey),
[tevolution](https://omega.gg/tevolution), [tevo](https://omega.gg/tevo) and it might be useful in
other scenarios.

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
- [tevo](https://omega.gg/tevo) - Command line Semantic Player

## Authors

- Benjamin Arnaud aka [bunjee](https://bunjee.me) | <bunjee@omega.gg>
