# Video Backend Markup Language (VBML)

## [english](../README.md) / français

VBML est un langage de balises orienté client conçu pour accéder directement aux ressources vidéo
sur Internet. Il est basé sur [BML](https://github.com/omega-gg/BML) et inspiré par [YAML](https://en.wikipedia.org/wiki/YAML)
pour garantir sa simplicité et le rendre facilement lisible. L'objectif est de fournir des
propriétés et routines simples afin d'accéder et organiser les ressources vidéo sur Internet. Le
langage est orienté client et dépend entièrement du logiciel qui l'exécute. Il peut être étendu via
un langage de script pour extraire des ressources vidéo plus complexes.

- [VBML Software](software.md)
- [VBML Ethics](ethics.md)

## Scénarios

Vous pouvez faire usage du VBML dans les scénarios suivants:

### Usages simples

- [Track](doc/track.md)
- [Playlist](doc/playlist.md)

### Usages avancés

- [Backend index](doc/index.md)
- [Backend](doc/backend.md)

## Exemples

- [track.vbml](samples/track.vbml)
- [live.vbml](samples/live.vbml)
- [playlist.vbml](samples/playlist.vbml)
- [feed.vbml](samples/feed.vbml)

## Langage de script

VBML intégre un langage de script conçu pour extraire des ressources vidéo complexes sur Internet.
Il permet à l'utilisateur de spécifier des routines d'acccès pour extraire ces ressources efficacement.
Il se base sur une syntaxe très simple qui met l'accent sur l'efficacité et la simplicité.


VBML comes with a scripting language designed to extract complex video resources on the Internet.
It enables the user to specify access routines to extract these resources efficiently. It's based
on a very simple syntax with a focus on efficiency and simplicity.

## History

This language was designed based on practical experience at extracting video resources on the
Internet. It's meant to be coupled with a client based software that needs to retrieve multiple
video resources efficiently. It was intially designed with a [Video Browser](http://omega.gg/about/VideoBrowser)
in mind (like [MotionBox](http://omega.gg/MotionBox)) but it's also used for [MotionMonkey](http://omega.gg/MotionMonkey),
[clientVBML](http://omega.gg/clientVBML) and it might be useful in different scenarios.

## Implementation

VBML is currently implemented as a part of [Sky kit](http://omega.gg/Sky) for the MotionBox
project. You can take a look at the following sources for implementation details:

- [WControllerPlaylist.h](https://github.com/omega-gg/Sky/blob/master/src/SkGui/src/controllers/WControllerPlaylist.h)
| [WControllerPlaylist.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkGui/src/controllers/WControllerPlaylist.cpp)
- [WBackendIndex.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/io/WBackendIndex.h)
| [WBackendIndex.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/io/WBackendIndex.cpp)
- [WBackendUniversal.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.h)
| [WBackendUniversal.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.cpp)

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
