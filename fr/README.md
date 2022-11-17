# Video Backend Markup Language (VBML)

## [english](../README.md) / français

VBML est un langage de balises orienté client conçu pour accéder directement aux ressources vidéo
sur Internet. Il est basé sur [BML](https://github.com/omega-gg/BML) et inspiré par [YAML](https://fr.wikipedia.org/wiki/YAML)
pour garantir sa simplicité et le rendre facilement lisible. L'objectif est de fournir des
propriétés et routines simples afin d'accéder et organiser les ressources vidéo sur Internet. Le
langage est orienté client et dépend entièrement du logiciel qui l'exécute. Il peut être étendu via
un langage de script pour extraire des ressources vidéo plus complexes.

- [Logiciels en lien avec le VBML](software.md)
- [Principes éthiques du VBML](ethics.md)
- [VidéoTag](VideoTag.md)

## Scénarios

Vous pouvez faire usage du VBML dans les scénarios suivants:

### Usages simples

- [Track](../doc/track.md)
- [Playlist](../doc/playlist.md)

### Usages avancés

- [Backend index](../doc/index.md)
- [Backend](../doc/backend.md)

## Exemples

- [track.vbml](../samples/track.vbml)
- [live.vbml](../samples/live.vbml)
- [playlist.vbml](../samples/playlist.vbml)
- [feed.vbml](../samples/feed.vbml)

## Langage de script

VBML intègre un langage de script conçu pour extraire des ressources vidéo complexes sur Internet.
Il permet à l'utilisateur de spécifier des routines d'acccès pour extraire ces ressources
efficacement. Il se base sur une syntaxe très simple qui met l'accent sur l'efficacité et la
simplicité.

## Histoire

Ce langage a été conçu en se basant sur une expérience pratique concernant l'extraction des
ressources vidéo sur Internet. Il est pensé pour être couplé avec un logiciel orienté client qui
requiert un accès efficace à une multitude de ressources vidéo. Il a originellement été conçu pour
un [Navigateur Vidéo](https://omega.gg/about/VideoBrowser/fr) (comme [MotionBox](https://omega.gg/MotionBox/fr))
mais il est également utile pour [MotionMonkey](https://omega.gg/MotionMonkey/fr), [tevolution](https://omega.gg/tevolution/fr)
et pourrait s'avérer utile dans d'autres scénarios.

## Implementation

Le moteur VBML est actuellement implémenté dans [Sky kit](https://omega.gg/Sky/fr). Vous pouvez
consulter les sources pour de plus amples détails:

- [WControllerPlaylist.h](https://github.com/omega-gg/Sky/blob/master/src/SkGui/src/controllers/WControllerPlaylist.h)
| [WControllerPlaylist.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkGui/src/controllers/WControllerPlaylist.cpp)
- [WBackendIndex.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/io/WBackendIndex.h)
| [WBackendIndex.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/io/WBackendIndex.cpp)
- [WBackendUniversal.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.h)
| [WBackendUniversal.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.cpp)

## Projets en relation

- [MotionBox](https://omega.gg/MotionBox/sources) - Navigateur Vidéo
- [MotionMonkey](https://omega.gg/MotionMonkey/fr) - Lecteur Sémantique
- [tevolution](https://omega.gg/tevolution/fr) - Écran Vidéo Déporté

## Auteurs

- Benjamin Arnaud alias [bunjee](https://bunjee.me/fr) | <bunjee@omega.gg>
