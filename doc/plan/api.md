# VBML: document the script functions in api.md

## Context

VBML backends run scripts (`QUERY_TRACK`, `EXTRACT_SOURCE` and so on), but the docs never list the
functions those scripts can call. `doc/backend.md` only covers the file properties. Today the only
reference is the engine source in Sky, `WBackendUniversal.cpp`, and the existing backends.

**Outcome:** `doc/api.md` lists every function a VBML script can use, with its parameters, what it
returns and a short description, grouped by category.

## Source of truth

`src/SkBackend/src/media/WBackendUniversal.cpp` in Sky:

- `BACKENDUNIVERSAL_FUNCTIONS`: the 108 names a script accepts, which is the list to cover. That's
  11 control keywords plus 97 functions, and the 97 match the `hash.insert` table exactly.
- The `inline QVariant` functions above the table: parameter count, parameter order, optional
  parameters, return types and failure values, read from each `getString(parameters, n)` style call.
- `WBackendUniversalScript::run` and `load`: the control flow and syntax rules.
- The `BACKENDUNIVERSAL_MAX_*` constants: the script limits.

The scripts in the `backend` project provide real usage for examples. 14 functions aren't used in
any backend (`LESSER_EQUAL`, `DIVIDE`, `LIST_SET`, `LIST_INSERT`, `REGEXP_CAP`, `URL_GENERATE`,
`URL_NAME`, `URL_VALUE`, `HTML_ATTRIBUTE_UTF8_AT`, `JS_EXTRACT`, `JS_CALL`, `JS_CALLS`,
`TORRENT_INTEGER_AFTER`, `PRINT`), so their entries rely on the code alone.

## Steps

### 1. Copy this plan

Copy this plan to `doc/plan/api.md`. The folder doesn't exist yet.

### 2. Write `doc/api.md`

Follow the layout of `doc/backend.md`: the `# [VBML](../README.md) API` title, a short intro, then
the sections below, ending with the usual Help and Authors sections.

**Script syntax:** one short section on what the engine accepts.

- A statement per line, `#` comments and `\` line continuation.
- Nested calls in parentheses, such as `SET url (APPEND "https://" host)`.
- How strings, variables and numbers are read, and how a condition evaluates to true or false.
- The limits: 300 statements, 3 nested `FOREACH`, the 5 second JavaScript timeout. The 1000 loop
  limit and the `IF` depth limit in the constants aren't reached by the code, so they aren't listed.

**Control keywords:** `IF`, `AND`, `OR`, `ELSE`, `ELIF`, `FI`, `FOREACH`, `CONTINUE`, `BREAK`, `END`,
`RETURN`, with one small example for conditions and one for loops.

**Functions:** in the order of `BACKENDUNIVERSAL_FUNCTIONS`, which is already grouped:

| Section | Functions |
|---|---|
| Comparison | `EQUAL` to `GREATER_EQUAL` |
| Variables and numbers | `SET`, `NUMBER`, `TIME`, `DATE`, `ADD`, `SUB`, `MULTIPLY`, `DIVIDE` |
| Strings | `GET_CHAR` to `SLICES_IN` |
| Lists and hashes | `LIST` to `LIST_CONTAIN`, `HASH_GET`, `HASH_SET`, `HASH_REMOVE` |
| Regular expressions | `REGEXP`, `REGEXP_CAP` |
| Extensions | `EXTENSION_IS_MEDIA` to `EXTENSION_IS_SUBTITLE` |
| URLs | `URL_GENERATE` to `URL_REMOVE_EXTENSION` |
| HTML | `HTML_TO_UTF8` to `HTML_ATTRIBUTE_UTF8_AT` |
| JSON | `JSON_EXTRACT` to `JSON_SPLIT` |
| JavaScript | `JS_EXTRACT`, `JS_CALL`, `JS_CALLS` |
| Archives | `ZIP_FILENAMES`, `ZIP_EXTRACT_FILE` |
| Torrents | `TORRENT_STRING_AFTER` to `TORRENT_FOLDERS`, noted as unavailable in `SK_NO_TORRENT` builds |
| Debug | `PRINT` |

Each entry uses the `### name: type` heading style of the other docs, with `[...]` for optional
parameters, a sentence or two, and an example only when the behavior isn't obvious:

````
### SLICE_IN text start end [from]: string

Returns the text between `start` and `end`, without them.
```
SET id (SLICE_IN data '"videoId":"' '"')
```
````

The signature above only shows the format. The real parameters of each entry come from the code.

**Not included:** the routines (`QUERY_TRACK` and so on) and the variables each one receives, such as
`data`, `url` and `next`. They aren't functions, and they could become their own page later.

### 3. Link it

Add `- [API](doc/api.md)` after the Backend link in `README.md`, the same link with `../doc/` in
`fr/README.md`, and a short Scripts section in `doc/backend.md` that links to the API page.

## Verification

1. Run a script that extracts the names from `BACKENDUNIVERSAL_FUNCTIONS` and checks that each
   appears exactly once as a heading in `doc/api.md`, with no extra headings. Expect 108.
2. Check each signature against the code, using the highest parameter index it reads and its minimum
   count check. An independent read of the file and the doc is worth it for 97 functions.
3. Check each example against a real use in the `backend` scripts, or against the code for the 14
   unused functions. Examples can't be run on their own, so they should stay close to real usage.
4. Check that the links work, the lines stay within the width of the other docs, and only
   `doc/api.md`, `doc/plan/api.md`, `doc/backend.md`, `README.md` and `fr/README.md` changed.

## Engine fixes

The review of `doc/api.md` against the code found two bugs, fixed in Sky. The `doc/api.md` entries for
`LAST_INDEX_END` and `JS_CALL` describe the fixed behavior, so the Sky fix has to go in with them.

- `WRegExp::lastIndexIn` returned a capture group number instead of a position, which broke
  `LAST_INDEX_END` with a `REGEXP`. It now searches backward with `QString::lastIndexOf`, and `from`
  defaults to `-1`.
- `JS_CALL` called `first()` on the empty list returned after the 5 second timeout. It now returns an
  empty value.

Nothing gets committed until asked.
