# Video Backend Markup Language (VBML)

VBML is a client based markup language designed to provide direct access to video resources on the
Internet. It's based on [BML](https://github.com/omega-gg/BML) and inspired by [YAML](https://en.wikipedia.org/wiki/YAML)
to keep things simple and human readable. The goal is to provide simple properties and routines in
order to access and organize video resources on the Internet. It's client based and entirely
depends on the software it's running from. It can be extended via a scripting language to extract
complex video resources.

## Scenarios

You can use VBML in the following scenarios:

### Simple cases

- Declare a Playlist
- Declare a Track

### Advanced cases

- Specify a [Backend index](doc/index.md)
- Specify a [Backend](doc/backend.md)

## Script Language

VBML comes with a scripting language designed to extract complex video resources on the Internet.
It enables the user to specify access routines to extract these resources efficiently. It's based
on a very simple syntax with a focus on efficiency and simplicity.

## History

This language was designed based on practical experience at extracting video resources on the
Internet. It's meant to be coupled with a client based software that needs to retrieve multiple
video resources efficiently. It was intially designed with a [Video Browser](http://omega.gg/MotionBox/VideoBrowser)
in mind (like [MotionBox](http://omega.gg/MotionBox)) but it's also used for [MotionMonkey](http://omega.gg/MotionMonkey),
[clientVBML](http://omega.gg/clientVBML) and it might be useful in different scenarios.

## Implementation

VBML is currently implemented as a part of [Sky kit](http://omega.gg/Sky) for the MotionBox
project. You can take a look at [WBackendUniversal.h](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.h)
and [WBackendUniversal.cpp](https://github.com/omega-gg/Sky/blob/master/src/SkBackend/src/media/WBackendUniversal.cpp)
for implemation details.

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
