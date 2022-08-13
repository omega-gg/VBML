# VBML - Backend index

## Template

```
# VBML 1.0.0

type: index
```

## Settings

- type [string]: The type must be set to `index`.

- source [string]: The official source of the VBML file.

- version [version]: The version of the VBML file with the `x.x.x(...) [version]` format.

- backends [list]: The list of backends with the `id [string] name [string] version [version] 
validation [regExp]` format.
```
backends: |
    youtube Youtube 1.0.0 ^youtube.com|^youtu.be
```

- covers [list]: The list of backend covers with the `id [string] source [url]` format.
```
covers: |
    youtube cover/youtube.png
```

## Samples

- [index.vbml](https://github.com/omega-gg/backend/blob/master/index.vbml): omega Movement backend index.

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
