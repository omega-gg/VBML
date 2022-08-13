# VBML - Backend index

## Template

```
# VBML 1.0.0

type: index
```

## Settings

- type [string]: The type must be set to 'index'.

- source [string]: The official source of the VBML file.

- version [version]: The version of the VBML file with the x.x.x(...) format.

- backends [list]: The list of backends:
    - id [string] name [string] version [version] validation [regExp]
    - eg: ```
          backends: |
              youtube Youtube 1.0.0 ^youtube.com|^youtu.be
          ```

## Samples

- [index.vbml](https://github.com/omega-gg/backend/blob/master/index.vbml): omega Movement backend index.

## Authors

- Benjamin Arnaud aka [bunjee](http://bunjee.me) | <bunjee@omega.gg>
