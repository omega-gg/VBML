# [VBML](../README.md) API

This page lists the functions you can call from the scripts of a VBML [backend](backend.md), such
as `QUERY_TRACK` or `EXTRACT_SOURCE`.

## Script syntax

A script is a list of statements, one per line, each starting with a keyword or a function. Calls
can be nested with parentheses.
```
SET url (APPEND "https://www.youtube.com/watch?v=" videoId) # A comment after the statement.
```

A `\` at the end of a line continues the statement on the next line.

Parameters are read as follows:

- `"text"` and `'text'` are strings. Inside them, `\n` is a line break, `\/n` is a literal `\n`, and
  `\"` and `\\` are escaped characters.
- A word that starts with a lower case letter is a variable, except `true` and `false`. A variable
  that was never set is empty.
- Any other word is literal text, such as `1000` or `true`.
- `(FUNCTION ...)` is the result of that function.

Values convert to what a function expects. A value that isn't a number reads as `0`.

When a function doesn't get enough parameters it does nothing and returns `false`, `0`, `-1` or an
empty value.

In the signatures below, `[parameter]` is optional and `...` repeats the previous parameter. A
`variable` parameter must be a variable name, because the function changes it. These functions
return `true`, unless stated otherwise.

A `match` parameter accepts text or a [REGEXP](#regexp-pattern-regexp) when stated.

## Limits

- A script is rejected when it goes past 300 statements.
- `FOREACH` can be nested 3 levels deep.
- A JavaScript call stops after 5 seconds.

## Control flow

```
IF (EQUAL id 0)
OR (EQUAL id 1)
    SET url "https://omega.gg"
ELIF (GREATER id 10)
    RETURN false
ELSE
    SET url ""
FI

FOREACH list value
    IF (EQUAL value "")
        CONTINUE
    FI
    LIST_APPEND result value
END
```

### IF condition

Runs the next statements when the condition is true. A condition is true when it reads as `true` or
as a whole number other than `0`. Anything else is false, including `1.5`.

### AND condition

Follows an `IF`, `ELIF` or `OR` on its own line. This condition must also be true. `OR` binds
tighter than `AND`, so `a AND b OR c` reads as `a AND (b OR c)`.

### OR condition

Follows an `IF`, `ELIF` or `AND` on its own line. Either this condition or the previous one must be
true.

### ELIF condition

Tests another condition when the previous ones are false.

### ELSE

Runs the next statements when the previous conditions are false.

### FI

Closes an `IF`.

### FOREACH list variable [maximum]

Runs the statements up to `END` once for each value of the list, stored in `variable`. `maximum`
limits the number of iterations, but the first one always runs.

### CONTINUE

Skips to the next iteration of the `FOREACH`.

### BREAK

Leaves the `FOREACH`.

### END

Closes a `FOREACH`.

### RETURN [value]

Stops the script and returns `value`, or `true` without one.

## Comparison

### EQUAL a b: boolean

Returns whether `a` and `b` are the same text.
```
IF (EQUAL id 2)
```

### NOT_EQUAL a b: boolean

Returns whether `a` and `b` are different texts.

### LESSER a b: boolean

Returns whether the number `a` is less than `b`.

### GREATER a b: boolean

Returns whether the number `a` is greater than `b`.

### LESSER_EQUAL a b: boolean

Returns whether the number `a` is less than or equal to `b`.

### GREATER_EQUAL a b: boolean

Returns whether the number `a` is greater than or equal to `b`.

## Variables and numbers

### SET variable value...: boolean

Stores `value` in the variable. With more than one value it stores them as a list.
```
SET i 0
SET queryData q t
```

### NUMBER value: number

Returns `value` as a number.

### TIME [text format]: number

Returns `text` as a number of milliseconds since the start of the day, read with a Qt time `format`.
Without parameters it returns the current time.
```
SET duration (TIME duration "m:ss")
```

### DATE [text format]: number

Returns `text` as a number of seconds since the Unix epoch, read with a Qt date `format`. Without
parameters it returns the current date. Returns an empty value when the date isn't valid.
```
SET expiry (ADD (DATE) 60)
```

### ADD a b: number

Returns `a` plus `b`.

### SUB a b: number

Returns `a` minus `b`.

### MULTIPLY a b: number

Returns `a` times `b`.

### DIVIDE a b: number

Returns `a` divided by `b`.

## Strings

### GET_CHAR text index: string

Returns the character at `index`, or an empty value when it's out of range.

### PREPEND text value...: string

Returns `text` with each value added before it, in turn.
```
SET q (PREPEND q "torrent ")
```

### APPEND text value...: string

Returns `text` with each value added after it, in turn.
```
SET url (APPEND url "&t=" t)
```

### REMOVE text match: string

Returns `text` without any occurrence of the `match` text. `REMOVE text position count` removes
`count` characters from `position` instead.
```
SET url (REMOVE url 0 6)
```

### CHOP text count: string

Returns `text` without its last `count` characters.

### REPLACE text match value: string

Returns `text` with each `match` replaced by `value`. `match` can be a `REGEXP`.

### MID text position [length]: string

Returns the part of `text` from `position`, up to `length` characters.

### SPLIT text separator: list

Returns the parts of `text` between each `separator`.
```
SET list (SPLIT q ' ')
```

### JOIN list separator: string

Returns the values of `list` joined with `separator`.

### LOWER text: string

Returns `text` in lower case.

### SIMPLIFY text: string

Returns `text` with the outer whitespace removed and the inner whitespace reduced to single spaces.

### READ data codec: string

Returns binary `data` read as text with a codec name, such as `"ascii"`. It reads as UTF-8 when the
codec is unknown, and as Latin-1 when it has invalid characters for that codec.

### LATIN_TO_UTF8 text: string

Returns Latin-1 `text` read as UTF-8.

### LENGTH text: number

Returns the number of characters in `text`.

### COUNT value: number

Returns the number of items in a list or a hash.

### COUNT_STRING text match: number

Returns the number of occurrences of the `match` text.

### INDEX_OF text match [from]: number

Returns the index of the first `match` from `from`, or `-1`. `match` can be a `REGEXP`.

### INDEX_END text match [from]: number

Returns the index right after the first `match` from `from`, or `-1`. `match` can be a `REGEXP`.
```
SET index (INDEX_END url '#')
```

### INDEX_SKIP text match skip: number

Returns the index of the first `match` when `skip` is below 1. Otherwise `match` is ignored and it
counts spaces: it returns the index of the space after the first `skip` spaces, the length of `text`
when there isn't one, or `-1` when there are fewer than `skip` spaces.
```
SET index (INDEX_SKIP search ' ' 2)
```

### LAST_INDEX_OF text match [from]: number

Returns the index of the last `match`, searching back from `from`, or `-1`. `match` can be a
`REGEXP`.

### LAST_INDEX_END text match [from]: number

Returns the index right after the last `match`, searching back from `from`, or `-1`. `match` can be
a `REGEXP`.

### CONTAIN text match: boolean

Returns whether `text` contains `match`, which can be a `REGEXP`.

### START_WITH text match: boolean

Returns whether `text` starts with `match`, which can be a `REGEXP`.

### END_WITH text match: boolean

Returns whether `text` ends with `match`, which can be a `REGEXP`. A `REGEXP` only tests its first
match.

### SLICE text start end [from]: string

Returns the text from `start` through `end`, both included, searching from `from`. It's empty when
`start` isn't found, and runs to the end of `text` when `end` isn't found. When `start` or `end` is
a
`REGEXP`, the other one is read as a regular expression too.
```
SET source (SLICE data "https://" ".m3u8" index)
```

### SLICE_IN text start end [from]: string

Works like `SLICE`, without `start` and `end` in the result.
```
SET type (SLICE_IN q '/' '?')
```

### SLICES text start end [from]: list

Returns every slice of `text`, in the same way as `SLICE`.
```
SET list (SLICES data "RESOLUTION=" ".m3u8")
```

### SLICES_IN text start end [from]: list

Returns every slice of `text`, in the same way as `SLICE_IN`.

## Lists and hashes

### LIST [value...]: list

Returns a list of the values.
```
SET queryData (LIST q t)
```

### LIST_GET list index: value

Returns the value at `index`, or an empty value when it's out of range.

### LIST_SET variable index value...: boolean

Replaces the value at `index`, which must exist. With more than one value it stores them as a list.

### LIST_TAKE_AT variable index: value

Removes the value at `index` from the list and returns it, or an empty value when it's out of range.

### LIST_APPEND variable value: boolean

Adds `value` at the end of the list.

### LIST_INSERT variable index value: boolean

Inserts `value` at `index`.

### LIST_REMOVE variable value: boolean

Removes the first occurrence of `value`.

### LIST_REMOVE_AT variable index: boolean

Removes the value at `index`, which must exist.

### LIST_INDEX list value [from]: number

Returns the index of `value` from `from`, or `-1`.

### LIST_CONTAIN list value: boolean

Returns whether the list contains `value`.

### HASH_GET hash key: value

Returns the value stored for `key`, or an empty value.
```
SET url (HASH_GET data "url")
```

### HASH_SET variable key value...: boolean

Stores `value` for `key`. With more than one value it stores them as a list.
```
HASH_SET next "id" 5
```

### HASH_REMOVE variable key: boolean

Removes `key` and its value.

## Regular expressions

### REGEXP pattern: regExp

Returns a regular expression, for the functions that accept one.
```
IF (CONTAIN q (REGEXP "^[({\\[]"))
```

### REGEXP_CAP text pattern capture [from]: string

Searches `text` from `from` with the `pattern` text and returns the group number `capture`.

## Extensions

### EXTENSION_IS_MEDIA extension: boolean

Returns whether `extension` is a video or an audio extension.

### EXTENSION_IS_VIDEO extension: boolean

Returns whether `extension` is `mp4`, `webm`, `ogv`, `mkv`, `avi`, `wmv`, `mov`, `flv`, `3gp` or
`m3u8`.

### EXTENSION_IS_AUDIO extension: boolean

Returns whether `extension` is `mp3`, `ogg`, `mka`, `wav`, `wma` or `flac`.

### EXTENSION_IS_SUBTITLE extension: boolean

Returns whether `extension` is `srt`.

## URLs

### URL_GENERATE url [base]: string

Returns a complete URL. A URL with a scheme stays as it is, `www.` gets `http://`, `//` gets
`https:`,
and anything else is resolved against `base` when there is one.

### URL_ENCODE text: string

Returns `text` with percent encoding.

### URL_DECODE text: string

Returns `text` without percent encoding.

### URL_NAME url: string

Returns the host without `www.`, or the decoded URL when it has no host.

### URL_VALUE url key: string

Returns the value of `key` in the query of the URL.

### URL_FRAGMENT url: string

Returns the part of the URL after `#`.

### URL_PATH url: string

Returns the part of the URL after the host, without the first `/`.

### URL_ELEMENT url from: string

Returns the text from `from` up to the next `/`, `?`, `&` or `#`. `URL_ELEMENT url count from` goes
up to the delimiter number `count` instead, or the end of the URL.
```
RETURN (URL_ELEMENT url 9)
```

### URL_ELEMENTS url count [from]: string

Returns the text from `from` up to the delimiter number `count`, like `URL_ELEMENT`. It returns the
rest of the URL when there are fewer delimiters.
```
SET id (URL_ELEMENTS url 2 10)
```

### URL_EXTENSION url: string

Returns the file extension in lower case, or an empty value when it has other characters than
letters
and numbers.

### URL_ADD_QUERY variable key value: string

Adds `key=value` to the query of the URL stored in the variable, and returns the URL.
```
URL_ADD_QUERY url "kp" "-1"
```

### URL_REMOVE_PREFIX url: string

Returns the URL without the part up to `//` and any `www.` right after it. A URL without `//` stays
as it is.

### URL_REMOVE_EXTENSION url: string

Returns the URL without its query and fragment, from the first `?` or `#`.

## HTML

### HTML_TO_UTF8 text: string

Returns `text` without its HTML tags and with its entities decoded.

### HTML_EXTRACT data url [slices]: hash

Returns the content of an HTML page loaded from `url`, as a hash:

- `title` and `cover`
- `sources`: a list of hashes with `url` and `title`
- `medias`: a list of hashes with `url`, `title` and `cover`

`slices` is a list of extra sources to look for in text between quotes or tags, each one written as
`start` or `start|end`.
```
SET data (HTML_EXTRACT data url (LIST "http" "|.torrent" "magnet:?"))
```

### HTML_TRACKS data url [slices]: list

Returns the track URLs of the page sources that an installed backend recognizes, followed by the
media URLs of the page, up to 500 in total. `slices` works like in `HTML_EXTRACT`.
```
SET list (HTML_TRACKS data url (LIST "http"))
```

### HTML_PLAYLISTS data url [slices]: list

Returns the playlists of the page sources that an installed backend recognizes, as hashes with `url`
and `type`, which is `feed` or `playlist`. `slices` works like in `HTML_EXTRACT`.

### HTML_ATTRIBUTE text name [from]: string

Returns the value of the first `name="..."` attribute from `from`.
```
SET url (HTML_ATTRIBUTE value "href")
```

### HTML_ATTRIBUTE_AT text position: string

Returns the attribute value that starts at `position`, up to the closing quote.
```
SET id (HTML_ATTRIBUTE_AT data (ADD index 11))
```

### HTML_ATTRIBUTE_UTF8 text name [from]: string

Works like `HTML_ATTRIBUTE`, with the value going through `HTML_TO_UTF8`.

### HTML_ATTRIBUTE_UTF8_AT text position: string

Works like `HTML_ATTRIBUTE_AT`, with the value going through `HTML_TO_UTF8`.

## JSON

### JSON_EXTRACT text [name] [from]: string

Returns the value after the first `"name"` text from `from`, or the value at the start of `text`
without a name. It searches the text, so it also stops at a value that reads `"name"`, and it
doesn't need valid JSON around the value. A double quoted string, an object or an array comes
without its outer quotes, braces or brackets.
```
SET id (JSON_EXTRACT data "id")
```

### JSON_EXTRACT_UTF8 text [name] [from]: string

Works like `JSON_EXTRACT`, with the value going through `HTML_TO_UTF8`.

### JSON_EXTRACT_HTML text [name] [from]: string

Works like `JSON_EXTRACT`, and replaces each `\/` in the value with `/`.

### JSON_SPLIT text [from]: list

Returns the objects or strings that follow each other in `text`, depending on which comes first,
each
one without its outer braces or quotes.
```
SET list (JSON_SPLIT data)
```

## JavaScript

### JS_EXTRACT text name [from]: string

Returns the code from `name` through the closing brace of the block that follows it.

### JS_CALL script [value...]: value

Evaluates `script` as a function and returns the result of calling it with the values as strings, or
an empty value when it takes longer than 5 seconds.

### JS_CALLS script list: list

Evaluates `script` as a function and calls it once for each list of strings in `list`, or once with
no parameters when `list` is empty. Returns the results, or an empty list when it takes longer than
5 seconds.

## Archives

### ZIP_FILENAMES data: list

Returns the file names of a zip archive.
```
FOREACH (ZIP_FILENAMES data) value
```

### ZIP_EXTRACT_FILE data name: bytes

Returns the content of the file `name` in a zip archive.
```
SET itemData (ZIP_EXTRACT_FILE data value)
```

## Torrents

These functions read bencoded torrent data. They aren't available in builds without torrent support.

### TORRENT_STRING_AFTER data key [from]: string

Returns the string that follows `key`.
```
SET name (TORRENT_STRING_AFTER data "name")
```

### TORRENT_INTEGER_AFTER data key [from]: number

Returns the integer that follows `key`, or `-1`.

### TORRENT_LIST_AFTER data key [from]: string

Returns the bencoded list or dictionary that follows `key`, without its leading `l` or `d`.
```
SET data (TORRENT_LIST_AFTER data "info")
```

### TORRENT_ITEMS data: list

Returns the files listed under `files`, as hashes with `id`, `path`, `name` and `index`.

### TORRENT_FOLDERS items: list

Returns the items from `TORRENT_ITEMS` grouped by folder, as hashes with `items`.

## Debug

### PRINT value...: empty

Writes the values to the log, separated by spaces.

## Samples

- [youtube.vbml](https://github.com/omega-gg/backend/blob/master/youtube.vbml): Youtube video retriever
- [bittorrent.vbml](https://github.com/omega-gg/backend/blob/master/bittorrent.vbml): BitTorrent video retriever

## Help

Ask your questions on the omega community: https://omega.gg/forum

The omega Movement discord: https://omega.gg/discord

## Authors

- Benjamin Arnaud aka [bunjee](https://bunjee.me) | <bunjee@omega.gg>
